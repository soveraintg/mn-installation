# Soverain TG
Shell script to install a [Soverain Masternode](https://soverain.org/) on a Linux server running Ubuntu 16.04,18.04 or 19.04. Use it on your own risk!

***
## Installation (on VPS):
```
wget https://raw.githubusercontent.com/soveraintg/mn-installation/master/sovemnscript.sh
sudo chmod +x sovemnscript.sh && sudo bash sovemnscript.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Soverain Core Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **6000** **SOVE** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:

```
Alias Address Privkey TxHash Output_index
```

Your entry should look something similar to this --

```
MN1 1.2.3.4:18976 87sHUmXu8eTD7MuNdEbWtCJK1xoy1kkBeywtxiyDY6nf2DSVzm8 9875493746f1cb7638719272faeabbd2b90795eaaf96c08393a31bba4dbbfc50 0

```


* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key** (from your VPS!!!)
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** and type:
```
startmasternode alias false MN1
```
***

## Usage:
```
soverain-cli getinfo
soverain-cli mnsync status
soverain-cli masternode status
```

Also, if you want to check/start/stop **Soverain** on your VPS, run one of the following commands as **root**:

```
systemctl status soverain #To check if Soverain service is running
systemctl start soverain #To start Soverain service
systemctl stop soverain #To stop Soverain service
systemctl is-enabled soverain #To check if Soverain service is enabled on boot
```

***
