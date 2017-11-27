

# Sumokoin mining howto

- [Sumokoin mining howto](#sumokoin-mining-howto)
  * [Step 1: Setting up your wallet](#step-1--setting-up-your-wallet)
    + [Using the GUI wallet](#using-the-gui-wallet)
      - [Installation](#installation)
      - [Creating a Sumokoin wallet](#creating-a-sumokoin-wallet)
      - [Synchronizing to the network](#synchronizing-to-the-network)
  * [Step 2: Choosing a pool](#step-2--choosing-a-pool)
    + [How to choose a pool](#how-to-choose-a-pool)
      - [Location of the pool](#location-of-the-pool)
      - [The pool fee](#the-pool-fee)
      - [Miners and hashrate of the pool](#miners-and-hashrate-of-the-pool)
    + [Getting the URL/port for miners](#getting-the-url-port-for-miners)
  * [Step 3: Setting up your mining software](#step-3--setting-up-your-mining-software)
    + [CPU: Using SumoEasyMiner](#cpu--using-sumoeasyminer)
      - [Installation](#installation-1)
      - [Starting to mine](#starting-to-mine)
    + [GPU: Using xmr-stak](#gpu--using-xmr-stak)
    + [GPU: Using ccminer](#gpu--using-ccminer)
  * [Step 4: Profit](#step-4--profit)
    + [Monitoring mining progress](#monitoring-mining-progress)
    + [Receiving SUMOs](#receiving-sumos)
  * [Support](#support)


## Step 1: Setting up your wallet

### Using the GUI wallet
![A fresh sumo wallet](/pics/sumo-wallet.png)

#### Installation
You can find the download link to the GUI wallet on the bottom of https://www.sumokoin.org.

Download the wallet and extract it's content:

```shell
tar -xjvf ~/Downloads/Sumokoin_Wallet-v0.0.1-b2-Linux-x64.tar.gz2
Sumokoin_Wallet-Ubuntu16.04-x64/
Sumokoin_Wallet-Ubuntu16.04-x64/_codecs_hk.so
Sumokoin_Wallet-Ubuntu16.04-x64/libgstvideo-1.0.so.0
Sumokoin_Wallet-Ubuntu16.04-x64/_codecs_jp.so
Sumokoin_Wallet-Ubuntu16.04-x64/_codecs_kr.so
Sumokoin_Wallet-Ubuntu16.04-x64/libfreetype.so.6
Sumokoin_Wallet-Ubuntu16.04-x64/PySide.QtCore.so
Sumokoin_Wallet-Ubuntu16.04-x64/libdrm.so.2
Sumokoin_Wallet-Ubuntu16.04-x64/libICE.so.6
....
```

Now go into the extracted directory and run the wallet:

```shell
cd Sumokoin_Wallet-Ubuntu16.04-x64/
./wallet
```
#### Creating a Sumokoin wallet
So you have now installed the wallet software and it's running. You still need to create an actual Sumokoin wallet on the network. This wallet will have a unique address to which sumo coins can be send.

 * In the "New Wallet" section click on "Create"
 * You are prompted for a password: choose a secure one.
 * Choose you language
 * Write down the mnemonic seed.
 * WRITE DOWN THE MNEMONIC SEED!
 
 The mnemonic seed is a set of words that allows you to restore your wallet on any computer. You absolutely want to write down these words in a secure place (not the same computer as your wallet) so that you can regain access to your wallet in case your computer dies on you.

 * Now click "Open wallet"

#### Synchronizing to the network
The wallet needs to synchronized to the network. This unfortunately might take several hours and once it is done; you will see "Network synchronized".

This doesn't matter; while the wallet is synchronizing we can still move on to the next step, which is choosing a pool.

## Step 2: Choosing a pool
Mining is typically done using pools that shard work to miners. The benefit of using a shared pool is that you will have faster results, as in, payouts. 

You can find a list of pools on https://www.sumopools.com

### How to pick a pool
When choosing a pool you want to take into account the following factors:
 * Location of the pool
 * The pool fee
 * Miners and hashrate of the pool
 
#### Location of the pool
It's best to choose a pool that is located in your region to ensure you get a low latency connection with it.

#### The pool fee
Running a pool costs money and effort. Many pools therefore have a fee that is around 0.1 - 1 percent of the sumo that is awarded. This is completely reasonable and don't let the fee influence your decision too much when picking a pool (unless the fee is >1% perhaps).

#### Miners and hashrate of the pool
Pools that have several miners usually also have a decent hashrate. You can see the amount of miners and hashrate on the www.sumopools.com website.  When you visit the pool's website you can also see how often blocks are found: this directly translates to how often sumo is being payed out to miners.

Note that pools with high numer of miners might get overloaded. This sometimes is the case with the official pool (pool.sumokoin.com) and mentioned on their pool site.

### Getting the URL/port for miners

Pools have multiple ports to which miners can connect. Most pools run software called "cryptonote-sumokoin-pool" and have a dedicated "Getting started" page on which you can find the ports to which you can connect.

An example of such a page is here https://pool.sumokoin.ch/#getting_started and from that page you'd learn that the miners can connect to pool.sumokoin.ch:4444, pool.sumokoin.ch:4445 and pool.sumokoin.ch:4446.

## Step 3: Setting up your mining software
There are many different miner software packages out there. I'll cover a few and will prefix them with CPU and GPU to indicate the type of mining they do.

### CPU: Using SumoEasyMiner

![SumoEasyMiner](/pics/sumoeasyminer.png)


#### Installation

The installation is actually described here:
https://github.com/sumoprojects/SumoEasyMiner

#### Starting to mine

 * Start SumoEasyMiner with: python sumominer.py
 * Click on "Add Pool" in the top right corner
 * At URL/Port enter the pool URL that you obtained in the "Choosing a pool section". E.g. pool.bla.com:4444.
 * Enter the wallet address
   * To get this address: open you GUI wallet
   * In the wallet GUI click "Receive" in the top right and copy the "Address" value (which starts with Sumo.."
 * In the password entering "x" will work for most pools. The password of the pool can usually be found on the pool's getting started page.
 * Click OK and you're good to go.
 
### GPU: Using xmr-stak for NVIDIA

#### Installation

Follow the below example to install the required packages, fetch and configure the code:
```shell
sudo apt-get install cmake gcc g++-5 libcuda1-352 nvidia-cuda-dev nvidia-cuda-toolkit libssl-dev libhwloc-dev
git clone https://github.com/fireice-uk/xmr-stak.git
cmake . -DMICROHTTPD_ENABLE=OFF
-- The C compiler identification is GNU 5.4.0
-- The CXX compiler identification is GNU 5.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Set miner currency to 'monero' and 'aeon'
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Found CUDA: /usr (found suitable version "7.5", minimum required is "7.5") 
-- Looking for CL_VERSION_2_0
-- Looking for CL_VERSION_2_0 - found
-- Found OpenCL: /usr/lib/x86_64-linux-gnu/libOpenCL.so (found version "2.0") 
-- Found OpenSSL: /usr/lib/x86_64-linux-gnu/libssl.so;/usr/lib/x86_64-linux-gnu/libcrypto.so (found version "1.0.2g") 
-- Configuring done
-- Generating done
-- Build files have been written to: /home/xxx/xmr-stak

make
```

Now build the code:

```shell
make
Scanning dependencies of target xmr-stak-c
[  2%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_jh.c.o
[  5%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_skein.c.o
[  8%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_blake256.c.o
[ 11%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_keccak.c.o
....
....
```

#### Running it

If your system did not have nvidia drivers before building xmr-stak; go and reboot now.
Now simply run the binary and answer the questions:

```shell
./bin/xmr-stak 
Please enter:
- Currency: 'monero' or 'aeon'
monero
- Pool address: e.g. pool.usxmrpool.com:3333
pool.sumokoin.ch:4445
- Username (wallet address or pool login):
Sumoo183tSKPM45fr58fVyK3SCgHCDhHMFgc8MNMM7uxH5vjyyu9zs8dCsfRysapCSVzjfBZgRAUfRe7GGmoQEbZJenUUXWrQrq
- Password (mostly empty or x):
x
- Does this pool port support TLS/SSL? Use no if unknown. (y/N)
n
- Do you want to use nicehash on this pool? (y/n)
n
- Do you want to use multiple pools? (y/n)
n
Configuration stored in file..
.....
.....
```

And you're good to go !

// TODO

### GPU: Using ccminer
// TODO

## Step 4: Profit

### Monitoring mining progress
// TODO

### Receiving SUMOs
// TODO

## Support

If you want to support this guide; perhaps consider using my pool as https://pool.sumokoin.ch.

