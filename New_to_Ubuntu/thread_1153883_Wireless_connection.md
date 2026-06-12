---
title: "Wireless connection"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by gotanothergrot on 2009-05-09
I have a remote PC (my sons) that has windows xp os with a wireless connection using Netgear 54 mbps usb adapter WG111v3.

Yesterday i installed hardy 8.04.01 for dual boot but have not the wireless connection established in Ubuntu. what should i do? Should i insert the WG111v3 software CD like i did in windows??

---

### Post by vallvi on 2009-05-09
I think you just need to configure your network manager. In Ubuntu 9.04 that is: system > preferences > network connections. Should be similar in your Ubuntu

There you tell ubuntu the details of your wireless & off you go!

---

### Post by swoody on 2009-05-09
> **gotanothergrot said:**
> I have a remote PC (my sons) that has windows xp os with a wireless connection using Netgear 54 mbps usb adapter WG111v3.

Yesterday i installed hardy 8.04.01 for dual boot but have not the wireless connection established in Ubuntu. what should i do? Should i insert the WG111v3 software CD like i did in windows??

Hi gotanothergrot ):P

Is the indicator light on your adapter lit up as it is in Windows? If it is, try clicking on the network icon in the upper right of your screen, and see if it recognizes any wireless network. If the indicator light is off, or you can't see any wireless networks, try going to "System">"Administration">"Hardware Drivers" In the new window that popped up, are there any drivers listed? If there are, select the wireless driver (select the one marked 'Recommended' if there is more than one) and select to activate it. After it does it's thing, you'll need to reboot the computer. Then test to see if you can detect any wireless networks.

Please post back here, and let us know if you get connected to the internet, whether there were or weren't any drivers available, and if you had any other issues arise :D

---

### Post by gotanothergrot on 2009-05-09
Thanks swoody, the indicator light does not light up as it does when windows boot. I navigated to the hardware drivers but none are listed...

---

### Post by safetycritical on 2009-05-09
Try this link. It's very helpful

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

:P

---

### Post by swoody on 2009-05-11
> **gotanothergrot said:**
> Thanks swoody, the indicator light does not light up as it does when windows boot. I navigated to the hardware drivers but none are listed...

Ok, on the Ubuntu machine, can you go to the terminal Applications>Accessories>Terminal and enter:
```
lspci
```
and post the output here? If you can't copy and paste the output, we really only need the lines that say "Network Adapter", "Wireless Adapter" or something to that extent. They should be towards the end of the output, but keep an eye out for anything else similar on the list. That'll let us know exactly what model adapter you're using, and will allow us to find out how to get this working for you :)

---

### Post by gotanothergrot on 2009-05-12
Thanks swoody, here's the output

graham@graham-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
graham@graham-desktop:~$

---

### Post by gotanothergrot on 2009-05-12
Swoody, disregard that output :redface: wrong computer, i must be loosing it.....

---

### Post by gotanothergrot on 2009-05-12
This is the output from my sons pc, Thanks swoody.

graham@branden-desktop:~$ lsusb
Bus 004 Device 005: ID 0846:4260 NetGear, Inc. 
Bus 004 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 001: ID 0000:0000  
graham@branden-desktop:~$

---

### Post by swoody on 2009-05-12
Disregard this post, I must be losing it too :)

---

### Post by gotanothergrot on 2009-05-12
swoody, i made a mistake and pasted lsusb instead lspci and i cant get to my sons PC until tomorrow, but the adapter is listed in the latter output, is this of any use??

---

### Post by swoody on 2009-05-12
After searching for what seems like forever, I think I have found something that may be of use for you :) Check out [this How-To]("http://www.uluga.ubuntuforums.org/showthread.php?t=732827") for installing the Netgear USB on Ubuntu. Just to let you know, you'll need an internet connection to follow this guide. If you can't connect your computer through an ethernet cable, you may be able to download the packages you'll need from another computer, and transfer them to your Ubuntu computer on a USB stick. The guide seems like it has been updated, and works up to Jaunty. If for some reason, it doesn't work for you in 8.04, let us know :D

---

### Post by gotanothergrot on 2009-05-13
Thank swoody, i had a go at saving the download to a memory stick transferring to other pc with limited results, heres the output i got,


graham@branden-desktop:~$ sudo apt-get -y install build-essential debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc lib64stdc++6-4.3-dbg lib64mudflap0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
graham@branden-desktop:~$ cd compat-wireless-2009-05-13
bash: cd: compat-wireless-2009-05-13: No such file or directory
graham@branden-desktop:~$ make
make: *** No targets specified and no makefile found. Stop.
graham@branden-desktop:~$ sudo make install
make: *** No rule to make target `install'. Stop.
graham@branden-desktop:~$ sudo make unload
make: *** No rule to make target `unload'. Stop.
graham@branden-desktop:~$ sudo modprobe rtl8187
graham@branden-desktop:~$ gksudo /ect/modules
graham@branden-desktop:~$ 

I probably will have to physically connect the computer like you said and take it from there,.Thanks again for your help.

---

### Post by swoody on 2009-05-26
Hi, gotanothergrot! I was just wondering if you got your wireless problems sorted out? If not, it appears that you need to download the package 'build-essential' from your other computer, and transfer it to your desktop that's having that's having the issue. You can do this in the same manner that you transferred the other packages. Then go through the installation steps again. Let me know if that works out for you :D

---

