---
title: "Newb stumped by Ubuntu"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by theronstar on 2009-11-22
Hello,
 
I run Vista and just installed Ubuntu. When I go to the network icon at the top right it shows me "connection established" but in parentheses it says 0% 
 
Firefox has page cannot be displayed. I am guessing there may be something else the network connections needs off me. I've put SSID and Key in but in IPv4 it is set to shared to computer and IPv6 to Ignore. Do you think there is a bit of data I need to put in one of those boxes?
 
Thanks.

---

### Post by sandyd on 2009-11-22
how far are you away from your router

---

### Post by theronstar on 2009-11-22
Hmm, my router is in another room from me. I am using a [http://www.amazon.co.uk/Edimax-Ew-7711utn-150Mbps-Mini-size-Adapter/dp/B001UE6OU0/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258937258&sr=8-1](http://www.amazon.co.uk/Edimax-Ew-7711utn-150Mbps-Mini-size-Adapter/dp/B001UE6OU0/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258937258&sr=8-1)
 
When I installed it in windows it just connects at power up but when I get to the ubuntu desktop nothing happens. At first I thought it is not supported there but the wireless network seems to pick up hot points although some have some funny looking characters. This is why I am wondering if it is something I am not entering properly or if my usb is not compatible with Linux. I'm gonna call it a night here cos I've been at this all day. I'll be grateful for any pointers.

---

### Post by sandyd on 2009-11-22
when you get back to ubuntu, open a terminal
(applications -> Accessories -> Terminal)
and type ( or copy) this in
```

lspci >> ~/Desktop/lspci.txt
```then attach the file lspci.txt (its on your desktop) to your next post.

---

### Post by theronstar on 2009-11-25
Hello, sorry for the delay in responding. I'd been sick the last few days. I did the command and am copying what it gave me.

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)


I hope this makes some sense. Thanks.

---

### Post by dearingj on 2009-11-25
> **carlee said:**
> when you get back to ubuntu, open a terminal
(applications -> Accessories -> Terminal)
and type ( or copy) this in
```

lspci >> ~/Desktop/lspci.txt
```then attach the file lspci.txt (its on your desktop) to your next post.

Actually, I think the command should be lsusb since the OP is using a USB wireless adapter.

---

### Post by theronstar on 2009-11-25
Sure, I will go back into Linux now. Thanks for the pointer.

---

### Post by theronstar on 2009-11-25
This is what the lsusb command returns.

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 06f8:3003 Guillemot Corp. 
Bus 002 Device 002: ID 0644:0200 TEAC Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 03f0:5511 Hewlett-Packard DeskJet F300 series
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7711  
Bus 001 Device 003: ID 07ab:fcf6 Freecom Technologies 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks

---

### Post by sandyd on 2009-11-25
theirs already a problem in the output im seeing. from what i see, your USB adaptor isnt listed in the hardware.
is your USB wireless adaptor ACTUALLY working?
go try it on another computer and report back.

---

### Post by theronstar on 2009-11-25
Hmm, I was suspecting that. I'm using this USB adapter in Vista at the moment to access the internet and communicate here right now. I'm wondering if it is that Linux does not support it but then if it did not I am confused by it saying 'connection established' whenever I load up Linux.

---

### Post by pi.boy.travis on 2009-11-25
> **theronstar said:**
> Hmm, I was suspecting that. I'm using this USB adapter in Vista at the moment to access the internet and communicate here right now. I'm wondering if it is that Linux does not support it but then if it did not I am confused by it saying 'connection established' whenever I load up Linux.

If you have the means, connect to the internet via ethernet with Ubuntu, keeping the adapter plugged in, and go to System>Administration>Hardware Drivers and see if you can find a driver there.

Hope this helps. . .

---

### Post by theronstar on 2009-11-25
My router is downstairs so an ethernet connection to my pc will prove quite tricky. I have browsed the contents of the installation CD and see it has a folder with the title Linux drivers. The only thing is unlike Windows where a wizard just pops up and I click next to install this does not happen in Ubuntu and I am unsure how to pass on the drivers from the CD to Linux. Can you follow what I am saying sorry if I'm not making sense? Can anyone tell me how?

---

### Post by pi.boy.travis on 2009-11-25
> **theronstar said:**
> My router is downstairs so an ethernet connection to my pc will prove quite tricky. I have browsed the contents of the installation CD and see it has a folder with the title Linux drivers. The only thing is unlike Windows where a wizard just pops up and I click next to install this does not happen in Ubuntu and I am unsure how to pass on the drivers from the CD to Linux. Can you follow what I am saying sorry if I'm not making sense? Can anyone tell me how?

If the drivers are proprietary, they will not be on the Ubuntu CD, due to legal restrictions.  In addition, most drivers are modules added to the kernel.  In most cases, this is much, much easier than the Windows way of doing things, unless your hardware requires some proprietary driver. . .

