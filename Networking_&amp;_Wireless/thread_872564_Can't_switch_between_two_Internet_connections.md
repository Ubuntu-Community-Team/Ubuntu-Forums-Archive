---
title: "Can't switch between two Internet connections?"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by rlwpub on 2008-07-28
I have two Internet connections. One on eth0 and one on ppp0.

When I double click on the network icon next to the speaker icon on the upper right of the screen, nothing happens.

Do I need to configure something so I can switch between these two Internet connections?

Re's
Rob

---

### Post by superprash2003 on 2008-07-28
you can use the ifup and ifdown command to enable or disable a connection.. 
ifup eth0 would enable eth0
ifdown ppp0 will disable ppp0

---

### Post by caljohnsmith on 2008-07-28
If you left-click the network icon and hold (not double-click), it should give a pop-up menu where you can chose "manual configuration". After hitting "unlock", you should be able to choose which NIC you want to use.

---

### Post by rlwpub on 2008-07-29
> **caljohnsmith said:**
> If you left-click the network icon and hold (not double-click), it should give a pop-up menu where you can chose "manual configuration". After hitting "unlock", you should be able to choose which NIC you want to use.

I see the ethernet connection but not the kppp connection. When I run kppp it connects to the ISP fine but you just can't seem to access the Internet with it.

Re's
Rob

---

### Post by rlwpub on 2008-07-31
Anyone using two Internet connections at all?

Re's
Rob

---

### Post by rlwpub on 2008-08-26
I'm still having this problem. Anyone have any more things I should try?

---

### Post by Elludium_Q-36 on 2010-03-17
I'm having the opposite problem:
[http://ubuntuforums.org/showthread.php?p=8978185](http://ubuntuforums.org/showthread.php?p=8978185)

Do not discount the advice of: "superprash2003" as this can be edited in files.

What release version are you running?  That affects what your tray applet or taskbar widget does.

What happens when you unplug your ethernet cable?

When you bring up KPPP, click on the "Configure" button and open your account (Edit).  Under the Gateway tab, I have the "Default Gateway" radio button selected and have checked "Assign the default route to this gateway".  That may make a difference for you if it assigns the default route to KPPP, which can also be done by editing files.  Normally your machine would look for a path to the internet over Ethernet, if connected.  In most applications, Ethernet has the best route.  My ethernet only goes to my other box, at present...

I just tried and if I deselect "Assign the default route to this gateway" I can't get online via KPPP.  Select that option and I'm online.

There must be something wrong with my config files because eth0 won't get an IP address from either of my routers.

Try "Assign the default route to this gateway" and see if that gets you online via KPPP while the ethernet is connected.

---

### Post by Elludium_Q-36 on 2010-03-18
I seem to be almost there, as I illustrate in my thread:
[http://ubuntuforums.org/showthread.php?p=8990878#post8990878](http://ubuntuforums.org/showthread.php?p=8990878#post8990878)

I think for most the usual front-end gui is gnome-ppp.
I've had KPPP for a while but I have Kubuntu, presently using 9.04.

Something happened to my knetworkconf package so I tried others.
Seems with package network-config that I'm almost there and maybe combined with package avahi-autoipd I might be able to get things done, even if I have to reassign my the ip addresses of my routers.

I installed package Knetstats which has tray icons for all net-connections, though it's redundant with ppp0 & KPPP.

Were you able to get this done?

---

