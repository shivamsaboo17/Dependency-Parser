# Dependency-Parser
Transition based neural parser for determining grammatical semantics in a corpus.</br>
They are widely used to find grammatical structures as well as resolve ambiguity from the sentences like...</br>
![Parsing ambiguous sentences](/images/Capture.PNG)
### The sentence is parsed by choosing for each word, what other word (including ROOT) it is dependent of.</br>
![](/images/download.png)
### Constraints for building such parser:</br>
1) Only one word is dependent on the root.</br>
2) We don't want any cycles i.e A -> B and B -> A</br>
### Greedy Transition based parser</br>
A stack and a buffer is maintained. Initially the stack is empty and the buffer consists of all the words of a sentence.</br>
There are 3 operations we perform on them for parsing:</br>
1) SHIFT : Take the top word from the buffer and put it in the stack.</br>
2) LEFT ARC: The left word in the stack depends on the right word.</br>
3) RIGHT ARC: The right word in the stack depends on the left word.</br>
![](/images/Capture1.PNG)
### Deciding the next operation...</br>
This is where our neural network comes into action. The above is a simple classification problem for 3 operations namely SHIFT, LEFT ARC and RIGHT ARC. The operation with highest probability from the neural network is performed for parsing.</br>
For input we choose features like top word in stack, top word in buffer, previous operation performed etc.
