---
title: "Wireless Network Not Working In Ubuntu 9.10"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by renegadespork on 2009-11-23
As always, I was very hesitant to start a new thread about my issue, but it seems I have exhausted my searching capabilities on the forums, so this seems to be my last option. Perhaps my problems has already been solved, but I'm not really knowledgeable enough to know exactly what is causing my problem to know what solution to look for. 

Essentially, here's my issue:

I recently installed Ubuntu 9.10 on my Macbook 4,1 model (the first time I've used any sort of linux), and everything is working great. The only problem I seem to have is that I can't get it to recognize any wireless networks. I assume it's a driver issue, because I have been unsuccessful in finding/installing a driver for my wireless card. 

I typed ```
lspci
``` in the terminal to find my wireless card model, and it is a ```
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```When I open up the System -> Administration -> Hardware Drivers, it says "No propriatary drivers are in use on this system".

If you know of what drivers I need to download/install/activate, or if you need more information to assess my problem, I would really appreciate the help.

EDIT:
A little more info:
```
jesse@Jesse-Laptop:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:90500000-90503fff memory:90000000-900fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:22:41:3a:f7:96
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:90400000-90403fff ioport:5000(size=256) memory:90800000-9081ffff(prefetchable)

```

---

### Post by danking12 on 2009-11-23
You can try these links, some of them seemed to get it to work:

[http://ubuntuforums.org/showthread.php?t=1308533](http://ubuntuforums.org/showthread.php?t=1308533)
[http://ubuntuforums.org/showthread.php?p=8243191#post8243191](http://ubuntuforums.org/showthread.php?p=8243191#post8243191)
[http://ubuntuforums.org/showthread.php?t=1313761](http://ubuntuforums.org/showthread.php?t=1313761)

I know I did it with previous Ubuntu releases on my girlfriends old laptop but it was after a fair bit of work and a lot of searching and I don't exactly remember what I did.

Keep up the work!

---

### Post by renegadespork on 2009-11-23
> **danking12 said:**
> You can try these links, some of them seemed to get it to work:

[http://ubuntuforums.org/showthread.php?t=1308533](http://ubuntuforums.org/showthread.php?t=1308533)
[http://ubuntuforums.org/showthread.php?p=8243191#post8243191](http://ubuntuforums.org/showthread.php?p=8243191#post8243191)
[http://ubuntuforums.org/showthread.php?t=1313761](http://ubuntuforums.org/showthread.php?t=1313761)

I know I did it with previous Ubuntu releases on my girlfriends old laptop but it was after a fair bit of work and a lot of searching and I don't exactly remember what I did.

Keep up the work!

Thanks for the help. I tried each of those processes, and here's what happened:

--------------------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1308533](http://ubuntuforums.org/showthread.php?t=1308533)
In this first thread, I found the solution was:
> **kut77less said:**
> Well it worked!!!!

But I did it a different way. I downloaded 

dpkg-dev (and some dependencies for it) 

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

And then I ran 

```
sudo dpkg-reconfigure bcmwl-kernel-source 			 		
```

And Then 

 			 				```
sudo modprobe -r b43 ssb wl
 sudo modprobe wl 			 		
```

It finally worked. 

Thanks for all your help.

This topic might be helpful, except that I know very little about the terminal, and neither the thread, nor the files explained how to install:
> dpkg-dev (and some dependencies for it) 

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

------------------------------------------------------------
[http://ubuntuforums.org/showthread.p...91#post8243191]("http://ubuntuforums.org/showthread.php?p=8243191#post8243191")
I encountered the same situation here.
> went to: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

after reading: [http://forum.ubuntu-fr.org/viewtopic.php?id=237533](http://forum.ubuntu-fr.org/viewtopic.php?id=237533)

and installed those drivers.
I have NO IDEA how to install those drivers, or even where to put them so terminal can find them.

---------------------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1313761](http://ubuntuforums.org/showthread.php?t=1313761)
This last link ends up redirecting me to the second one.

---------------------------------------------------------------

I think I should have specified that I will probably need to be walked through step by step on how to install/activate these drivers because my knowledge on how the terminal works is incredibly limited and simply based on observation.

---

### Post by danking12 on 2009-11-24
Okay, I would suggest doing some reading up on the terminal. It is in essence the same thing as the Windows command-line. Knowing some basics will help a lot when forum posts aren't fully step by step.

Here is a good places to start:
[http://www.ibm.com/developerworks/linux/library/l-sek51-basics/?ca=dgr-lnxw15NewLinux#h3]("http://www.ibm.com/developerworks/linux/library/l-sek51-basics/?ca=dgr-lnxw15NewLinux#h3")

I am sure you can find many more help resources online.

Alright, now for the wireless card. I'll try and step this out the best I can and I apoligize if I make it too simplistic. When coming with commands you don't recognize you can type:
```
man <insert command here>
```
into the terminal without the pointy brackets and it will display a help file on the command. You can exit from this help by pressing "q" and scrolling down by pressing the space bar.

What you can do is any output that is written by the commands run at the terminal just copy and paste them into a reply to this message.

Step 1: Open a terminal
Applications->Accessories->Terminal

Step 2: Run dpkg-reconfigure, the first link claims he installed it but this package should already be installed. You can do this by typing into the terminal the following code:
```
sudo dpkg-reconfigure bcmvl-kernel-source
```
"sudo" makes you a super user that has higher priviledges to modify files outside of your home directory, install packages and so on. dpkg-reconfigure should hopefully reconfigure the module for your wireless card.

Step 3: Run modproble, this will add and remove the required modules that will *hopefully* get your wireless card up and running, now type these two commands into the command line:
```
sudo modprobe -r b43 ssb vl
sudo modprobe vl
```

Now, you may want to give it a restart and see what happens. Let me know of any questions or other issues. We'll see if this works and then we can go onto the next link I sent you if it doesn't.

---

### Post by danking12 on 2009-11-24
I'm not sure how much of a beginner you are but here is a forum post with links to a guide a friend recommended:

[http://ubuntuforums.org/showthread.php?t=1052065]("http://ubuntuforums.org/showthread.php?t=1052065")

---

### Post by 3rdalbum on 2009-11-24
Note: I've never tried installing Broadcom drivers, so take my suggestion with a grain of salt.

The Hardware Drivers program should offer the "bcmfirmwarecutter" which will get a Broadcom wireless device to work. However it will not know about this package unless you update the package list. This is easy - plug your computer directly into your modem/router with an Ethernet cable so you have an internet connection. Go to System > Software Sources and make sure that you have the four repositories enabled in the first tab.

Close the program. If you made any changes, it will ask if you want to reload the package list; hit Reload, and then after that's finished go to Hardware Drivers and the bcmfirmwarecutter should be offered to you. If you weren't asked if you want to reload the package list, then go to System > Administration > Synaptic Package Manager and hit the Reload button. When that's done, quit out of the program and try Hardware Drivers.

I don't know for sure if this is all that's required to get your particular Broadcom chipset to work on Ubuntu, but I have heard that this works with at least some chipsets.

---

### Post by stoogiebuncho on 2009-11-24
> **3rdalbum said:**
> Note: I've never tried installing Broadcom drivers, so take my suggestion with a grain of salt.

The Hardware Drivers program should offer the "bcmfirmwarecutter" which will get a Broadcom wireless device to work. However it will not know about this package unless you update the package list. This is easy - plug your computer directly into your modem/router with an Ethernet cable so you have an internet connection. Go to System > Software Sources and make sure that you have the four repositories enabled in the first tab.

Close the program. If you made any changes, it will ask if you want to reload the package list; hit Reload, and then after that's finished go to Hardware Drivers and the bcmfirmwarecutter should be offered to you. If you weren't asked if you want to reload the package list, then go to System > Administration > Synaptic Package Manager and hit the Reload button. When that's done, quit out of the program and try Hardware Drivers.

I don't know for sure if this is all that's required to get your particular Broadcom chipset to work on Ubuntu, but I have heard that this works with at least some chipsets.

+1 

Once I had to actually restart the computer before Hardware Drivers found the driver for my wireless card.  I have no idea why.  However, once it found it all I had to do was enable it and everything worked

---

### Post by Sealbhach on 2009-11-24
> **3rdalbum said:**
> Note: I've never tried installing Broadcom drivers, so take my suggestion with a grain of salt.

The Hardware Drivers program should offer the "bcmfirmwarecutter" which will get a Broadcom wireless device to work. However it will not know about this package unless you update the package list. This is easy - plug your computer directly into your modem/router with an Ethernet cable so you have an internet connection. Go to System > Software Sources and make sure that you have the four repositories enabled in the first tab.

Close the program. If you made any changes, it will ask if you want to reload the package list; hit Reload, and then after that's finished go to Hardware Drivers and the bcmfirmwarecutter should be offered to you. If you weren't asked if you want to reload the package list, then go to System > Administration > Synaptic Package Manager and hit the Reload button. When that's done, quit out of the program and try Hardware Drivers.

I don't know for sure if this is all that's required to get your particular Broadcom chipset to work on Ubuntu, but I have heard that this works with at least some chipsets.

+2

Do this and enable the Broadcom STA Wireless Driver. That should fix it.

.

---

### Post by renegadespork on 2009-11-25
> **3rdalbum said:**
> Note: I've never tried installing Broadcom drivers, so take my suggestion with a grain of salt.

The Hardware Drivers program should offer the "bcmfirmwarecutter" which will get a Broadcom wireless device to work. However it will not know about this package unless you update the package list. This is easy - plug your computer directly into your modem/router with an Ethernet cable so you have an internet connection. Go to System > Software Sources and make sure that you have the four repositories enabled in the first tab.

Close the program. If you made any changes, it will ask if you want to reload the package list; hit Reload, and then after that's finished go to Hardware Drivers and the bcmfirmwarecutter should be offered to you. If you weren't asked if you want to reload the package list, then go to System > Administration > Synaptic Package Manager and hit the Reload button. When that's done, quit out of the program and try Hardware Drivers.

I don't know for sure if this is all that's required to get your particular Broadcom chipset to work on Ubuntu, but I have heard that this works with at least some chipsets.

+3

I also had to restart my computer to get Hardware Drivers to search for my drivers again, but it worked perfectly. I am currently posting this from Ubuntu 9.10 using my wireless network. Thank you so much. I'll mark this thread solved.

---

### Post by crazychristian on 2009-11-25
> **renegadespork said:**
> +3

I also had to restart my computer to get Hardware Drivers to search for my drivers again, but it worked perfectly. I am currently posting this from Ubuntu 9.10 using my wireless network. Thank you so much. I'll mark this thread solved.

This worked for me as well (I also had to restart). Thanks :)

---