---

### Post by theronstar on 2009-11-25
Oops. I guess I never explained what I was trying to say well. I'll start over. I installed my USB adapter on Vista and have got internet access with no problems via that. I installed Ubuntu the other day and I get a 'connection established' box at start up but no actual connection. The lspci and lsusb logs do not show up the wireless adapter.

Does this mean then that the drivers that were installed in Vista that enable the device to work will only work for when I am in Windows and I will need to install the Linux driver for the USB adapter in Linux. The USB adapter installation CD has a folder entitled Linux drivers but I do not know how to install them in Linux mode because unlike Windows, Linux does not pop up a wizard that I click next in order to complete an installation process. So my question was, how do I pass the Linux drivers from the CD to Linux. I hope I worded what I was saying better this time. Sorry for any confusion

---

### Post by pi.boy.travis on 2009-11-25
> **theronstar said:**
> Oops. I guess I never explained what I was trying to say well. I'll start over. I installed my USB adapter on Vista and have got internet access with no problems via that. I installed Ubuntu the other day and I get a 'connection established' box at start up but no actual connection. The lspci and lsusb logs do not show up the wireless adapter.

Does this mean then that the drivers that were installed in Vista that enable the device to work will only work for when I am in Windows and I will need to install the Linux driver for the USB adapter in Linux. The USB adapter installation CD has a folder entitled Linux drivers but I do not know how to install them in Linux mode because unlike Windows, Linux does not pop up a wizard that I click next in order to complete an installation process. So my question was, how do I pass the Linux drivers from the CD to Linux. I hope I worded what I was saying better this time. Sorry for any confusion


Ah, sorry about that.  The drivers are on the CD. . . 

What files are in the Linux Drivers folder?  Are they .deb packages, or scripts (.sh) ?

---

### Post by theronstar on 2009-11-25
The main folder named Linux drivers is .tar and within that folder there are several sub folders. Some have a .c extension, some a .h and some a .dat. 

I've always only known to look for a .exe file and that brings up a wizard. I am quite out of my depth here.

---

### Post by pi.boy.travis on 2009-11-25
> **theronstar said:**
> The main folder named Linux drivers is .tar and within that folder there are several sub folders. Some have a .c extension, some a .h and some a .dat. 

I've always only known to look for a .exe file and that brings up a wizard. I am quite out of my depth here.



I would guess that the drivers are in source-code form. . . 

Unfortunately, I'm not sure where to go from here.  You may need to check the manufacturer's website for instructions, or maybe a readme.txt or install.txt file. . .   
 
Sorry I can't provide further instructions. . .

---

### Post by Finland_Penguin on 2009-11-25
> **theronstar said:**
> The main folder named Linux drivers is .tar and within that folder there are several sub folders. Some have a .c extension, some a .h and some a .dat. 

I've always only known to look for a .exe file and that brings up a wizard. I am quite out of my depth here.

Open up the tar file, and extract it to 
~/Wifi_Drivers

open a terminal and type:
```

cd Wifi_Drivers
sudo -s
make

```


try that and tell us what happens.

---

### Post by theronstar on 2009-11-25
I tried that command and I got after I typed make. I forgot the beginning of the line that the terminal displayed but I remember it ended Stop. 

I am wondering whether this is a driver issue or a way the connection is meant to be established. I do get a connection established when I load up Ubuntu but just no connection. 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax) my device is 
 EW-7711UTn. Is that link saying Linux already supports it?

---

### Post by Shpongle on 2009-11-25
if you post the tar archive up maybe someone can compile it for you and post instructions, shouldn't be hard if its in c  are you sure theres no read me , if you can bring your box to the router  with the usb in and try search for drivers as mentioned above! , its worth a try

---

### Post by theronstar on 2009-11-26
Hello, sorry I did not mention this before but yes there is a readme though I cannot make any real sense of it. Sorry if this question sounds stupid but how do I search for drivers at the router?

---

### Post by wrgb2 on 2009-11-26
Go to System > Administration > Hardware Drivers, and it will search for any available proprietary drivers for your hardware.

---

### Post by theronstar on 2009-11-26
Hello. 

The check said I had no propietary hardware drivers. I put on some screenshots of my page cannot be displayed problem and how it looks to me as I don't think I am explaining it properly.

My network is the O2 wireless one. I don't know why the others come up with funny symbols as they don't come up like that in here (I'm back in Windows now).

---

### Post by theronstar on 2009-11-28
Hey. A big thanks to everyone who helped me.

I FINALLY got this issue resolved it was so frustrating. Basically there were two drivers that were conflicting and I had to write a blacklist to rt2800usb in a file someplace. Now my wireless works as normal. 

How do I  mark the thread solved now?

---

### Post by rednano12 on 2009-11-28
Thread Tools -> Mark as Solved

---

