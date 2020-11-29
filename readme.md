## Fco Ríos. X BootCamp Web Nov20. 
## Práctica 1 - Git y Github

La primera parte de este ReadMe se compone de las respuestas a las preguntas solicitadas. 
La segunda parte contiene todos los pasos solicitados y los comandos usados para completarlos.

**- ¿Qué comando utilizaste en el paso 11? ¿Por qué?** <br />
  `git reset --hard HEAD~1`
  El comando reset lo podemos usar para mover el puntero HEAD dentro del grafo. En este caso lo situamos en el commit inmediatamente anterior al que estamos con el parámetro ~1 y añadimos el parámetro —hard para revertir los cambios realizados en el working copy. 

**- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?** <br />
  `git reflow` para buscar el SHA/identificador del commit con los cambios que hemos deshecho anteriormente. Una vez temos el identificador del commit hacemos `git reset --hard SHA`. 
  Con --hard recupero en mi working copy los cambios anteriormente desechos.

**- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?**<br />
  No se producen conflictos. Esto es porque el merge realizado es fast forward por lo que la rama que absorbe, styled, ya tiene todos los commits de la rama absorbida, master (main en mi caso). Sólo hemos movido nuestra referencia en el grafo al último commit de la rama con la que hacemos el merge.
	
**- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?**<br />
  Primero he de cambiar de rama con `git checkout styled`. Las ramas no están en la misma lista por lo que se genera conflicto. El merge es no fast forward. 

**- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?**<br />
  No hay conflicto porque es un fast forward (no se genera un nuevo commit, sólo se cambia el puntero Head al último commit de styled. `git checkout main` y `git merge styled`.

**- ¿Qué comando o comandos utilizaste en el paso 25?**<br />
  `git graph` como alias de `graph = log --graph --oneline`

  ~~~
  *   24b9acf (HEAD -> main, styled) Merge branch 'htmlify' into styled
  |\
  | * b827aeb (htmlify) Modificar git-readme en HTMLify
  * | 4cbfdc4 Modificar Readme
  |/
  * fc137d3 Añadir readme.md
  ~~~

**- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?** <br />
  `git merge —no-ff title` 
  Sí, se podría haber hecho fast forward con `git merge title`. No generaría conflicto, el puntero de master (main para mí) se trasladaría al último commit de title.

**- ¿Qué comando o comandos utilizaste en el paso 27?**<br />
  `git reset head~1`

**- ¿Qué comando o comandos utilizaste en el paso 28?**<br />
  `git restore git-nuestro.md`

**- ¿Qué comando o comandos utilizaste en el paso 29?**<br />
  `git branch -D title`

**- ¿Qué comando o comandos utilizaste en el paso 30?**<br />
  Tenemos que llegar al commit que hemos hecho en el paso 26. `git reflog` y copiar el SHA. `Git reset SHA`

**- ¿Qué comando o comandos usaste en el paso 32?**<br />
  Copiamos el SHA del commit inicial con `git reflog`.
  Ahora podemos ir a este commit con `git checkout SHA`, con lo que tendríamos que ver qué hacer con los archivos stageados en caso de tener algún ahí porque este comando modifica el working copy. Además, quedaríamos en estado DETACHED HEAD. También podemos ir a ese commit con Git reset SHA, que nos evitaría el estado DETACHED.

**- ¿Qué comando o comandos usaste en el punto 33?**<br />
  `git reflog` y `git reser SHA`

- - - 

**1) Crear un repositorio**<br />
`git init`

**2) Crear un archivo git-nuestro.md con el contenido:**<br />
  Git nuestro
  Git nuestro que estas en los repos Comprimidos sean tus commits
  Venga a nosotros tu log
  En el local como en el remote
  Danos hoy nuestro pull de cada día
  Perdona nuestros conflictos
  Como también perdonamos los de otros geeks No nos dejes caer en detached HEAD
  y líbranos de SVN
  git commit --amend
`nano git-nuestro.md`

**3) Añadir git-nuestro.md al staging area**<br />
`git add git-nuestro.md`

**4) Mover lo que hay en el staging area al repositorio**<br />
`git commit -m "Añadir git-nuestro.md"`

**5) Crear una rama llamada “styled”**<br />
`git branch styled`

**6) Listar las ramas que hay en el repositorio**<br />
`git branch`

