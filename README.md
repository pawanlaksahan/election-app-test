# Election - DAPP Tutorial

Build your first decentralized application, or Dapp, on the Ethereum Network with this tutorial!

Full Free Video Tutorial:\*\*
https://youtu.be/3681ZYbDSSk

## 2022 Updated Code

out-of-the-box for use!

Fix several issues, check CHANGELOG for detail.

## Dependencies

Install these prerequisites to follow along with the tutorial. See free video tutorial or a full explanation of each prerequisite.

- NPM: https://nodejs.org
- Truffle: https://github.com/trufflesuite/truffle
- Ganache: http://truffleframework.com/ganache/
- Metamask: https://metamask.io/

## Step 1. Clone the project

`git clone https://github.com/ArchLinuxStudio/election`

## Step 2. Install dependencies

```
$ cd election
$ npm install
```

## Step 3. Start Ganache

Open the Ganache GUI client that you downloaded and installed. This will start your local blockchain instance. See free video tutorial for full explanation.

## Step 4. Compile & Deploy Election Smart Contract

`$ truffle migrate --reset`
You must migrate the election smart contract each time your restart ganache.

## Step 5. Configure Metamask

See free video tutorial for full explanation of these steps:

- Unlock Metamask
- Connect metamask to your local Etherum blockchain provided by Ganache.
- Import an account provided by ganache.

## Step 6. Run the Front End Application

`$ npm run dev`
Visit this URL in your browser: http://localhost:3000

If you get stuck, please reference the free video tutorial.

---

## Notes

1. Use `web3.eth.getAccounts()` to get accounts now
2. To bootstrap sample truffle project, use command `truffle unbox pet-shop`

---

## Deploy to rinkeby test network

1. Run geth node

```bash
geth --rinkeby --http --http.api personal,eth,net,web3 --allow-insecure-unlock
```

This can take dozens of hours, depending on your machine configuration and internet speed.  
This will cost you close to 100GB or so of hard drive space.

2. Create a new account

```bash
geth --rinkeby account new
```

3. Attach into geth console

```bash
geth --rinkeby attach
```

And you can do many things in geth console

```bash
eth.syncing     #check the syncing status
eth.accounts    #check all accounts
eth.getBalance(eth.accounts[0]) #check account balance
personal.unlockAccount(eth.accounts[0],null,1200)   #unlock a certain accont for 20 minutes
```

4. Acquire eth from https://www.rinkeby.io/#faucet

Here they require that you have to post a twitter or facebook, which is disgusting.

5. Migrate

```bash
truffle migrate --reset --compile-all --network rinkeby
```

6. Verify deployment

```bash
geth --rinkeby attach
```

```bash
var contractAddress = "Your_Contract_Address"
var contractAbi = [Your_ABI_Array] #copy the abi array in build/contracts/Election.json, turn it into one line style
var electionContract = web3.eth.contract(contractAbi)
var electionInstance = electionContract.at(contractAddress)
electionInstance.candidates(1)
electionInstance.vote(1, {from: eth.accounts[0]});
```
