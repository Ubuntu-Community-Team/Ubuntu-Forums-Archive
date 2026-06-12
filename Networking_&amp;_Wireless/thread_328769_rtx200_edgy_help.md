---
title: "rtx200 edgy help"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2006-12-31
I am trying to install the driver for rt73 chipset using the rtx200 package. The first command to issue is 'make' but as soon as I give it I get this error.

#error Debugfs support has been disabled in your kernel

I have looked on the internet to find an answer but apparently nobody else has the problem.

How do I enable debugfs?

---

### Post by Bouncelot on 2007-01-02
I am getting this too. no luck yet, but still looking for a solution.

---

### Post by peterthewolf on 2007-01-04
bouncelot

got this answer on serialmonkey forum

You should edit the 'config' file in the rt2x00 folder and change
CONFIG_RT2X00_DEBUGFS=y
to
CONFIG_RT2X00_DEBUGFS=n
_________________
Regards,
Ivo van Doorn
Project Administrator

---

### Post by BeachBum on 2007-03-15
Was anyone able to get this driver working?

---

### Post by Bouncelot on 2007-03-15
I got it building, but was having problems with it connecting. I eventually gave up. I plan to take a look at it again in a few weeks.

---

### Post by Austin_KW on 2007-03-15
> **BeachBum said:**
> Was anyone able to get this driver working?

I downloaded the daily tar directly from serialmonkey & this works

Remove & blacklist old driver
[INDENT]sudo modprobe -r rt73usb
sudo echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist
[/INDENT]
Get the New Driver
[INDENT]wget [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) 
tar -xvf rt73*.gz[/INDENT]
Get Kernel headers and build the new driver
[INDENT]
sudo apt-get install linux-headers-$(uname -r)
cd rt73-*/Module
make[/INDENT]
Install the new driver
[INDENT]sudo make install
sudo modprobe rt73[/INDENT]

---

### Post by BeachBum on 2007-03-15
The legacy drivers work just fine, I'm having trouble getting the rt2x00 beta drivers working.   Like Bouncelot, installing is fine but connecting is not working.

---

### Post by yigal.weinstein on 2007-03-17
I am having the same issue.  2.6.20-11-generic is the latest Feisty kernel it uses rt73usb by default.  So it is already installed but I can't make a connection to the network.

---

### Post by peterthewolf on 2007-03-18
yigal see this post
[http://www.ubuntuforums.org/showthread.php?t=375848](http://www.ubuntuforums.org/showthread.php?t=375848)

---

### Post by yigal.weinstein on 2007-03-18
peter, I am not sure if you are aware that rt73 is not rt73usb.

I actually found out about the need to blacklist on my own.  rt2570 was hard crashing my Feisty system, I dmesg | less and found rt{2570,73} were both loading.  I knew rt73 worked so I blacklisted rt2570 and so I have been happy ever since.  However NetworkManager works with rt73usb but not with rt73.  But NetworkManager only knows about wlan0 device it doesn't actually know how to use rt73usb.  The idea is to get my wireless to work with NetworkManager but this is really not a big issue as I already have WPA working with rt73.

It just so happens that 2.6.20-11-generic uses rt73usb and not rt73 for my wifi.  So I had to blacklist rt73usb and use rt73.  No big deal but the fact that NetworkManager detected the wifi device made me excited so that I wanted to see if I could make a working connection with NM and rt73usb but alas no one seams to be able to.

---

