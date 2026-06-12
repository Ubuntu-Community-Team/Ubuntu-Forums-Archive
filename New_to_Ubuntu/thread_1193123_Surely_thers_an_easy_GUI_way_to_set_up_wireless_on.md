---
title: "Surely thers an easy GUI way to set up wireless on Jaunty 64bit??"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Doctoxic on 2009-06-21
Hi

I need to set up wireless connection to my router (Netgear DG834N) using WPA2 personal on a Wireless N network.

I am running 64bit Jaunty and have a USB WN121T wireless receiver plugged in.

if i run "iwconfig" i get the following message.
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

I have (at least i think i have) set up a wireless connection in "Network Connections"

I have the following driver files copied from a WinXP installation but not sure if i need them and if i do then what do i do with them.
WN121T.inf
WN121TXP.sys
hmmmmm - just thought - these would be 32 bit drivers wouldn't they and if so does that mean they won't work on my 64 bit system?


Theres quite a lot of posts on wireless related stuff but it all seems very complicated - i can't find a simple guide that shows you how to set up a wireless connection -  with pretty much everyone using wfi shouldn't this be simple goddamit :D

OK, OK i know its probably me missing something but any advice appreciated :)

many thanks

doc

---

### Post by Crunchy the Headcrab on 2009-06-21
Windows drivers won't work on Linux.  I can't tell you much more than that because I'm new to Linux and wireless worked on my system from boot.

I would type:

USB WN121T Ubuntu or USB WN121T Ubuntu 9.04

into Google.  I've found support instructions for a lot of other devices this way.

---

### Post by hyperdude111 on 2009-06-21
Windows drivers will not work with linux.

I have 64bit jaunty and wireless works out of the box. To troubleshoot your problem google the name of your wireless card and ubuntu for info.

---

### Post by ibuclaw on 2009-06-21
Windows drivers may work with Linux using ndiswrapper.

Boot into Ubuntu, insert your Ubuntu CD, and go to **Applications->Add/Remove** and search for
```
ndisgtk
```
in the search bar and you should see "**Windows Wireless Drivers**". Select the checkbox, and select "**Apply Changes**".

The software and all dependencies **should** be on the LiveCD, so you shouldn't run into any problems installing.

After the program has finished installing, go to **System->Administration->Windows Wireless Drivers** and select "**Install New Driver**", then browse to the directory that has **WN121T.inf** and select it.

If all goes well, pressing "**Install**" may get it setup correctly, for you to start using.

Regards
Iain

---

### Post by Doctoxic on 2009-06-21
> **tinivole said:**
> Windows drivers may work with Linux using ndiswrapper.

Boot into Ubuntu, insert your Ubuntu CD, and go to **Applications->Add/Remove** and search for
```
ndisgtk
```
in the search bar and you should see "**Windows Wireless Drivers**". Select the checkbox, and select "**Apply Changes**".

The software and all dependencies **should** be on the LiveCD, so you shouldn't run into any problems installing.

After the program has finished installing, go to **System->Administration->Windows Wireless Drivers** and select "**Install New Driver**", then browse to the directory that has **WN121T.inf** and select it.

If all goes well, pressing "**Install**" may get it setup correctly, for you to start using.

Regards
Iain

Thanks Ian

