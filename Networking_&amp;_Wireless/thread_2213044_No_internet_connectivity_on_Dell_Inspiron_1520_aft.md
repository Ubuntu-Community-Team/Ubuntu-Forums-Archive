---
title: "No internet connectivity on Dell Inspiron 1520 after installing Ubuntu 12.04"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by DaveP2629 on 2014-03-24
I ran Ubuntu 12.04 from a DVD ISO today and had ethernet connection but no wireless. Thanks to various postings on here I learned how to tackle the wireless issue involving Broadcom BCM4311 chipset so I decided to install Ubuntu alongside the existing Vista OS. Having done that I was somewhat taken aback to find that Ubuntu now failed to make a wired connection, where it had perfectly happily when running off the DVD! As I cannot now connect to the internet at all I can't do the wireless driver fix either, so I appear to be totally stuck. As it was working fine when I did the trial off the DVD ISO I assume that there is no hardware issue and there must a a driver there that worked too. This is my first attempt to use Ubuntu and I'm not a techie, so I'd be eternally grateful to anyone who can help me work out what I need to do to get the ethernet connection working again. Many thanks, in anticipation.

---

### Post by chili555 on 2014-03-24
Please hook up the ethernet. Yeah, yeah, I know, you say it's not working. Please open a terminal Ctrl+Alt+t and do:```
sudo modprobe b44
```At this point, your ethernet will spring to life. Next do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer 
```

Detach the ethernet, reboot and let us hear the result.

Why do I get all the easy ones??

---

### Post by DaveP2629 on 2014-03-25
Hi chili555, thanks for replying.

I did the sudo modprobe b44 and hit enter and it responded by asking for a password. I entered my login password but nothing seemed to happen and the ethernet certainly didn't spring to life. I tried entering all the rest but nothing happened so I killed the terminal with everything still as it was. :(

Dave

---

### Post by chili555 on 2014-03-25
Let's dig a bit deeper. Please run,write down and post fromdome other computer, the results of this command:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.

---

### Post by DaveP2629 on 2014-03-25
OK - this is what I've got after running your command:

03:00.0 Ethernet controller [[COLOR=#ff0000]0200[/COLOR]]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network Controller [[COLOR=#ff0000]0280[/COLOR]]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Many thanks for your help with this. I'm totally in the dark and could just as well be communicating with my Dell in Chinese!

---

### Post by chili555 on 2014-03-25
I hear you, Dave, even in Chinese! Once we get you on line and you get a bit more keyboard time, it will clear up.

The driver b44 is correct for your ethernet. We need the ethernet to download the required firmware. Is the driver loading automatically?```
lsmod | grep b4
```If you see b44 and, hopefully b43 (the driver for your wireless), hook up the ethernet again and see if you can connect. If so, grab the firmware fast!!```
sudo apt-get install firmware-b43-installer
```If not, look for clues in the message log:```
dmesg | grep -e b44 -e eth0
```Thanks.

---

### Post by DaveP2629 on 2014-03-25
Hmmmm. Well, no b44 nor b43, in fact, nothing returned at all. Tried your dmesg command and got back: No such file or directory

---

### Post by DaveP2629 on 2014-03-25
Sorry, I missed a -e out of the dmesg last time! Tried again and this time nothing at all back.

---

### Post by chili555 on 2014-03-25
Interesting. Please try:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf  <--if it isn't present, please just continue
```Reboot and connect to the ethernet and then try again:```
lsmod | grep b4
dmesg | grep -e b44 -e eth0
```Thanks.

---

### Post by DaveP2629 on 2014-03-25
After the first command I got a whole load of stuff back including, at the end: The following package was automatically installed and is no longer required: dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bcmwl-kernel-source*
0 to upgrade, 0 to newly install, 1 to remove and 40 not to upgrade.
After this operation, 3,668 kB disc space will be freed.
Do you want to continue [Y/n]?

I didn't want to go any further without checking with you first!

---

### Post by chili555 on 2014-03-25
> **DaveP2629 said:**
> After the first command I got a whole load of stuff back including, at the end: The following package was automatically installed and is no longer required: dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bcmwl-kernel-source*
0 to upgrade, 0 to newly install, 1 to remove and 40 not to upgrade.
After this operation, 3,668 kB disc space will be freed.
Do you want to continue [Y/n]?

I didn't want to go any further without checking with you first!Press Y and proceed.

---

### Post by DaveP2629 on 2014-03-25
OK. All done and I've got an ethernet connection!!! Those last two commands have returned quite a few lines of data. Do you want me to type any of it into here for you?

---

### Post by DaveP2629 on 2014-03-25
As I have a wired connection I've carried on with the command: [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install firmware-b43-installer
[/FONT][/COLOR]Many many lines of "stuff" has come back, finishing with loads of lines with: Extracting b43/.............. and ending in .fw
I'm hoping that means I've downloaded and installed the wireless firmware that I need. Fingers crossed!!!

---

### Post by chili555 on 2014-03-25
No. I suggest you detach the ethernet, reboot and reply to tell us how much you are enjoying your new wireless. Then I'll tell you why it went wrong in the first place.

---

### Post by DaveP2629 on 2014-03-25
Yeayyyy!!!! :p Wireless is there too now and I'm definitely enjoying it! As, no doubt, you knew all of the time! Many, many, thanks for your help here. Go on then, please tell me why I had no ethernet nor wireless connectivity.

---

### Post by chili555 on 2014-03-25
Awesome. Glad it's working.

There is a mechanism in the system that activates during install that offers to install Additional Drivers, including for your Broadcom wireless. Incredibly, it blacklists the driver b44 for your ethernet. The driver it installs for your wireless is wrong, as you saw, and you are left with no connectivity at all! Then I have to get to work and unravel the mess!

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by DaveP2629 on 2014-03-25
Really?!! Is this just a 12.04 issue? I thought 12.04 was a long term support release so would be pretty bug free. These sound like fundamental errors to me and not part of a mature and robust operating system. They effectively cripple your PC after the install. If the issue is well known why haven't Canonical issued fixes by now, or am I not yet up to speed with the way things work in the Ubuntu world?

---

### Post by chili555 on 2014-03-25
It is being worked on. There is a lot of confusion not only with Ubuntu, but Suse, Fedora, Arch, et al. In my humble opinion, even Broadcom (!!!) puts out incorrect information. It is difficult for me and a few brave pioneers to swim upstream.

Here is what your device is:> Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)...and here is what Broadcom themselves say: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)> SUPPORTED DEVICES
-----------------
The cards with the following PCI Device IDs are supported with this driver.
Both Broadcom and and Dell product names are described.   Cards not listed
here may also work.

	   BRCM		    PCI		  PCI		  Dell
	  Product Name	  Vendor ID	Device ID	Product ID
          -------------	 ----------	---------   	-----------
          4311 2.4 Ghz	    0x[COLOR="#FF0000"]14e4[/COLOR]	0x[COLOR="#FF0000"]4311[/COLOR]  	Dell 1390
<snip>You know very well, because you just had the experience, that this is not true. You know that the correct driver is actually the native b43 and proprietary firmware.

---

### Post by DaveP2629 on 2014-03-25
Wow - I can see that there's a problem when the original manufacturer even gets it wrong! Thankfully there're stars like you out there to rescue us technically challenged types! Once again - very many thanks for your invaluable help.

---

