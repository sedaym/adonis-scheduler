# Adonis Scheduler Provider

This library provides an easy way to schedule recurring tasks for AdonisJS.

## Install

```
npm install --save adonis-scheduler
```

## Configure

Register it in `bootstrap/app.js`:

```javascript
const providers = [
  ...
  'adonis-scheduler/providers/SchedulerProvider'
]

const aliases = {
  ...
  Scheduler: 'Adonis/Addons/Scheduler'
}
```

Register the commands:

```javascript
const aceProviders = [
  ...
  'adonis-scheduler/providers/CommandsProvider'
];

...

const commands = [
  ...
  'Adonis/Commands/Scheduler:Run'
];
```

## Usage

### Starting the scheduler

Starting an instance of the kue listener is easy with the included ace command. Simply run `./ace scheduler:run`.

The provider looks for jobs in the `app/Tasks` directory of your AdonisJS project and will automatically register a handler for any tasks that it finds.

### Creating your first task

Jobs are easy to create. They live in `app/Tasks` and they are a simple class. They expose the following properties:

| Name        | Required | Type      | Static | Description                                           |
|-------------|----------|-----------|--------|--------------------------------------------------------|
| schedule    | true     | many      | true   | The schedule for which the task should run. [More docs.](https://github.com/node-schedule/node-schedule#cron-style-scheduling)      |
| handle      | true     | function  | false  | A function that is called for this task.               |

[Here's an example.](examples/app/Tasks/Example.js)

## Thanks

Special thanks to the creator(s) of [AdonisJS](http://adonisjs.com/) for creating such a great framework.
