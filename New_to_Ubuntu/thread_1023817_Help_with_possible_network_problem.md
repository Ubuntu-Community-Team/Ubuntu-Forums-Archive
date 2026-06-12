---
title: "Help with possible network problem???"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by User X on 2008-12-28
I had Ubuntu 8.04 on my PC (installed from a live CD downloaded from Ubuntu.com) and I was trying to get software called EMC2 (from [www.linuxcnc.org](www.linuxcnc.org)) up and running with no luck.  I decided to download and try their live CD as a means of getting EMC2 working.  It worked, so I trashed my existing 8.04 install and began fresh with thie new live CD from linuxcnc.org.  My first instalation hung up when "Configuring APT" and I read on the forums that unplugging the network cable would get the instalation beyond this point.  I tried it, and that worked.  The instation seemed to go fine and I could run EMC2.  However - When I try to use firefox to get online it struggles.  Google.com loaded fine and I can visit all their websites, but when I visit other sites like newegg.com it takes a long time to get anywhere and its like it's not getting any CSS data from the websites.  I can't visit any sites from google with any better results either.  I tried installing a program - Blender - and the update of the repositorys seems to hang and won't complete the indexing.  Update manager, and synaptic packet manager fails as well.  Can anyone help?

This guy appears to have had a simmilar problem...
[http://ubuntuforums.org/showthread.php?t=1021760&highlight=checking+mirror](http://ubuntuforums.org/showthread.php?t=1021760&highlight=checking+mirror)

---

### Post by cariboo on 2008-12-28
We need more information, before we can help. Could paste the output of:

```
sudo lshw -C network
```

in your next post. The above command myst be run in a Applications-->Accessories-->Terminal. Also, how do you connect to the internet, directly through a modem, through a router or some other method.

Jim

---

### Post by User X on 2008-12-28
Here is what I get from that terminal command:

-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:17:31:84:e8:19
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.101 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s

I connect to a wireless router (it is a wired connection though) which connects to my cable modem.  Thanks for your help Jim, I also have stumbled onto this:

[http://ubuntuforums.org/showthread.php?p=2410996#post2410996](http://ubuntuforums.org/showthread.php?p=2410996#post2410996)

Do you think this will help my problem?

---

### Post by User X on 2008-12-29
[https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html)

I have found this on google and was wondeing if someone can answer a few questions I have about it.  

1. I am allready running the 2.6.24-16 rtai kernel so do I begin following this at section 2 in the process?

2. Since I am allready running Hardy do I need to complete step 3 in the process?

---

### Post by User X on 2008-12-29
So in reading another post here on the forums I came across someone with the same problems that I have listed and a "sort of" solution.  I have a dual boot on this system with Ubuntu and Windows XP.  It turns out that my problem is not Ubuntu entirely but also Windows XP.  When I shut down Windows it is my understanding that it places the onboard SIS 190 Network adapter in some sort of suspend mode that I assume has something to do with the main boards ability to WOL and when I boot to Ubuntu the Linux driver is unable to get the network adapter out of the "suspend" mode.  So I shut down the computer and switched off the power supply (or I guess you could unplug it) for about 10 minutes (enough time for the capacitors to dissipate any store energy), then I turned it back on and it works like a charm.  However, every time I shut down windows I have to do this trick.  Anyone know how to disable this feature in Windows? Or make the Ubuntu driver pull the network adapter out of the suspend mode?

---

### Post by User X on 2008-12-30
Bump... because I'd like to find a better solution...

---

