# Proyecto JavaScript: Una simple lista de tareas
## Descripción
Una simple lista de tareas, consiste en una aplicación web que permite a los usuarios agregar tareas, editarlas, marcarlas como completadas y eliminarlas.  Es una aplicación sencilla y fácil de usar, además está diseñada para funcionar tanto en dispositivos móviles como de escritorio. 

## Funcionalidades
La aplicación proporciona las siguientes funcionalidades:

Agregar tareas: Se pueden agregar nuevas tareas a la lista con solo hacer clic en el botón agregar tarea.

Editar tareas: Al hacer clic sobre una tarea se activa el modo de edición, lo que permite modificar su contenido. Solo se pueden editar las tareas que se encuentran en la lista de tareas por hacer.

Marcar como completado: Haciendo doble clic sobre la tarea esta se marca como completada. En dispositivos móviles, los usuarios pueden hacerlo deslizando hacia la derecha sobre la tarea. Al marcar como completada una tarea esta pasa automáticamente a otra lista llamada completado.

Lista de tareas completadas: Las tareas que se encuentran en esta lista no se pueden modificar, pero se pueden devolver a la lista de tareas por hacer demarcándolas de la misma manera como se marcaron previamente, es decir, haciendo doble clic o deslizando hacia la derecha en un dispositivo móvil.

Eliminar tareas: Solo las tareas que se encuentran en la lista completado se pueden eliminar, para ello basta con hacer clic en el botón de eliminar que tiene cada tarea en la lista.

## Sobre su programación
La aplicación está programada utilizando HTML, CSS y JavaScript buscando brindar una experiencia fluida y dinámica al usuario. A diferencia de otras listas de tareas convencionales basadas en formularios, esta utiliza elementos de lista.

Cuando el usuario agrega una tarea en la aplicación, se involucran las siguientes funciones JavaScript:

  addListItem(): Esta función se ejecuta cuando el usuario hace clic en el botón de agregar tarea. Su objetivo es crear un nuevo elemento de lista (newTaskListItem) a partir de una plantilla previamente definida (newTaskTemplate). El nuevo elemento se clona utilizando content.cloneNode(true) para obtener una copia completa del contenido. Luego, se agrega el nuevo elemento a la lista de tareas pendientes (toDoList) utilizando el método appendChild().
  
  Event Listener: El botón de agregar tarea tiene un Event Listener asociado que escucha el evento de clic. Cuando se produce el clic, se activa la función addListItem().
Cuando el usuario desea editar una tarea en la aplicación, se involucran las siguientes funciones JavaScript:

  handleSingleClick(event): Esta función se activa cuando el usuario hace clic en una tarea. Primero, encuentra el elemento de lista (listItem) más cercano al elemento en el que se hizo clic utilizando event.target.closest("li"). Luego, verifica si el contenido actual de la tarea coincide con el valor inicial predeterminado ("Nueva tarea"). Si es así, se borra el contenido del elemento de lista estableciendo listItem.textContent = "". Si el contenido está vacío, se restaura el valor inicial predeterminado estableciendo listItem.textContent = originalContent.
  
  Event Listener: La lista de tareas pendientes (toDoList) tiene un Event Listener asociado que escucha el evento de clic (click). Cuando se produce un clic en la lista, se activa la función handleSingleClick(event).

Cuando el usuario marca una tarea como completada o elimina una tarea en la aplicación, se involucran las siguientes funciones JavaScript:

  handleListItemClick(event): Esta función se activa cuando el usuario hace clic en una tarea. Primero, encuentra el elemento de lista (listItem) más cercano al elemento en el que se hizo clic utilizando event.target.closest("li"). Luego, verifica si el contenido de la tarea no está vacío utilizando listItem.textContent.trim() !== "". Si la tarea no está vacía, se actualiza el estado de completado de la tarea mediante el atributo data-completed del elemento de lista. Si el estado de completado es true, se llama a la función handleCompletedListItem(listItem) para realizar las acciones correspondientes a una tarea completada. Si el estado de completado es false, se llama a la función handleToDoListItem(listItem) para realizar las acciones correspondientes a una tarea por hacer.

  handleCompletedListItem(listItem): Esta función se encarga de manejar una tarea que se encuentra en la lista completado. Primero, busca el botón de eliminar (deleteButton) dentro del elemento de lista utilizando listItem.querySelector(".delete-button"). Si existe, se elimina utilizando deleteButton.remove(). Luego, se mueve la tarea a la lista de tareas completadas (ToDoList) utilizando toDoList.appendChild(listItem). Además, se establece el atributo contenteditable del elemento de lista en true para permitir la edición del contenido de la tarea.

  handleToDoListItem(listItem): Esta función se encarga de manejar una tarea que se encuentra en la lista por hacer. Primero, se crea un botón de eliminar (deleteButton) utilizando la función createDeleteButton(). Luego, se agrega el botón de eliminar al elemento de lista utilizando listItem.append(deleteButton). A continuación, se mueve la tarea a la lista de tareas completadas (completedTaskList) utilizando completedTaskList.appendChild(listItem). Finalmente, se elimina el atributo contenteditable del elemento de lista para deshabilitar la edición del contenido de la tarea.

  createDeleteButton(): Esta función crea dinámicamente un botón de eliminar para una tarea. Primero, se crea un elemento de botón utilizando document.createElement("button"). Luego, se le asigna una clase CSS utilizando deleteButton.classList.add("delete-button"). Se establece el contenido HTML del botón utilizando deleteButton.innerHTML para mostrar un ícono de eliminación. Por último, se agrega un Event Listener al botón de eliminar que escucha el evento de clic (click). Cuando se hace clic en el botón de eliminar, se elimina el elemento de lista al que pertenece utilizando event.target.closest("li").remove().