Tried it but no luck - does it need 64 bit winXP drivers? - They seemed to install ok (though i get a messgae "unable to see if hardware is present"- but after you ok the error message the installed driver says hardware is present.  Also if i click the "configure Network" button i get an error message that says "could not find a network configuration tool"

if i run "iwconfig" i get the following message.
lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions.

any ideas?

thanks

doc

---

### Post by Doctoxic on 2009-06-21
> **hyperdude111 said:**
> Windows drivers will not work with linux.

I have 64bit jaunty and wireless works out of the box. To troubleshoot your problem google the name of your wireless card and ubuntu for info.

thanks hyperdude111

was that with USB or wireless NIC card? - not sure it makes a difference but am curious?

thanks

Doc

---

### Post by Doctoxic on 2009-06-21
> **Crunchy the Headcrab said:**
> Windows drivers won't work on Linux.  I can't tell you much more than that because I'm new to Linux and wireless worked on my system from boot.

I would type:

USB WN121T Ubuntu or USB WN121T Ubuntu 9.04

into Google.  I've found support instructions for a lot of other devices this way.

thanks

will give this a go as well

doc

---

### Post by Doctoxic on 2009-06-21
does this help?

linux64@linux64-desktop:~$ lsusb
**Bus 001 Device 002: ID 0846:7100 NetGear, Inc. WN121T Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 1532:000d Razer USA, Ltd 
Bus 002 Device 002: ID 046a:0021 Cherry GmbH 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ibuclaw on 2009-06-21
> **Doctoxic said:**
> does this help?

linux64@linux64-desktop:~$ lsusb
**Bus 001 Device 002: ID 0846:7100 NetGear, Inc. WN121T Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 1532:000d Razer USA, Ltd 
Bus 002 Device 002: ID 046a:0021 Cherry GmbH 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

What does this output?
```
ndiswrapper -l
```
If you see something along the lines of:
**wn121t : driver installed        device (0846:7100) present**

Then you should be good to do the following:
```
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi
sudo modprobe ndiswrapper

```

And when you run **iwconfig**, you should see a new wireless device.

You may require rebooting before the network applet works with it.

Regards
Iain

---

### Post by Doctoxic on 2009-06-21
linux64@linux64-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wn121t : driver installed
	device (0846:7100) present

now going to try the other bits

doc

---

### Post by Doctoxic on 2009-06-21
other bits gave this:

linux64@linux64-desktop:~$ sudo ndiswrapper -m
[sudo] password for linux64: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

linux64@linux64-desktop:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
linux64@linux64-desktop:~$ sudo ndiswrapper -mi
module configuration information is stored in /etc/modprobe.d/ndiswrapper
linux64@linux64-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
linux64@linux64-desktop:~$ 

what was that doing?

thanks

Doc

---

### Post by Doctoxic on 2009-06-21
linux64@linux64-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



gonna try it again after a reboot

thanks
doc

---

### Post by Doctoxic on 2009-06-21
hmmm

after reboot i still get:

linux64@linux64-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by Doctoxic on 2009-06-21
another thought

where do the .inf and .sys files need to be - i have them both in my home folder - is that ok?

also, from the "windows wireless drivers" window it won't let me "configure network as no tool" - do i need to install something else

or maybe there are permission problmes? but with what?

yours confusedly

doc

---

### Post by cariboo on 2009-06-21
You may be running into a conflict with the driver Linux automatically installs for your device. Make sure ndiswrapper is unloaded:

```
sudo rmmod ndiswrapper
```

then in the same terminal type:

```
sudo lshw -C network
```

and paste the output in your next post.

---

### Post by Doctoxic on 2009-06-21
> **cariboo907 said:**
> You may be running into a conflict with the driver Linux automatically installs for your device. Make sure ndiswrapper is unloaded:

```
sudo rmmod ndiswrapper
```

then in the same terminal type:

```
sudo lshw -C network
```

and paste the output in your next post.

will do - am on a different PC at the moment

but why am i doping this if as you say there are drivers already loaded?  what would i need to do to get it working without the ndiswrapper

thanks again

doc

---

### Post by Doctoxic on 2009-06-21
> **cariboo907 said:**
> You may be running into a conflict with the driver Linux automatically installs for your device. Make sure ndiswrapper is unloaded:

```
sudo rmmod ndiswrapper
```

then in the same terminal type:

```
sudo lshw -C network
```

and paste the output in your next post.

linux64@linux64-desktop:~$ sudo rmmod ndiswrapper
[sudo] password for linux64: 
linux64@linux64-desktop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:fb:a7:d2:43:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
linux64@linux64-desktop:~$

---

### Post by johnward1978 on 2009-08-25
Type: -$ dmesg

...and you will see ndiswrapper error messages complaining about it being a 64 bit kernel and the driver is 32 bit. So we need to find a 64 bit version of the file WN121T.inf

Aside from installing a new kernel that is 32 bit, I am stumped as I can't find a 64 bit version. Moving to 64 bit is just a massive hassel!

Cheers,

John

---

### Post by 3rdalbum on 2009-08-26
> **johnward1978 said:**
> Aside from installing a new kernel that is 32 bit, I am stumped as I can't find a 64 bit version. Moving to 64 bit is just a massive hassel!

No, trying to use a wireless device that doesn't have in-kernel drivers, is a big hassle.

I'd recommend doing some research into wireless devices, and buy a USB wireless card that works out-of-the-box on Ubuntu Jaunty. Saves yourself some pain. The Realtek RTL8187 chipset is easy to find and it finally works properly on Jaunty with a package from the repositories.

If you have a card that's supported out-of-the-box or with a repository package, then you don't need the terminal - you just use the Network Manager applet. Then it's an "easy GUI way to set up wireless".

---

