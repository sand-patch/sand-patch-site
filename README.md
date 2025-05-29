# sand-patch: Particle, Fractal, and Cellular Automata Simulations  
#### Video Demo: <[URL](https://youtu.be/jVog2D_lnBA)>  
#### Description:

**sand-patch** is an interactive browser-based visualization project developed using [React](https://react.dev/) and [HTML Canvas](https://www.w3schools.com/html/html5_canvas.asp) that brings together three dynamic simulations: a sand/water particle simulation, real-time fractal visualizations, and Conway’s Game of Life. The goal of this project is to demonstrate the beauty of emergent behaviors found in physics, mathematics, and cellular systems through hands-on interaction and intuitive design.

---

### Project Overview:

This project was built to explore different types of self-organizing systems in a single cohesive environment. Each simulation runs in its own isolated component with a unified UI design that emphasizes readability, minimalism, and responsiveness. Users can navigate between the simulations via a top-level React Router interface that mimics the feel of a creative sandbox application.

**The three primary modules are:**

- **Sand/Water Simulation:**  
  A pixel-based falling sand game-like simulation where particles (sand, water) obey simple gravity and collision rules. Sand stacks, water flows around obstacles, and interaction is driven via mouse drawing. This system mimics cellular physics and is implemented with a custom matrix state updated per animation frame. While inspired by [Sandspiel](https://sandspiel.club/), this module uses a physics engine I built from scratch.

- **Fractal Explorer:**  
  A [Mandelbrot](https://en.wikipedia.org/wiki/Mandelbrot_set) set renderer that allows users to zoom, pan, and adjust parameters such as maximum iterations and color schemes. This interactive fractal viewer helps users explore infinite detail, complexity, and mathematical beauty derived from a few simple equations. The fractal canvas is rendered in real-time based on user-controlled parameters. It also includes a variety of additional fractals, such as the [Sierpiński Triangle](https://en.wikipedia.org/wiki/Sierpi%C5%84ski_triangle), [Koch Snowflake](https://en.wikipedia.org/wiki/Koch_snowflake), [Pythagoras Tree](https://en.wikipedia.org/wiki/Pythagoras_tree_(fractal)), and [Cantor Set](https://en.wikipedia.org/wiki/Cantor_set).

- **Game of Life:**  
  An implementation of [Conway’s Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life), where users can click to toggle cell states, then watch patterns evolve based on simple rules of life and death. The simulation highlights how simple rules can lead to surprisingly complex and unpredictable behavior, balancing chaos and order.

---

### File Structure and Code Design:

- **`App.jsx`**  
  This is the root React component, which sets up routing for the three major views. It uses React Router DOM to allow navigation between the Sand/Water, Fractal, and Game of Life modules.

- **`WaterSim.jsx`**  
  This file contains the sand and water particle simulation. It uses a 2D array to model the world grid and updates particle positions using a per-frame loop controlled by `requestAnimationFrame`. Mouse interactions allow users to spawn particles on the canvas.

- **`FractalExplorer.jsx`**  
  Implements the Mandelbrot fractal renderer. It includes controls for zoom level, pan offset, and iterations, with black/white color rendering done per-pixel using canvas image data. It uses double buffering to handle rapid user interaction without frame tearing.

- **`GameOfLife.jsx`**  
  Implements Conway’s Game of Life with a customizable grid. Users can clear, randomize, and step through generations manually or automatically using buttons. Canvas rendering displays alive and dead cells in a pixel grid.

- **`index.css`**  
  Provides a consistent theme across all simulations, with a retro-tech aesthetic using dark backgrounds, monospace fonts, and glowing UI controls. Each panel layout is responsive and designed to keep the user interface intuitive and immersive.

---

### Design Decisions:

A major design goal was to maintain visual consistency and user experience across very different kinds of simulations. To achieve this:

- A shared UI layout (`.panel`, `.left-column`, `.right-column`, etc.) was created and reused.
- Custom hooks and `useCallback` were used to optimize performance and reduce unnecessary re-renders.
- Canvas APIs were chosen over libraries like Pixi.js or p5.js to maintain fine control over rendering and performance.
- The fractal viewer prioritizes pixel-perfect zooming with accurate floating-point math, while the sand sim favors frame speed and simplicity.
- Modular components make future expansions (like adding [Langton’s Ant](https://josephpetitti.com/ant) or [fluid dynamics](https://en.wikipedia.org/wiki/Fluid_dynamics)) easy to implement.

---

### Challenges and Learnings:

One challenge was balancing interactivity with performance, especially in the fractal zoom and sand simulation. Canvas rendering and large 2D state arrays can be expensive, so performance optimization was necessary (e.g., throttling updates, avoiding unnecessary DOM updates, and caching certain values).

Another interesting challenge was designing a consistent user interface that could support such different systems. It was essential to build reusable layout components and to style them in a way that supports usability without distracting from the simulation.

---

### Conclusion:

**sand-patch** is more than just a visual toy—it’s an educational platform for exploring how complexity arises from simplicity. Whether you're fascinated by the infinite spirals of fractals, the physics of particles, or the philosophical implications of the Game of Life, this app provides an accessible way to engage with foundational scientific and mathematical ideas.

Feel free to explore the code, fork the project, and expand it with your own simulation modules!
