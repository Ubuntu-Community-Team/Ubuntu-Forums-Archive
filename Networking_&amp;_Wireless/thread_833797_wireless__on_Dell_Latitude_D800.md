---
title: "wireless  on Dell Latitude D800"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by rdiaztushman on 2008-06-18
Hello all!

New installation of Ubuntu 8.04 on a Dell Latitude D800.  Installation went smoothly but now I can't get the wireless to connect to my router.  It connected 45 minutes ago while I was running Windows XP, but now I've wiped Windows off my computer (intentially)

Here's the output from my terminal:

> 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9b:49:b1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.2 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:2f:9b:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Any help would be appreciated.

Thanks in advance!

---

### Post by Ayuthia on 2008-06-18
> **rdiaztushman said:**
> Hello all!

New installation of Ubuntu 8.04 on a Dell Latitude D800.  Installation went smoothly but now I can't get the wireless to connect to my router.  It connected 45 minutes ago while I was running Windows XP, but now I've wiped Windows off my computer (intentially)

Here's the output from my terminal:



Any help would be appreciated.

Thanks in advance!

You could try the firmware first.  Your card might be recognized in System->Administration->Hardware Drivers.  Just enable the Broadcom card.  If it is not there, open up the Terminal and type:
```
sudo apt-get install b43-fwcutter
```
It will ask you if you want to have it find the firmware for you.  Just say yes and it will install it for you.

---

### Post by rdiaztushman on 2008-06-18
Thanks so much for the quick reply.  Here's the error message I got after running the code you said to run:

> 
$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter


Thoughts?

Thanks again for your help - I hate to be such a pain.

---

### Post by Ayuthia on 2008-06-18
> **rdiaztushman said:**
> Thanks so much for the quick reply.  Here's the error message I got after running the code you said to run:



Thoughts?

Thanks again for your help - I hate to be such a pain.
I am guessing that you have a working internet connection right now in Ubuntu.  If that is the case, have you ran any updates?  If not, please type:
```
sudo apt-get update
```and it should update from the repositories. Once it does that, you should be able to install it.

---

### Post by rdiaztushman on 2008-06-18
Cheers to you, Ayuthia.  The update followed by your initial magic code did the trick.

Thanks!

BTW, where can I find a useful wiki/document that describes exactly what all these words (sudo, apt-get, fwcutter) mean?

Thanks again, especially for being so prompt so late at night.

---

### Post by EXCiD3 on 2008-06-19
Heres the wiki page on Sudo and root: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
This explains aptitude/apt-get and the repositories: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Great place to get started on Ubuntu: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) Explains LOTS of stuff :D

---

### Post by Ayuthia on 2008-06-19
> **rdiaztushman said:**
> Cheers to you, Ayuthia.  The update followed by your initial magic code did the trick.

Thanks!

BTW, where can I find a useful wiki/document that describes exactly what all these words (sudo, apt-get, fwcutter) mean?

Thanks again, especially for being so prompt so late at night.

The fwcutter stands for firmware cutter.  The Linux Broadcom drivers need a portion of the firmware to make it work so that is why it is called fwcutter.

By the way, you don't necessarily need to use apt-get.  You can also use Synaptic.  I tend to use the Terminal a lot...

---

### Post by CoyoteMoss on 2012-10-13
And how is it that you get updates if you can't connect to internet?

---

### Post by overdrank on 2012-10-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

