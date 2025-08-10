# GEMINI.md
This file provides guidance to GEMINI when working with code in this repository.

## Commonly Used Commands

### Build
To build the project and create a `war` file:
```bash
mvn package
```

### Test
To run all the tests:
```bash
mvn test
```
To run a single test class:
```bash
mvn -Dtest=jp.gr.java_conf.yuta_yoshinaga.reversi4color.test.ReversiTest test
```

### Verify
To build the project, run tests, and perform other checks:
```bash
mvn -B verify
```

## Code Architecture

This is a Java-based web application for playing the game of Reversi. It follows a standard Model-View-Controller (MVC) architecture.

*   **Controller**: The `FrontController` servlet (`src/jp/gr/java_conf/yuta_yoshinaga/reversi4color/controller/FrontController.java`) handles all incoming HTTP requests. It receives the coordinates of a clicked square from the frontend, processes the move, and returns the updated game state as a JSON response.
*   **Model**: The core game logic is implemented in the `jp.gr.java_conf.yuta_yoshinaga.reversi4color.model` package.
    *   `Reversi.java`: This is the main class that encapsulates the Reversi game logic.
    *   `ReversiPlay.java`: This class manages the game play, including validating moves and updating the board state.
    *   The game state is stored in the user's session.
*   **View**: The frontend is composed of HTML, CSS, and JavaScript files located in the `WebContent` directory. The frontend is responsible for rendering the game board and interacting with the user. It communicates with the server via AJAX requests.

The application uses the `jsonic` library for JSON serialization and deserialization. Unit tests are written using JUnit 5.
