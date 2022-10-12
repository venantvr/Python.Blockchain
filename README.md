# Build a blockchain protocol for a distributed ledger

## Demystifying blockchain through a simple coding examples

Background vector created by freepik — www.freepik.com
In this post I am going to build a simple distributed ledger using a blockchain, expanding on tutorials by CodeAcademy and others to explain some of the key mechanisms around blockchain and how they might be implemented in Python.

## An quick overview of blockchain
The basic idea of a blockchain protocol is to preserve a database called a ledger across a distributed network of machines or nodes. Ledgers can be used for anything, to hold transactions or digital currency as is the case for BitCoin or Ethereum. To maintain the integrity of the ledger which is held in different places across the network, the blockchain protocol rewards participants on the network when they solve a computational intensive problem — a process referred to as mining. It is this process into which participants on the network enter into, that ensures the integrity of the distributed ledger on public networks. A blockchain is essentially a proof of the solutions to the problems that participants on the network solve, which are linked together in a chain, and with each new solution found, a new block is created, and into which the next set of records are copied.

## Building a Blockchain Class
First, we’ll build the Blockchain class constructor method that creates an initial empty list (to store our blockchain) and another to store the ledger —a record of transactions. The Blockchain class object will be responsible for managing the entire blockchain. We’ll create the following methods to help us manage the blockchain :

[1] register_node() — this method will register a new node on the network

[2] new_block() — this method will create a new block in the blockchain, copy recent transactions into this new block and clear the set of transactions.

[3] valid_proof() — this method will check that a block being submitted to add to the blockchain solves the problem.

[4] proof_of_work() — this method will check that mining has yielded the correct proof to create the next block in the blockchain. We return the proof if the proof is correct, otherwise it will keep calling valid_proof() until we find a valid proof.

[5] valid_chain() — this method will iterate through the entire blockchain calling valid_proof() to check subsequent blocks are valid.

[6] new_transaction() — this method will add a new transaction to the list of transactions.

[7] last_block() — this method will return the last block in the chain.

Here is how the Blockchain class looks :

### Resolving conflicts on the network
Since the Blockchain protocol is run over a distributed network we’ll need a method on the Blockchain class object to resolve conflicts on the network. We’ll simply check if there are any other blockchains on the network that are longer than ours and if so, make that our own chain, otherwise we can continue to mine in the knowledge that we are mining for the next block and our efforts are worth it.

### Interacting with the Blockchain
Finally, to bring our blockchain to life and to interact with it, we can expose a number of methods via a web app interface using flask.

### Registering a node on the network
We’ll want to allow users to register a node on the network so they can participate in the proof of work process and be rewarded for their efforts. We call the register_node() method on the Blockchain class object to register a node.

We’ll also want to allow these participants to check if their Blockchain is valid and fetch the Blockchain from the network if it isn’t.

### Adding Transactions to the Blockchain
We want to allow participants to add transactions to the ledger. To do this, we simply call new_transaction() on our Blockchain class object with the transactional details to be added.

### Mining
One last important thing! We need to create the interaction to allow participants on the network to mine their blockchain.

Now we can instantiate the flask app, create the Blockchain class object and run the flask application and interact with our blockchain.

To download the full code file see : https://github.com/jamesdhope/blockchain

### References
[1] https://www.wikihow.com/Build-a-Blockchain-App

[2] https://www.codecademy.com/learn/introduction-to-blockchain/modules/blockchain-in-python

[3] Daniel van Flymen, https://hackernoon.com/learn-blockchains-by-building-one-117428612f46.

[4] https://towardsdatascience.com/building-a-minimal-blockchain-in-python-4f2e9934101d

[5] Omer Goldberg, https://hackernoon.com/building-a-blockchain-the-grey-paper-5be456018040