**7) Moverse a la rama “styled”**<br />
`git checkout styled`

**8) Comprobar que se está en la rama correcta**<br />
`git branch`

**9) Modificar en el archivo git-nuestro.md:**<br />
*Git* nuestro que estás en los repos Comprimidos sean tus *commits* Venga a nosotros tu *log*
En el local como en el *remote* Danos hoy nuestro *pull* de cada día Perdona nuestros *conflictos*
 Como también perdonamos los de otros geeks No nos dejes caer en *detached HEAD*
y líbranos de *SVN*
\`git commit --amend\`
`nano git-nuestro.md`

**10) Añadir los cambios al staging area y luego pasarlos al repositorio**<br />
`git add git-nuestro.md`, `git commit -m "Modificar git-nuestro.md"`

**11) Deshacer el último commit (perdiendo los cambios realizados en el working copy)**<br />
`git reset --hard HEAD~1`

**12) Rehacer el último commit (el que acabamos de deshacer)**<br />
`git reflog`, `git reset --hard SHA_commit`

**13) Hacer un merge con ‘master’ (styled absorbe a master)**<br />
Estando en styled `git merge main`

**14) Volver a la rama master**<br />
`git checkout main`

**15) Crear una nueva rama llamada “htmlify”**<br />
`git branch htmlify`

**16) Cambiar a la rama htmlify**<br />
`git checkout htmlify`

**17) Modificar en el archivo git-nuestro.md:**<br />
<p><em>Git</em> nuestro que estas en los repos<br /> Comprimidos sean tus <em>commits</em><br /> Venga a nosotros tu <em>log</em><br />
En el local como en el <em>remote</em><br />
Danos hoy nuestro <em>pull</em> de cada día<br /> Perdona nuestros <em>conflictos</em><br />
Como también perdonamos los de otros geeks<br />
No nos dejes caer en <em>detached HEAD</em><br /> y líbranos de <em>SVN</em><br />
<code>git commit --amend</code></p>

`nano git-nuestro.md`

**18) Hacer un commit**<br />
`git add git-nuestro.md`, `git commit -m "Modificar git-readme HTMLify"`

**19) Hacer un merge de “htmlify” en “styled” (styled absorbe a htmlify)**<br />
Estando en styled `git merge htmlify`

**20) Si hay conflictos, deberemos resolverlos quedándonos con el contenido de la rama “styled”.**<br />
`nano git-nuestro.md` para editar el fichero y resolver conflictos.
`git add git-nuestro.md` y `git commit` sin -m para aprovechar el mensaje que genera el mismo Git.

**21) Desde “master”, hacer un merge con “styled”**<br />
Estando en master, `git checkout main`, `git merge styled`

**22) Crear una rama “title” y cambiarse a esa rama**<br />
`git branch title`, `git checkout title`

**23) Añadir un título (a tu gusto) al archivo git-nuestro.md y hacer un commit.**<br />
`nano git-nuestro.md`, `git add git-nuestro.md`, `git commit -m "Añado title"`

**24) Volver a la rama master**<br />
`git checkout main`

**25) Dibujar el diagrama**<br />
`git graph`(alias)

**26) Hacer un merge “no fast-forward” de “title” en “master” (master absorbe a title)**<br />
Estando en master (main) `git merge —no-ff title` 

**27) Deshacer el merge (sin perder los cambios del working copy)**<br />
`git reset HEAD~1`

**28) Descartar los cambios**<br />
`git restore git-nuestro.md`

**29) Eliminar la rama “title”**<br />
`git branch -D title`

**30) Rehacer el merge que hemos deshecho**<br />
`git reflog`, `git reset SHA`

**31) Volver a master y eliminar el resto de ramas**<br />
`git reflog`, `git checkout SHA`

**32) Volver al commit inicial cuando se creó el poema**<br />
`git reflog`, `git checkout SHA`

**33) Volver al estado final, cuando pusimos título al poema****<br />
`git reflog`, `git reser SHA`

**34) Crear los siguientes tags:**<br />
Estando en cada commit con `git reflog`
  inicial: en el primer commit `git tag inicial`
  styled: modificación del paso 10 `git tag styled`
  htmlify: modificación del paso 17-18 `git tag htmlify`
  title: modificación del paso 30 `git tag title`

**35) Ir al tag htmlify**<br />
`git checkout htmlify`
