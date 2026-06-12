---
title: "No network connection"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by adam_benson on 2008-01-21
Hi there,

I have installed 7.04 and am trying to connect to my home wireless network. I know the network is up and working for a Vista machine, as that is how I am visiting this site. I cannot seem to get the new desktop connected. The [FONT="Courier New"]iwconfig[/FONT] command tells me the wireless network card is disabled and I cannot find a way to changed this.
I have read many of the previous post and can supply the usual responses. I would appreciate your help in getting this problem resolved.
thanks,
Adam
```

adam@adam-desktop:/$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

adam@adam-desktop:/$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      No scan results
adam@adam-desktop:/$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

adam@adam-desktop:/$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 12
       serial: 00:19:21:57:bd:1f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 multicast=yes
       resources: iomemory:fdbfc000-fdbfffff ioport:ce00-ceff irq:17
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@04:01.0
       logical name: eth0
       version: 02
       serial: 00:1d:7e:06:3c:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fd8fc000-fd8fdfff irq:20
adam@adam-desktop:/$ 




```

---

### Post by jeffus_il on 2008-01-21
Here is a thread showing how to set up your network card, It seems like your card is not supported by a native Linux driver, so you will have to use a driver called ndiswrapper, which "wraps" the windows driver. Apparently, the manafucturers of the card are not divulging technical information to allow the open source community to develop the driver.
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by adam_benson on 2008-01-21
Thanks! I'll try this. -Adam

---

### Post by ugm6hr on 2008-01-21
Theo ther option is to install Gutsy 7.10, which has the Broadcom driver as a "Restricted" driver.

The pros / cons of ndiswrapper vs bcm drivers for Broadcom cards are posted all over this forum.

---

### Post by adam_benson on 2008-01-21
I've installed ndiswrapper-1.15
I pulled out the wireless adapter card to verify that I had the right card and version (it's still workign in vista).
I put the driver files (bcml5.inf & bcml5.sys) into /tmp
I entered
```

sudo ndiswrapper -i bcmwl5.inf

```
the response was
```

driver already installed

```
When I check the driver I get
```

adam@adam-desktop:/tmp$ sudo ndiswrapper -l
bcm43xx : invalid driver!
bcmwl5 : invalid driver!
drivername : invalid driver!
adam@adam-desktop:/tmp$ 

```
Just to make sure I had read and followed all the instructions, I followed the last command:
```

sudo ndiswrapper -m

```
and restarted my machine.

Now what I go to network settings, I have nothing showing the wireless adapter.

As always, I appreciate this forums help with this.
-Adam

---

### Post by jeffus_il on 2008-01-21
Try to uninstall the driver (ndiswrapper -e) first before you install, 
Would you like to try 7.10 as the previous poster recommended?

---

### Post by adam_benson on 2008-01-21
I'm thinking I'll try that. Thanks -Adam

---

### Post by adam_benson on 2008-01-21
OK I have 7.10 installed now and am facing the same issue. Here are the results of the various commands:
```

ubuntu@ubuntu:~$ sudo iwcnfig
sudo: iwcnfig: command not found
ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      No scan results

eth1      Interface doesn't support scanning.

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 12
       serial: 00:19:21:57:bd:1f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth0
       version: 02
       serial: 00:1d:7e:06:3c:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
ubuntu@ubuntu:~$ 

```

thanks for your time,
Adam

---

### Post by jeffus_il on 2008-01-22
Did you install the restricted drivers package and run the restricted drivers setup utility?

See this thread:
[http://ubuntuforums.org/showthread.php?t=587549](http://ubuntuforums.org/showthread.php?t=587549)

Don't give up yet, there are people who have managed to get it working.

---

### Post by adam_benson on 2008-01-22
I hauled my machine to an Ethernet drop and the restricted drivers notice cam up. I grabbed those and am now look for instructions on how to install them (I'm guessing it's not as simple as just rebooting but I'll give that a shot too). I also need to confess that when the drivers were downloaded I did not see where they went - so locating them, if I need to, may be a challenge.
I'm going to reboot and then follow the link you just gave me.
good times...
Adam

---

### Post by adam_benson on 2008-01-22
So, that seemed to help with the card. iwlist can see my home network. I'm going to unplug my machine from the LAN. I will then see if the wireless icon up on the right sees the network then.
wish me luck,
Adam

---

### Post by adam_benson on 2008-01-22
Well that worked. I took the machine to a wired connection, got the updates and restricted drivers, and here I am connected to the Internet by wireless LAN card.
Thank you for your time! =)
-Adam

---

### Post by adam_benson on 2008-01-22
One last resource:
I found this link to be especially helpful regarding the restricted drivers for an acer machine.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)
best of luck
-Adam

---

