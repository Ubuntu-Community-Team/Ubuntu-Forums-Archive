---
title: "Belkin Wireless N USB on Ubunto"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by krafcik on 2009-01-24
Help - just installed UBUNTU and I'm trying to get my wireless up. I'm trying to follow the directions below - but i don't know where to enter any of the stuff into? Also, it seems like the USB ports are not even active - how do you get those up an running?

Using Belkin N Wireless USB Adapter with Ubuntu

I picked up a wireless N router and adapter a while ago–both from Belkin–and decided to get them working with Ubuntu.  This is how I got it to work.
Get the driver

Step number one is to download the driver from Belkin’s website.
Extract the driver files

The download from Belkin results in an executable from which the necessary driver files cannot be extracted using cabextract. To get at them, you need to actually run the install program using wine, so install wine first.
$ sudo apt-get install wine

Now you need to go to the directory where you downloaded the drivers and run it.
$ wine f5d8053v3_ww_02.0.0.04_w2.exe

Afterwards, the relevant files will be found inside your .wine directory, but I’ll get back to that later. First you need to install something that will let you use a Windows driver.
Make your Windows driver speak Linux

You now have a driver designed to control your wireless adapter, but it was also designed to run exclusively on Windows. This calls for ndiswrapper, whose job is to act as translator for the Windows driver and Linux system. As far as Belkin’s driver is concerned, it’s running on a Windows system. Note that you can also use ndisgtk–a graphical version of ndiswrapper–for this purpose.
$ sudo apt-get install ndiswrapper

Now we’ll go into the directory that the setup program created in wine.
$ cd ~/.wine/drive_c/Program\ Files/Belkin/F5D8053/XP2K

Now it’s time to wrap up the driver and load it up.

$ sudo ndiswrapper -i rt2870.inf
$ sudo ndiswrapper -m
$ sudo depmod -a
$ sudo modprobe ndiswrapper

In a few moments, it should show up in the Network Manager applet, where you can now connect to your network using you Belkin N Wireless USB Adapter.

Note: Network Manager will probably not show the correct speed you’re connected at, but transfer a file over the network with your new adapter and you’ll see that it’s definitely going at N-wireless speeds.

---

### Post by David R. Ingham on 2009-02-03
I found this post and followed it except that the ndiswrapper link didn't work, so I got it from another post's links, that I set my directory to the CD instead of downloading the driver and it said "command depricated" for the -m line.
No new item in the network widget on the top bar.  A "Belkin Wireless Network Utility" icon appeared on my desktop, and it runs if I double click it, but it shows no connections either.
One other thin:  I have a D-link 802.11g DSL/router, not a Belkin n.
I tried re-booting the router and re-booting the PC.
What did I do wrong?

---

### Post by David R. Ingham on 2009-02-11
More detail.
I have messages:  ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
and
couldn't load driver rt2870;
This is an F5D8055 v1.  This time the driver is the 8055 driver from the Belkin web site, instead of from the CD.
It looks like ndiswrapper does not supply a service that the driver needs?
Is there a newer ndiswrapper?

---

