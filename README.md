## Background & Objectives

In this challenge, you will create a **to-do list**, with the  **Stimulus**. The list will have two functionalities: 

- a user can add a new task to it
- a user can remove a task from it (optional)

### Setup

Download and run this challenge on your machine:

```bash
cd ~/code
gh repo clone yannklein/todo-stimulus
cd todo-stimulus
code .
```

Let's launch a local webserver by running:

```bash
serve
```

Then, open [`localhost:8000`](http://localhost:8000) in your browser.

### Stimulus setup

Stimulus package URL is already set in `importmap` in the `index.html`.
Import the package in the `index.js` file with the following code:

```js
import { Application } from "@hotwired/stimulus"
window.Stimulus = Application.start()
```

### The C of CAT: Stimulus controller

Create a `todo_list_controller.js` file in the `controllers` folder.

Copy/paste the below controller skelton code in it:

```js
import { Controller } from '@hotwired/stimulus'

export default class extends Controller {
  // static targets = [ 'test' ]

  connect() {
    console.log('Hello from todo_list_controller.js')
    // console.log(this.testTarget)
  }
}
```

Put the `data-controller` attribute at the right place in the HTML. It should be on an HTML element (div or other) that encapsulate every HTML part that we want to handle with Javascript.

### The A of CAT: Stimulus action

We want to be able to create and display a new task when the user press the 'Add a task' button.
Create a data action: add the correct attribute in the right HTML element (=the button!) and create the corresponding method in your Stimulus controller. Add a `console.log()` in the method to make sure it works.

### The T of CAT: Stimulus target

> Remember 💡 there are 3 steps to follow to create a target: 
> - add data-xxx-target="example" in the HTML
> - create a static targets = ['example'] in the stimulus controller
> - use this.exampleTarget where you need it

In the method created in the previous step, we will want to: 

1. Get the value ( = the new task name) written by the user in the input. For this step, create a data target on the input and get its value.
2. Use this value to produce a new task item. Use the template below to create it:
```js
<div class="shadow-sm rounded p-3 mb-2 border d-flex justify-content-between">
  <div class="d-flex">
    <input class="d-flex form-check-input me-1" type="checkbox" />
    <div>Finish the todo challenge</div>
  </div>
  <button type="button" class="btn-close" aria-label="Close"></button>
</div>
```
3. Insert this item in the item list. For this step, create a data target on the list.

### Optional: remove items

For this step, you will need a new controller, follow all the previous steps but this time with the goal of removing items.

Some pointers:
- each items should have a 'remove item' controller on them.
- the user clicks on the X of the item to remove it
- to access the HTML element that has a `data-controller` on it, you can use `this.element`
- to remove an HTML element you can use the method `.remove()`

Good luck!!
