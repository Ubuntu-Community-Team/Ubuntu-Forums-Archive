---
title: "how to get a TP-Link TL-WN727N wireless USB adapter to work"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by ryan4321 on 2010-09-02
Hey guys. I'm pretty new to this Ubuntu thing, but i bought a TL-WN727N wireless USB adapter for my desktop and I can't get it to work. I looked for a driver to get it to pick up wifi, but I can't find one. Thanks in advance.

---

### Post by nickbooker on 2010-09-02
Hi there.

That card needs an updated driver for its internal chipset, available from Ubuntu's repositories, for which you'll need to connect to your router via a wired network temporarily.

Unplug the wireless card from your machine, and connect your machine to your router with a wired network cable.

Wait a few seconds, and check you can browse to a website (e.g. [www.ubuntu.com](www.ubuntu.com)), to ensure you have a connection to the Internet.

To install the updated driver, click Applications -> Accessories -> Terminal, and type the following commands at the $ prompt, pressing Enter after each one and supplying your password if prompted:

```
sudo apt-get update

sudo apt-get install linux-backports-modules-wireless-generic
```

Note when entering passwords the characters you type are not echoed back to screen, even as asterisks - this is normal Linux command-line behaviour.

When finished on the command line, type the following to close the terminal:
```
exit
```

Unplug your ethernet cable.

Close all your windows and restart the computer.  This will make sure the older version of the driver gets unloaded from memory, so the new version can be loaded in its place.

When logged back in, insert your wireless stick.

Wait about 30 seconds.

Left-click the Network Manager icon on the panel at the top of the screen (it will be near the left-side of the clock) and you should see a list of available network names to connect to.

Click the one corresponding to your access point and you'll be prompted for any keys required to connect your network.

If you can't see any access points, right-click the network manager icon and make sure the option Enable Wireless is both present and ticked.

A message will appear briefly in the top-right hand corner of your screen when the connection is established.

Try browsing to a different website to check you have a working route out onto the Internet, and you should be all set.

In future, you should just be able to plug in the device, and if it doesn't connect to your access point automatically just left-click the network manager icon and pick the access point from the list.

Hope this helps,

Nick

---

### Post by ryan4321 on 2010-09-02
Thanks for the quick reply. My computer updated fine, but when i try to run the command "sudo apt-get install linux-backports-modules-wireless-generic", all i get is the response "E: Couldn't find package linux-backports-modules-wireless-generic". I tried it again after restartin also, but got the same result

---

### Post by decaff on 2010-09-17
Same here. same answer 
E: Couldn't find package linux-backports-modules-wireless-generic

I really can't get my head around it, been trying for 2 weeks now with every possible solution.

((I don't even have wired!! my RTL card doesn't work. At least if I could get the wireless working.))

Any help would be greatly appreciated.

---

### Post by anewguy on 2010-09-17
Not sure if this is the one or not, but try:

sudo apt-get install linux-backports-modules-wireless-lucid-generic


See if that helps or not, or if it even does the install.

Dave ;)

---

### Post by decaff on 2010-09-17
Also, I can't download from the same PC as the network adapter is not working.
  So I need the wireless at least.

I browsed in the DVD and there's not Ethtool in it (Ubuntu Studio 10.04)
Look forward to a reply :) thanks people

---

### Post by ryan4321 on 2010-09-28
Wow. Finally... I can't thank nickbooker and anewguy for your help!!

---

### Post by hammockhero on 2011-01-22
Works for me too on Ubuntu 10.04. Thanks to nickbooker and anewguy!

---

### Post by jeanlikethis on 2012-03-05
I have ubuntu 11.10 and installed TP-Link TL-WN727N. 

Follow the instructions from: [https://help.ubuntu.com/community/Wi...ce/Tenda_W311M](https://help.ubuntu.com/community/Wi...ce/Tenda_W311M)

I found Ralink driver 5370 is much stable and reliable than RT2800usb. Please following the steps of downloading and compiling the driver. I have been suffering from the slow and clogging wifi from rt2800 though it is much easier to enable. 

5370 is the one to go.

I also blacklisted rt2870, rt2800 for safe reasons. 5370 works great for me.

Hope this helps.

---

### Post by jeanlikethis on 2012-03-05
~

---

### Post by anymoose on 2012-03-20
HI! This is the definitive fix for Ubuntu 11.10 and TL-WN727N(V3)

Use this link (only) if kernel version is shown below; Ubuntu 11.10

ls /lib/modules

3.0.0-12-generic

Web Link;
[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)

Use user Chili555 post #2. Everything is done in post #2 ie no files to download
no compilation, no other changes. This fix must be entered carefully; all spelling,
spaces and capital/lc letters *must* be correct. Worked for me after reboot. Test
your adapter with MS-Win XP with Included utility on CD ahead of time, if possible.

Not sure if this will work in Ubuntu live filesystem on CD for obvious reasons. Works
when filesystem is on HD disk and USB stick.

Signed; Anymoose

---

### Post by SEECo on 2013-04-16
> **anewguy said:**
> Not sure if this is the one or not, but try:




See if that helps or not, or if it even does the install.

Dave ;)

I ran the command and the package was installed successfully. 

sudo apt-get install linux-backports-modules-wireless-lucid-generic

After it i rebooted the PC and plugged in the Tp-Link and even after waiting for 30 secs it said  Device not Ready(SEE in Picture Given)

---

### Post by bloomafhd on 2013-08-07
> **anewguy said:**
> Not sure if this is the one or not, but try:

sudo apt-get install linux-backports-modules-wireless-lucid-generic


See if that helps or not, or if it even does the install.

Dave ;)

I ran the command and the package was installed successfully. 

sudo apt-get install linux-backports-modules-wireless-lucid-generic

After it i rebooted the PC and plugged in the Tp-Link and even after  waiting for 30 secs it said  Device not Ready(SEE in Picture Given)

---

