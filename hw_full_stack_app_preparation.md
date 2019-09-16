# Homework: Full Stack Games Hub App

### Learning Objectives

- Understand the relationship between client, server and database
- Be able to navigate a codebase that you haven't written

## Brief

Your boss has asked to you look over the codebase of a full-stack JavaScript application. The front-end is written in JavaScript using Vue, the back-end uses an Express server and a MongoDB database. Your task is to make yourself familiar with the codebase.

The application includes a README.md with instructions on running the application.

![Overview of the tech stack and tooling with commands](images/tech_stack_with_commands.png)

*Overview of the tech stack and tooling with commands*

## MVP

### Task

Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process.

### Questions

1. What is responsible for defining the routes of the `games` resource?

- GamesGrid.vue in client/src/components

2. What do you notice about the folder structure?  Whats the client responsible for? Whats the server responsible for?

- The client folder is responsible for the gathering of and presentation of data. When data needs to be saved, it is sent to the server which saves the data itself.

3. What are the responsibilities of server.js?

- server.js listens activity on LH:3000 and redirects incoming traffic to the routers through app.use, it also manages the connection to the database and manages cors.

4. What are the responsibilities of the `gamesRouter`?

- gamesRouter is responsible for CRUD actions coming from LH:3000, it also pulls in the existing database so as to amend the data.

5. What process does the the client (front-end) use to communicate with the server?

- The client has no direct communication with the server, but the front end communicates with the server via a fetch in GameServices.js which sends the data inputted by the user through a POST to LH:3000. server.js is tuned to listen to incoming actions from this address, and so the data is taken and run through the routers.

6. What optional second argument does the `fetch` method take? And what is it used for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs.

- This second parameter allows for customisation of different settings. In this instance it is used to specify that the request is a POST request, specifying the content type, and then converting the data into a JSON string (i.e. placing keys in strings).

7. Which of the games API routes does the front-end application consume (i.e. make requests to)?

- LH:3000/api/games

8. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?

- Unsure, but security springs to mind, to prevent any direct access from the front end to the database? 

## Extension

Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?

- To create a unique id for the database itself, so that we can be sure when running formulas that we are placing information into the correct database.

Add to your diagram the dataflow for removing a game.
