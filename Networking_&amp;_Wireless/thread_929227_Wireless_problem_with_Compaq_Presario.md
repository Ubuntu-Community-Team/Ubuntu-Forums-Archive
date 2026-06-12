---
title: "Wireless problem with Compaq Presario"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Bill Purvis on 2008-09-24
I have a Compaq Presario F767NR with an Atheros integrated wireless. When I click system>administration>hardware drivers shows that it is enabled and in use but when I click the manual network settings in the system tray it does not show a wireless connection. can anyone help me get this running? I am a complete newbie to Linux, just installed ubuntu yesterday.

---

### Post by SvistoSK on 2008-09-24
Hi buddy, i am newbie too , so do not expect a lot, just little help.
Go to the Terminal and type in ,, iwlist scanning ,, .
If is wifi working , it should list something like this here:

martin@ghost-recon1:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:B5:E1:1C
                    ESSID:"SvistoTheOne"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=2
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK



In this case wlan0 is wireless card.So you should see available wireless networks  around,if any.Ofcourse,if your card is working.

---

### Post by Bill Purvis on 2008-09-24
Ok. opened the terminal and typed in iwlist scanning  this is what was returned -
bpurvis@bpurvis-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

When I am in Vista the wireless works.

---

### Post by willca on 2008-09-25
post this and see what kind of card is it.

sudo lspci | grep Ethernet

---

### Post by zxscooby on 2008-09-25
Is the switch on?

---

### Post by SvistoSK on 2008-09-25
> **Bill Purvis said:**
> Ok. opened the terminal and typed in iwlist scanning  this is what was returned -
bpurvis@bpurvis-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

When I am in Vista the wireless works.
Right, it seems that wifi is not working.You need to find out what wireless card is in your laptop.So give a try what willca suggests.
(sorry for english:-D i am slovakian.)

---

### Post by Bill Purvis on 2008-09-25
I will try that as soon as I get home from work. I assume that I type in the command (sudo lspci | grep Ethernet)from the terminal.

---

### Post by Bill Purvis on 2008-09-25
OK, below are the results.

bpurvis@bpurvis-laptop:~$ sudo lspci | grep Ethernet
[sudo] password for bpurvis: 
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
bpurvis@bpurvis-laptop:~$

---

### Post by willca on 2008-09-26
OK have not had a chance with atheros personally since i dont own one. But this should take care of it for this chipset.

You have to disable anything that Hardy installed via Hardware Drivers. Look for anything that is Atheros and disable it and reboot.

Then do below.

save this file in a directory.

wget -c [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6) current.tar.gz

tar xvf madwifi*.tar.gz

cd madwifi*r3862*

sudo apt-get update && sudo apt-get install build-essential

Then run the following commands to compile madwifi.

make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

Test it out if it works.
sudo iwlist ath0 scan

I think its ath0 or wlan0. Just try either.

Remember if you update your Hardy and a new kernel gets installed, you will need to redo this again.

---

### Post by SvistoSK on 2008-09-26
> **willca said:**
> OK have not had a chance with atheros personally since i dont own one. But this should take care of it for this chipset.

You have to disable anything that Hardy installed via Hardware Drivers. Look for anything that is Atheros and disable it and reboot.

Then do below.

save this file in a directory.

wget -c [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6) current.tar.gz

tar xvf madwifi*.tar.gz

cd madwifi*r3862*

sudo apt-get update && sudo apt-get install build-essential

Then run the following commands to compile madwifi.

make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

Test it out if it works.
sudo iwlist ath0 scan

I think its ath0 or wlan0. Just try either.

Remember if you update your Hardy and a new kernel gets installed, you will need to redo this again.

Willca ,how do you get this done , look for anything that is Atheros and then to disable it?Do you mean to remove all ,,Atheros,, entries (records) ?

---

