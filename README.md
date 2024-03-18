# A3C_for_KungFu
Using Asynchronous Advantage Actor-Critic Algorithm to train a RL model to play Kung Fu Master


https://github.com/ruchakhopkar/A3C_for_KungFu/assets/70127769/23893722-5b46-41ee-ac82-04bc97af74fb


\n I have used one of the environments from [gymnasium](https://gymnasium.farama.org/content/basic_usage/) called KungFuMasterDeterministic-v0, in which some of the actions of the villains are deterministic and many other actions are non-deterministic.
\n I built a neural network containing convolutional and linear layers which gives as output, the action values(size 14) and the state values(size 1). 
\n The input in this case is a stack of 4 grayscale images of dimension 42 * 42.
\n In any given state, the agent can take 1 of 14 different actions: ['NOOP', 'UP', 'RIGHT', 'LEFT', 'DOWN', 'DOWNRIGHT', 'DOWNLEFT', 'RIGHTFIRE', 'LEFTFIRE', 'DOWNFIRE', 'UPRIGHTFIRE', 'UPLEFTFIRE', 'DOWNRIGHTFIRE', 'DOWNLEFTFIRE']
\n I then create an agent with 2 functions: act and learn(step)
\n In the act function, given a state the agent will take some action based on the output from the neural network. The action is chosen based on a softmax function for exploration-exploitation.
\n In the step function, the agent actually learns. It computes the advantage of taking a certain action in a certain state(Q(s,a) - V(s)). It backpropagates on the actor's loss(log probability of the action chosen * advantage - entropy) and the critic's loss (MSE between target state value and predicted state value).
\n I used Adam as an optimizer. 
\n I then write a few functions to handle the multiprocessing through the different agents in the environment. 
