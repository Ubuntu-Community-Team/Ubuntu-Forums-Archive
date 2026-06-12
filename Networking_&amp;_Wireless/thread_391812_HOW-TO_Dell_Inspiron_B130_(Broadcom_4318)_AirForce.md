---
title: "HOW-TO: Dell Inspiron B130 (Broadcom 4318) AirForce2 setup"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by MalcolmCarmen on 2007-03-23
EDIT: As of May 11, 2008, it appears that the thread I am linking to below (Step 2) also lists native drivers. I was using ndiswrapper when I wrote this. Still, it may be useful, but it may change the way you need to use my instructions -- I'm not sure.
____________________________

I am posting this for search engine archiving, and to sort of put all my steps in one place. This is more of a compilation of other guide(s). I've had to go through this process for a Dell B130 and B120 laptop (only difference is LCD size) using Edgy Eft with the following wireless chipset:

Obtained with: **lspci | grep Broadcom**

```

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I will simply give a general overview of the steps I've taken. It is assumed that you have a fresh ubuntu install, or one relatively unconfigured.

1. "**sudo gedit /etc/apt/sources.list**" -- Uncomment all deb-src lines possible (and anything else you might see commented out that you can uncomment). The idea is to enable multiverse/universe packages. Let me know if I'm not quite correct here, since I'm not too familiar with the packaging system in detail.

2. Read and follow [http://www.ubuntuforums.org/showthread.php?p=1140976](http://www.ubuntuforums.org/showthread.php?p=1140976) -- this will get your wireless card working, but you won't be able to connect to a network yet

3. You will want to install a network manager. The easiest to go with appears to be gnome-network-manager. Follow the following guide to do so: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

NOTE: in step #3, when it says to comment out a lot of lines, it means it. If you don't do it correctly, network-manager will simply refuse to work and will report "No connection". I modified my own /etc/network/interfaces so that it contained only the following (I actually deleted instead of commented out my other lines):
```

auto lo
iface lo inet loopback

```

This will eliminate any configuration for any ethernet device you have, so you may need to re-configure it. To tell the truth, I've not used my ethernet interface again after this process, so I can't say if using System > Administration > Networking will cause network-manager to stop working again. It likely won't, as long as you don't modify your wireless connection's settings.

4. Reboot if you've not done so yet. Hopefully, you'll see the network-manager applet icon in the upper right hand corner. If when you mouse over it, it says "No connection", you may not have properly modified your /etc/network/interfaces -- otherwise, you should now be able to select a wireless network in your area and configure things from there.

I am by no means the expert, so I expect some instructions to be redundant here. Let me know of anything like that, and I'll edit!

One other thing, I've done this on both of the laptops after Step #2, but I don't know if it is even required:
1 - Use "**lspci**" -- this will list out a lot of devices. You should see your wireless card towards the end. Or, to pull it out quicker. use "**lspci | grep Broadcom**"
2 - Now, you need a magical device ID for your wireless card. The line for my wireless card from "lspci" looks like this:
**02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
the "02:03.0" is the important part. Remember it, and go to the next step:
3 - "**lspci -n**" -- Look at the values in the left-hand column. Find the xx:xx.x number that you just remembered. In the right-hand column is the device ID:
**02:03.0 0280: *14e4:4318* (rev 02)**
4 - Use "**ndiswrapper -l**" -- this SHOULD list out your single driver from the setup you made in Step #2. If not, go make sure you've followed the guide correctly. You will use "**ndiswrapper -d <devid> bcmwl5**" (bcmwl5 is the name of the driver installed in step #2) -- you will replace <devid> with the value that you found in part 3 here.

Now, all those steps may have been wholly redundant since "ndiswrapper -l" reports 
"driver installed, hardware present " to begin with, but I figured I'd include it anyway.

---

