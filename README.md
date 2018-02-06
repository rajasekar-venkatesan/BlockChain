# BlockChain
Blockchain implementation in Python

## Run servers:
Terminal 1:
python blockchain.py

Terminal 2:
python blockchain.py --port 5001

Terminal 3:
python blockchain.py -p 5002

...


## Transaction template:
{
'sender': <sender-name/id>,
'recipient': <recipient-name/id>,
'amount': <transaction-amount>,
}


## HTTP POST Operations
### 1) Add Transactions:
Example: To add a transaction to the node in port 5000 \n
$ curl -X POST -H "Content-Type: application/json" -d '{"sender": "sender-name/id", "recipient": "recepient-name/id", "amount": 5}' "http://localhost:5000/transactions/new"

### 2) Register Nodes:
Example: To register a neighbouring node(:5000) with a node(:5001) \n
$ curl -X POST -H "Content-Type: application/json" -d '{"nodes": ["http://127.0.0.1:5000"]}' "http://localhost:5001/nodes/register"

## GET Operations
### 1) Mine: 
Creates/Mines for a new block with all the transactions since previous block \n
http://localhost:5000/mine

### 2) Chain: 
Displays the blockchain held by that node \n
http://localhost:5001/chain

### 3) Resolve nodes: 
Compares a node's own chain with its neighbours' chain and resolve which chain to use. \n
http://localhost:5000/nodes/resolve


## Block template:
{ \n
'index': <id>,
'timestamp': <time>,
'transactions': [<transactions>],
'proof': <proof-value>,
'previous_hash': <hash value of previous block>
}
