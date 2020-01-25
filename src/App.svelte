<script>
  let name = "";
  let listTasks = [];

  function handleAddTask() {
    let text = document.getElementById("newTaskInput").value;
    listTasks = listTasks.concat({ done: false, task: text });
    document.getElementById("newTaskInput").value = "";
  }

  function handleRemoveDoneTasks() {
    listTasks = listTasks.filter(t => !t.done);
  }
</script>

<style>
  main {
    padding: 1em;
    max-width: 90%;
    width: 100%;
    margin: 0 auto;
  }

  h1 {
    text-align: center;
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 2em;
    font-weight: 100;
  }

  p {
    text-align: center;
  }

  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  h2 {
    font-size: 1em;
  }

  .remove-done-tasks {
    text-align: center;
  }

  .new-task {
    display: flex;
  }

  .done {
    opacity: 0.5;
  }

  @media (min-width: 640px) {
    main {
      max-width: 350px;
    }
  }
</style>

<main>
  <h1>Hello {name === '' ? ':)' : name}</h1>

  <p>Welcome to your Svelte developed to do list!</p>

  <ul>
    {#each listTasks as tasks}
      <li class={tasks.done ? 'done' : 'todo'}>
        <input type="checkbox" bind:checked={tasks.done} />
        {tasks.task}
      </li>
    {/each}
  </ul>

  <br />

  <div class="remove-done-tasks">
    <button on:click={handleRemoveDoneTasks}>Clear Done</button>
  </div>

  <h2>Enter a new task bellow!</h2>
  <div class="new-task">
    <input type="text" id="newTaskInput" />
    <button on:click={handleAddTask}>Add</button>
  </div>
</main>
