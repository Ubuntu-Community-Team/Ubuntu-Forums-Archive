---
title: "wireless networking in kubuntu"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by limac on 2007-11-25
hey,

i just made a switch from ubuntu to kubuntu, and would require your help getting me set up and ready to go for wireless networking access. I have atheros wireless 802.11b/g PCI express adapter. 

Thx

---

### Post by kevdog on 2007-11-25
Setting up wireless isnt any different between the two distributions.

---

### Post by limac on 2007-11-25
for Ubuntu I didn't have to set it up or anything, If I just clicked on the wireless (network) icon on the top of the screen, the possible wireless connections automatically appeared. but for this it is saying no active device once i click on it (the unplugged icon on the bottom of the screen. All i need to know is how to set up the wireless connection in kubuntu

Thnx

---

### Post by razrlazr on 2007-11-25
Many Ubuntu tools can be used in Kubuntu.  To set up your wireless network in Kubuntu, go to the System Settings area and click on Network Settings. Click Administrator Mode and enter your password.  Highlight the correct interface and click the configure interface button below.  From there you can enter the credentials, etc. for your wireless network.

After you do that, you can monitor the connection using kwifimanager or the ubuntu utility.

marytee
---------------------------
Detroit USA

---

### Post by limac on 2007-11-25
> **razrlazr said:**
> Many Ubuntu tools can be used in Kubuntu.  To set up your wireless network in Kubuntu, go to the System Settings area and click on Network Settings. Click Administrator Mode and enter your password.  Highlight the correct interface and click the configure interface button below.  From there you can enter the credentials, etc. for your wireless network.

After you do that, you can monitor the connection using kwifimanager or the ubuntu utility.

marytee
---------------------------
Detroit USA

But there is only one interface below that says eth0.

---

### Post by kevdog on 2007-11-25
Please post

lshw -C network

Is this a new distribution you just installed (brand new installation)?

---

### Post by limac on 2007-11-25
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:fe:f8:1e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=10.12.6.76 latency=0 module=r8169 multicast=yes
limac@limac-kubuntu:~$                                                   

This is what it resulted as.

And I just installed kubuntu 7.10 today, and that's all that's there in my hard disk.

---

### Post by kevdog on 2007-11-25
All good news for you all the way around.  

#1 - You have a wired connection -- Use it

#2 - Determine your kernel version -- uname -r

#3 - Use synaptic or adept(kde) to download the linux restricted package for your kernel version. This will install the madwifi drivers for your card (ath_pci).  Reboot, and you should be good to go.

---

### Post by limac on 2007-11-25
my kernel version is 2.6.22-14-generic

But in adept all the restricted drivers are installed

---

### Post by kevdog on 2007-11-25
Ok -- just checked the madwifi page and your card is definitely supported.  Do something for me:

sudo updatedb
locate ath_pci

What does this show? Only show me a directory this relates to your kernel verison.

---

### Post by limac on 2007-11-26
limac@limac-kubuntu:~$ sudo updatedb
[sudo] password for limac:
limac@limac-kubuntu:~$ locate ath_pci
/lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko
limac@limac-kubuntu:~$

This is what that shows.

---

### Post by kevdog on 2007-11-26
Can you do the following

sudo modprobe ath_pci > log.txt

Can you repost
lshw -C network
log.txt

---

