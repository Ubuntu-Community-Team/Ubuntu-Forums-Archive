---
title: "Can't recognize Netgear MA111 wireless USB adapter"
date: 2004-10-31
forum: Networking &amp; Wireless
---

### Post by cwaldbieser on 2004-10-31
I had previously set up Mandrake 9.2 for my Mom to try, but she had some difficulties using it, so I thought I would try installing Ubuntu (Warty Warthog) for her (it seemed a little more user-friendly to Linux novices).  However, her PC connects to our home network via a Netgear MA111 wireless USB adapter.  To get this working with Mandrake, I had to download and install a software called "prism2_usb" and "wlanctl-ng", and after fooling around with editing my /etc/rc.d/rc.local file, I was eventually able to get it to work.  The prism2_usb module already seems to be loaded (I see it when I do an lsmod), but I did not see wlanctl-ng in the package manager.

I am a bit new to where everything is located in Ubuntu.  I tried using the networking wizard from Computer->System Configuration->Networking, but the drop-down for networking devices didn't have anything in it.  I tried manually entering "wlan0", but the connection just refused to activate without really giving me any kind of reason why.

I do have another PC with Ubuntu that is connected directly to our router via an ethernet cable, and it seems to be working fine.  Anybody have any ideas what I should try next?

Thanks,
Carl Waldbieser

---

### Post by cwaldbieser on 2004-11-05
Well, I think I finally found a solution!  I had to download the linux-wlanctl-ng.deb package from another computer and then sneaker-net it to the PC with the wireless adapter.  I installed the package (using dpkg -i), and then issued the following commands which I got off the wlanctl-ng website:

$ sudo modprobe prism2_usb prism2_doreset=1
$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
$ sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=<my SSID> authtype=opensystem
$ sudo ifconfig wlan0 <IP addr>

Of course, I substituted the SSID my router was using and the IP address I wanted the machine to use.  After that, I was able to use the GUI (Computer->System Configuration->Networking) to set up the other stuff (like the default route, etc), though I could have done this from the command line, I guess.

From the reading I had done, I had thought that iwconfig and the related wireless-extension tools were supposed to replace linux-wlanctl-ng (which is not in the supported Ubuntu repositories as far as I can tell).  However, it seems that at least in my case, they are not a good substitute.

One question I still have is where can I set this up so that these commands are issued automatically when the PC boots up?  It could become really annoying for my mom to have to run a shell script every time she wants to use the Internet.  I know on Mandrake, I could set it up in /etc/rc.d/rc.local, but I am not familiar with this sort of initialization would go on Ubuntu (or any Debian-based distro).

Hope this helps others who might have had similar problems.  I also hope that this becomes easier to configure by the time Hoary Hedgehog rolls around.  :)

Carl Waldbieser

---

### Post by Kinimod on 2004-11-07
[QUOTE=cwaldbieser]

$ sudo modprobe prism2_usb prism2_doreset=1
$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
$ sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=<my SSID> authtype=opensystem
$ sudo ifconfig wlan0 <IP addr>[/QUOTE]

I typed this in and my MA111 seems to work. I can ping my Router (192.168.0.1) and such things. But I can't "go" to the internet. There seems to be no connection. What should I configure to get the internet working? 

Something with DNS or what? 

Sorry, I'm new to Linux and I cannot speak English (I'm from Switzerland).

Greetings
Dominik

---

### Post by cwaldbieser on 2004-11-15
Can you ping outside sites (like [www.google.com](www.google.com))?  If so, your problem is not with DNS.  Try pinging an outside site from a computer with a direct connection to the Internet (via ethernet, for example).  Copy down the IP address and try pinging it from your wireless computer.  If you can reach it, your problem probably is DNS.

If you can *only* seem to be able to ping your router, a couple of things come to mind.  It could be that you have no default route set up.  Try typing "route" at the terminal prompt and see if it has an entry for a default route that matches your router IP address.

It could also be that you need to configure the settings on your router.  How to do that is likely dependent on what type of router you have.

Carl

---

### Post by Kinimod on 2004-11-20
I've solved the problem for me. I had to typ in "dhclient", thats all :)

---

### Post by DiCiCat on 2004-12-03
Hello, (and sorry for my bad English  :-#  )

The best way i found to use a Prism2_usb wireless card is to not use the Linux-wlan-ng.deb pakage. This pakage include the files needed to control usb card, (modules prism2_usb and P80211 are already compiled in Ubuntu kernel image) but scripts had been modified by Debian team and badly support usb (i don't know if pci and pcmcia support are better, but read the readme file which is installed whith the pakage to know how to configure.)

If you use the linux-wlan-ng.deb pakage, you can make Usb prism2 card fonction with the wlanctl commands and so create a script from your own to initialize it. But if you choose this way, i don't know how to link Hotplug and the script you have to create, to automatically start the script at boot up or whan you plug the card in.

So the best way, is to download the sources of the linuw-wlan-ng on the website of the linux-wlan project and to compile it. I try the 0.2.1pre23 sources, but it refuse to compile properly with the Warty kernel sources, so i try with the pre21 driver and it is ok. With this pakage, you just have to modified the /etc/wlan/wlan.conf and the /etc/wlan/wlancfg-* files as explain in the linux-wlan-ng-0.2.1pre21 readme.
For me, it works perfectly at boot time, with hotplug, without any other else manipulation.

I hop you understand my explanations in an aproximative English :)

---

