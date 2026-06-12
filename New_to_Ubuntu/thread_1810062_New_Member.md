---
title: "New Member"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by dannymoro on 2011-07-22
Hi, I can't connect to internet (firmware missing)  Have dell inspiron 1510, windows 7
dell wireless ...802.11g half mini card.   i am using a dual boot. cAN someone help me? thank you.        
                       danny m

---

### Post by Enigmapond on 2011-07-22
Welcome to the forum! I don't know what distro you are using, but if you navigate to Administration/Hardware Drivers (or Additional Drivers) on a wired connection, it will install the Broadcom Driver for you. Hope this helps!

Cheers!

---

### Post by dannymoro on 2011-07-22
thanks for responding.  distro?  ubuntu 11.  newest version.  i need to connect wirelessly.

---

### Post by Enigmapond on 2011-07-22
> **dannymoro said:**
> thanks for responding.  distro?  ubuntu 11.  newest version.  i need to connect wirelessly.

Right but in order to do that, you need a wired connection and navigate to where I said before and it will download the driver. After it installs, you will be able to connect on the wireless...

---

### Post by amjjawad on 2011-07-22
> **dannymoro said:**
> thanks for responding.  distro?  ubuntu 11.  newest version.  i need to connect wirelessly.

Hello and Welcome :)

From Terminal, please run this command and post the output here:

```
sudo lshw -C network

```

Please, post the output and wrap up the text with "CODE" tags.

---

### Post by dannymoro on 2011-07-23
o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

danny@danny-Inspiron-1545:~$ sudo lshw -C network
[sudo] password for danny: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:76:60:8c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:87:29:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
danny@danny-Inspiron-1545:~$

---

### Post by dannymoro on 2011-07-23
Success!  Thanks for your help.  After finding out how to open a terminal and posting my results, i followed first advice toconnect thru router, download broadcom driver, restart and disconnect from router. hopefully, i wiill still be able to connect with windows.
now i can have some fun while learing ubuntu.  Thanks again.

---

### Post by sadaruwan12 on 2011-07-23
Now this problem started after you installed ubuntu right. Some times the wireless get disabled do you have a switch or a function key to enable wireless on your laptop.

One I use have I've to switch it on and restart at the first time after a new install of Ubuntu but after that every thing works.

It seems to be your wlan interface is down you cloud try this in the terminal.

```
sudo ip link set wlan0 up
```

[Click]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") Here nice referral might help you.

NOTE: If your into Linux make Google your pal and internet your girlfriend ;-) cheers.

---

### Post by dannymoro on 2011-07-23
yes , problem started after my friend loaded ubuntu on my dell.
i am able to connect now so i am good.
 not a programming type so i will go slowly with the terminal. Like to learn basics of ubuntu. use computer mainly for internet (ofcourse). We will see what happens.

---

### Post by sadaruwan12 on 2011-07-23
OK, then friend please mark the thread as solved if your issue is over thank you for being a user of Ubuntu Linux.

---

### Post by amjjawad on 2011-07-23
> **dannymoro said:**
> 
  
```
*-network [COLOR=Red]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:87:29:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=**[COLOR=Red]b43[/COLOR]** driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
danny@danny-Inspiron-1545:~$
```


It looks like your Wireless Network was disabled and there is a driver already installed.

Anyway, I hope you managed to fix your problem :)

---

### Post by dannymoro on 2011-07-23
Thanks for help.  spent some time trying to mark my thread as solved but not sure how to.  

Thread is solved!

---

### Post by amjjawad on 2011-07-23
> **dannymoro said:**
> Thanks for help.  spent some time trying to mark my thread as solved but not sure how to.  

Thread is solved!

This is how :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

