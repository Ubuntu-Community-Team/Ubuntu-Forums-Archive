---
title: "have wireless card, but can't connect to home wifi"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by hanzj on 2010-08-16
Hello,

We installed a wireless card into the computer more than a year ago, and I don't remember how to make use of it in ubuntu.

When I hover on the NetworkManager Applet, it says "No Network Connections."  This is not true, because a Windows computer in the same room can pick up quite well the wifi signal.


When I click on the NetworkManager Applet, it does not show any wireless connection available. This should not be so, because the SSID is broadcasted.

When I go to Network Connections and add in a Wireless Connection with the SSID and password, it doesn't seem to help.


Can you please help?

Thanks.

---

### Post by CharlesA on 2010-08-16
Can you post the output of this command please:

```
ifconfig
```

---

### Post by hanzj on 2010-08-16
thanks for the quick reply. I can't find my USB stick to copy and paste the text from one computer to another, but the 2 main groups are

eth0 
and lo

I'm guessing the eth0 is our wired internet card. 
lo is "local loopback".

---

### Post by CharlesA on 2010-08-16
Yup, it looks like the wireless card isn't being detected. Is it a USB or built-in wireless card?

Can you run this please:

```
lspci | grep Network
```
```
lspci | grep Ethernet
```

```
lsusb | grep Network
```
```
lsusb | grep Ethernet
```

It should be listed as "Network controller" or "Ethernet controller"

---

### Post by hanzj on 2010-08-16
it's a built-in card. i'll run the codes soon.

---

### Post by hanzj on 2010-08-16
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by CharlesA on 2010-08-16
Hrm, see if you have anything listed under System > Administration > Hardware Drivers.

Judging from the list of threads here, you need to use ndiswrapper to get it working.

Check here:[http://www.google.com/search?hl=en&client=firefox-a&hs=W4C&rls=org.mozilla%3Aen-US%3Aofficial&q=88w8335+site%3Aubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=en&client=firefox-a&hs=W4C&rls=org.mozilla%3Aen-US%3Aofficial&q=88w8335+site%3Aubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by anewguy on 2010-08-16
If you want to get this working with ndiswrapper, there are a couple of things to do first:

- locate the Windows _XP_ driver files for your adapter - they should be .inf and .sys files

- have the media you used to install Ubuntu handy (either the LiveCD or an install USB flash drive.

Once you have those, just post back and we'll walk you through it real easily.  Pay no attention to posts that say you must compile or "make" ndiswrapper - that's not the case.  Also, you'll hear some say ndiswrapper is crap - that is a falicy as well.  Ndiswrapper is just another of the tools the come with Ubuntu to help you get your PC running Ubuntu.

Dave ;)

---

### Post by hanzj on 2010-08-18
i think I have the cd of the windows xp drivers somewhere, but in case I don't, are they available online?

---

### Post by anewguy on 2010-08-18
You'd have to check the support site for your PC since this is a built-in adapter.

---

### Post by hanzj on 2010-08-18
anewguy,
but the wifi card did not come with the PC. We put it in afterwards.

---

### Post by anewguy on 2010-08-19
EDIT:  Please ignore the following original text I had here > Then what is the make and model of the adapter (from the box it came in)?  Post that back and I'll see if I can get the driver for you.

There should be a driver on a CD that came with the device.  Usually you can find it in a folder on the CD called driver or drivers, but not always.  Some are a self-extracting executable.


That was before I realized something - that sounds like the card I'm using, so you're talking most probably about a Netgear WG311 PCI card.  You'll need to physically look at that card to see what the version number is on the card - mine says WG311v3.  If it's the WG311v3, I can give you the driver and the instructions on how to quickly get it running.

Dave ;)

---

### Post by hanzj on 2010-09-25
I've located a CD-rom for a wireles card, and I think it's the right one.

I've attached 2 folders to this post. One is for "WinX64". The other is "WinXP_2K". How do I go about installing these drivers now?

---

### Post by hanzj on 2010-09-25
All right. I got it working.

I used [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) as my guide.

I just had to get the three debs installed.
For 10.04 Lucid Lynx
[http://packages.ubuntu.com/lucid/misc/ndiswrapper-common](http://packages.ubuntu.com/lucid/misc/ndiswrapper-common)
[http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9](http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/lucid/ndisgtk](http://packages.ubuntu.com/lucid/ndisgtk)


I did NOT have to disable any drivers.

I then did "sudo ndisgtk" and choose the INF in the winxp folder.


Voila!

---

