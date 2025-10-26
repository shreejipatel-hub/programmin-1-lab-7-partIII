Project: automaton
Aothors: David J. Barnes and Michael Kölling

This project is part of the material of the book

   Objects First with Java - A Practical Introduction using BlueJ
   Seventh edition
   David J. Barnes and Michael Kölling

It is discussed in chapter 7.


27)yes it depicts pretty much the same behaviour but unlike automaton controller automaton asks us for a for a number of cells as a parameter and from my observation it seems likes the pattern depends on that number.
28) the fill method is used to fill the array with a specific type of value.
29) the single "1" produces a pattern with large triangles but with three separated "1" causes the initial pattern to interact and overlap.
yes the patterns are deterministic.
30) left = (i == 0) ? 0 : state [i = 1];
	right = (i + 1 < state.length) ? state [i + 1] : 0;
31)the nextstate array is created to preserve the integrity of the current generation while the next is being calculated.it basically serves as a buffer to store all the new values until the new calculations are done.if we change it the simulation will be broken and make patterns which doesnt make any sense.
32)what we can do is make a temporary variale and store the values in there but its way more tricky compared to the original solution.
34)private int calculateNextState(int left, int right, int center)
    {
        return (left + center + right) % 2;
    }
36)// Build the new state in a separate array.
        int[] nextState = new int[numberOfCells];
        // Naively update the state of each cell
        // based on the state of its two neighbors.
        int left = 0;
        int center = state[0];
        for(int i = 0; i < numberOfCells; i++) {
            
            int right = (i + 1 < state.length) ? state [i + 1] : 0;
            
            nextState[i] = calculateNextState(left, right, center);
            left = center;
            center = right;
        }
        state = nextState;

