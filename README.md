# Proof of Authority
###How to Launch New Blockchain
Begin by installing environmental configurations and dependencies:

To install the Go Ethereum Tools:

Open your browser and navigate to the Go Ethereum Tools download page at https://geth.ethereum.org/downloads/

Find the proper installation for your OS (also, is it 32 or 64 bit? It matters!)

2.1. Installing in OS X. Click on the "Geth & Tools 1.9.7" to download the applications bundle archive.

After downloading the tools archive, open your "Downloads" folder, and you will find a file named geth-alltools-darwin-amd64-1.9.7-a718daa6.tar.gz in OS X, and a file called geth-alltools-windows-amd64-1.9.7-a718daa6.zip in Windows. Note that the last numbers in the filename could vary depending on the last built available.

Decompress the archive in the location of your preference in your computer's hard drive, and rename the containing folder as Blockchain-Tools.


NEXT, we need to to install MyCrypto Desktop App:

Open your browser and navigate to the downloads page at https://download.mycrypto.com/.
Choose the install necessary for you operating system. Once the install is downloaded, open and follow installation prompts.
Open the app and choose 'Create a new wallet', then 'Generate a wallet'.
It is MOST SAFE to use the "Mnemonic Phrase" option. MyCrypto will generate a unique mnemonic phrase for you; PLEASE STORE IT SOMEWHERE SAFE, OFFLINE!!
Confirm the mnemonic code by selecting the words IN THE SAME ORDER you were given them.
Unlock your wallet by going to "View & Send" and pick "Mnemonic Phrase." Onve you begin to enter the mnemonic phrase, please leave a space between each word. Submit password and choose a wallet address. 
Once the address is chosen, copy it (begins with '0x') as well as your private key. NEVER SHARE YOUR WALLET ADDRESS OR PRIVATE KEY WITH ANYONE!!
At the bottom left of the app, click "Change network" and select "Kovan" testnet.

The steps to set up a genesis block:

Generate your genesis block.

Run puppeth in CLI, and you will be prompted to name your network.

Once the network is named:
Configure a new genesis block, 2
Create new genesis from scratch, 1
Ethash proof of work, 1

Pre-funded account is the addrress from MyCrypt wallet that you created

Should you precompile, press enter or yes

Specify your chain/network ID, you will need this when creating custom network in MyCrypto, ex. 222

Manage existing genesis, 2

Export genesis configurations, 2

This will create files, but you only need networkname.json, enter

Then close it out, control c

Use Geth, a command-line tool to create nodes, initalize nodes, and conenct the node together

Create accounts for two nodes for the network with a separate datadir for each using geth. Copy the address and the private key for each node when it's given and save the password in a safe place.

./geth --datadir node1 account new ./geth --datadir node2 account new

Using geth, initialize each node with the new networkname.json.

./geth --datadir node1 init networkname.json ./geth --datadir node2 init networkname.json

Now the nodes can be used to begin mining blocks

./geth --datadir node1 --mine --minerthreads 1

Scroll up to node1 mine and copy the enode for node2, open a seperate tab for node 2

./geth --datadir node2 --port 30304 --rpc --bootnodes "enode://"

or you can do it this way too.

Run the nodes in separate terminal windows with the commands: Sealer address is the nodes public address key

./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock ./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --allow-insecure-unlock

NOTE: Type your password and hit enter - even if you can't see it visually

Your private PoA blockchain should now be running

Create custom network for node 1 and 2:

With both nodes up and running, the blockchain can be added to MyCrypto for testing.

Open the MyCrypto app, then click Change Network at the bottom left.

Click "Add Custom Node", then add the custom network information that you set in the genesis.

Make sure that you scroll down to choose Custom in the "Network" column to reveal more options like Chain ID:

Type ETH in the Currency box.

In the Chain ID box, type the chain id you generated during genesis creation.

In the URL box, copy and paste: http://127.0.0.1:8545. (default RPC port on your machine). Then you can save & USE CUSTOM NODE.

After connecting to the custom network in MyCrypto, it can be tested by sending money between accounts.

Select the View & Send option from the left menu pane, then click Keystore file.

On the next screen, click Select Wallet File, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click Unlock.

This will open your account wallet inside MyCrypto.

In the To Address box, type the account address from Node2, then fill in an arbitrary amount of ETH.

Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.

Click the Check TX Status when the green message pops up, confirm the logout:

You should see the transaction go from Pending to Successful in around the same blocktime you set in the genesis.

You can click the Check TX Status button to update the status.

Private blockchain is now created.
