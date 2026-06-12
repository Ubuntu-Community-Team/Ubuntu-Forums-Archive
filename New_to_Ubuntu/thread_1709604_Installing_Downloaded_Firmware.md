---
title: "Installing Downloaded Firmware"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by sev1 on 2011-03-18
I'm trying to get my TP Link TL-WN821N USB dongle with Atheros ar9170 chipset working. After doing some research, the carl9170 driver gives this device max potential, so I've downloaded the ar9170 firmware before downloading the driver.

My question is: now that the firmware package is in downloads, how do I install it, or where should I move it so that it is detected/installed? I tried dragging to lib/firmware but this didn't take. I'm a new Ubuntu convert & pretty bad with Terminal.

Cheers

---

### Post by tkelito on 2011-03-18
What type of package did you download?  I am assuming tar.gz?

---

### Post by Hippytaff on 2011-03-18
Hi and welcome to the forums

I know you don't like the terminal but can you remove the usb and put it back in. Then open one (a terminal) and post the results of ```
dmesg | tail
``` and ```
lsusb
``` with the usb plugged in?

Some times usb efforts are not decteded as wireless devices but mass storage devices because the firmware is in the usb device - so just to rule that out.

As for the package you download what files are there - assuming it's a tar.gz - (is it binary or a .deb package, .inf and .sys files etc) is it the linux driver?

---

### Post by sev1 on 2011-03-18
It's not tar.gz - in downloads just shows as: carl9170-1-fw

The .fw presumably meaning firmware

---

### Post by Hippytaff on 2011-03-18
then [this ]("http://linuxwireless.org/en/users/Drivers/carl9170")might help...but the output of those commands would also be useful ;-)

---

### Post by sev1 on 2011-03-18
Hi HT - Thanks.
I pretty sure the correct firmware for Linux distros isn't embedded in the device as it comes with software for MS users. Also, no action when I plug it in. I could cheat an load the Win drivers, but that doesn't really help in learning things Ubuntu. Perhaps I should have opted for an easier beginners task. Here's the screen:

-laptop:~$ dmesg|tail
[ 7911.302889] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[ 7911.323785] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[ 7911.776611] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[ 7911.776649] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[ 7911.776713] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[ 7911.776789] [drm] Loading R200 Microcode
[ 7930.538137] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7940.732032] eth1: no IPv6 routers present
[ 8369.968061] usb 1-5: new high speed USB device using ehci_hcd and address 6
[ 8370.101202] usb 1-5: configuration #1 chosen from 1 choice
-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

& it's not that I don't like terminal per se, I just suck at using it....

Cheers

---

### Post by Hippytaff on 2011-03-18
it certainly recognises it as a wireless device, so my initial thought (that you might have to switch the mode to so ubuntu recognised it as a wireless device is ruled out...the issues of embedded drivers within these devices does cause issues for linux users because (as you say) they are predominantly windows drivers.

That link I posted might help then...have a read and let us know

---

### Post by sev1 on 2011-03-18
> **Hippytaff said:**
> then [this ]("http://linuxwireless.org/en/users/Drivers/carl9170")might help...but the output of those commands would also be useful ;-)

This is site has the link from which I downloaded the FW - it's at: [http://linuxwireless.org/en/users/Drivers/carl9170#Firmware-1](http://linuxwireless.org/en/users/Drivers/carl9170#Firmware-1)

:P

---

### Post by Hippytaff on 2011-03-18
it certainly recognises it as a wireless device, so my initial thought (that you might have to switch the mode to so ubuntu recognised it as a wireless device is ruled out...the issues of embedded drivers within these devices does cause issues for linux users because (as you say) they are predominantly windows drivers.

Are there any readme's with the download - and have you read the FAQ's?

---

### Post by Razorback on 2011-03-18
Not sure if this will help.

[http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working.html](http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working.html)

[http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb)

---

### Post by Hippytaff on 2011-03-18
As well as Razorback's suggestion...this looks like it would do the job also

[http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html](http://www.linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html)

---

### Post by wep940 on 2011-03-18
I'm not sure about needing to install the firmware in Linux, however I did find something with step-by-step for installing the driver and getting the adapter to work in ubuntu (albeit 10.04, but might work for all):
 
[http://www.ubuntugeek.com/gui-program-to-install-ath9k_htc-atheros-linux-driver.html](http://www.ubuntugeek.com/gui-program-to-install-ath9k_htc-atheros-linux-driver.html)
 
Near the top it has a link to chipsets supported - I've already looked and yours is supported according to the USB manufacturer id and product id: 0cf3:7015

---

### Post by Hippytaff on 2011-03-18
> **wep940 said:**
> I'm not sure about needing to install the firmware in Linux, however I did find something with step-by-step for installing the driver and getting the adapter to work in ubuntu (albeit 10.04, but might work for all):
 
[http://www.ubuntugeek.com/gui-program-to-install-ath9k_htc-atheros-linux-driver.html](http://www.ubuntugeek.com/gui-program-to-install-ath9k_htc-atheros-linux-driver.html)
 
Near the top it has a link to chipsets supported - I've already looked and yours is supported according to the USB manufacturer id and product id: 0cf3:7015

I was hoping you'd turn up ;-)

---

### Post by wep940 on 2011-03-18
> **Hippytaff said:**
> I was hoping you'd turn up ;-)
 
How's it been going? Seems like you're doing a great job on the forum! ;)
 
EDIT:  BTW, I'm going to try Linux-XP to see how it my work for my elderly parents.  It seems like it might look like Windows XP to them, which would be good.

---

### Post by sev1 on 2011-03-21
> **Razorback said:**
> Not sure if this will help.

[http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working.html](http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working.html)

[http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb)
Thx, that was helpful. I didn't think to check the BackTrack Forums.

---

### Post by sev1 on 2011-03-21
The particular TP-Link USB dongle has a lot of different versions and makes. Mine is TP-Link - TL-WN821N v2 

After researching it, I found that I need the ar9170 firmware and drivers (as opposed to ar9171). I finally - in my slow Linux newbie sort of meandering way - got all the firmware in the right place. Now I need to install [compat-wireless-2.6.32.3.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.3.tar.bz2")

I have it downloads, but the following commands haven't worked for me thus far: 
Thx to all for help on this!

tar -xf /root/compat-wireless-2.6.32.3.tar.bz2
cd compat-wireless-2.6.32.3
make
make install
make unload

---

### Post by sev1 on 2011-03-21
> **sev1 said:**
> The particular TP-Link USB dongle has a lot of different versions and makes. Mine is TP-Link - TL-WN821N v2 

After researching it, I found that I need the ar9170 firmware and drivers (as opposed to ar9171). I finally - in my slow Linux newbie sort of meandering way - got all the firmware in the right place. Now I need to install [compat-wireless-2.6.32.3.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.3.tar.bz2")

I have it downloads, but the following commands haven't worked for me thus far: 
Thx to all for help on this!

tar -xf /root/compat-wireless-2.6.32.3.tar.bz2
cd compat-wireless-2.6.32.3
make
make install
make unload


DUH -------> I must have been dropped on my head recently....
sudo tar jxvf file.tar.bz2

---

