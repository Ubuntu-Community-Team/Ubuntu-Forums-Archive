---
title: "Can't connect to internet on Ubuntu 10.04"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by faviouz on 2011-01-10
Hi,
 
I installed Ubuntu 10.04 yesterday, and after trying to connect to the internet an endless number of times, I come here for help.
 
First, I tried connecting through my router, which I knew it wasn't going to work as I was told by a friend.
 
Then I tried connecting through my ethernet cable so I could update to 10.10 which would probably fix the wireless problem. But surprisingly I couldn't connect with my ethernet cable either! I saw there "Auth eth0" when I plugged it in, but in the end it didn't work.
 
And then I click the network icon again, after removing the ethernet cable and doing some resets to both my modem and router, I see "SMC" in there, which is my router. I tried to connect and the icon indicated that I was connected, but when I gave Firefox a go, pages hang at loading.
 
Still connected to "SMC", I tried to update to 10.10 again. At first I thought it was going to work because it was fetching updates and the bar was moving, but when I expanded the updates list, they all said Failed and after a moment a window popped up saying it couldn't finish the operation.
 
Basically, I can't connect either with my ethernet cable or wireless. I don't think it is a router or modem problem, because I was able to go online before installing Ubuntu. Having that said, what do you good people suggest me to do?
 
Thank you and please bare with me as I am still a newbie to Linux . :P

---

### Post by TBABill on 2011-01-10
Can you open a terminal and enter ```
lspci
``` or use ```
lsusb
``` if this is a USB device? Paste the output back here so we can see what your hardware is to determine how to help.

---

### Post by taseedorf on 2011-01-10
Most ethernet drivers should be installed out of the box... If you plug a cat5 cable into your router from your computer try opening a terminal and typing 'ifconfig'  Do you get an IP address for your device?

---

### Post by laidback on 2011-01-10
If it's FF that's hanging I had the same.
Solution...run FF, type about:config in the URL window (internet address section) and accept the warning.
Now in the filter section type ipv6 which should produce 1 line...

network.dns.disableIPv6

which is probably set to false at the moment.

You want to change the setting to True...to do that just double click the line with the mouse and it toggles from false to true (and back if you want)

restart FF and try again. This time I think you'll be OK.

---

### Post by faviouz on 2011-01-10
I got this when I ran lspci in the terminal:
 
```
 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```
 
> **taseedorf said:**
> Most ethernet drivers should be installed out of the box... If you plug a cat5 cable into your router from your computer try opening a terminal and typing 'ifconfig' Do you get an IP address for your device?
 
I'll try that in a sec and will edit this post.

---

### Post by faviouz on 2011-01-10
Silly me, I didn't have the ethernet cable plugged in correctly before. Just tried it again, and I was able to connect to the internet using the ethernet cable. Then I just updated the system to 10.10 and I got wireless working too. Everything is fine now, thank you!

For those who found this thread and are also wondering how to get wireless working, just update to 10.10 and it will most likely work.

---

