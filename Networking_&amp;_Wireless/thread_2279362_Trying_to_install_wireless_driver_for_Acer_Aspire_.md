---
title: "Trying to install wireless driver for Acer Aspire V3 572 (Ubuntu 14.04)"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by kevin167 on 2015-05-22
Hello,

I have been having quite a difficult time trying to install the wireless drivers on my Acer Aspire V3 572. I have been reading through these forums all day today attempting to fix my problem, but have not found any success

[B]The problem:
[/B]I can't connect to wireless internet. My wireless drive is working on Windows 8.1. After going to Settings > Software and Updates > Additional Drivers. I see:

"Broadcom Corpiration: BCM43228 802.11 a/b/g/n
This device is not working
(option 1)Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
(option 2)Do not use this device"

The button for "Do not use this device" is the default option. When I attempt to change it to "Using Broadcom 802.11 Linux STA ... (proprietary)" and click "Apply Settings", the Additional Drivers screen either, 1) goes grey and nothing happens (I've left it on for up to 15 minutes), or 2) I see a bar that looks like it's attempting to load (but never does). Similar to this video: [https://www.youtube.com/watch?v=4VVosf9p5GM](https://www.youtube.com/watch?v=4VVosf9p5GM)

Ethernet connection works completely fine.

[B]What I have tried:
[/B]-restarting multiple times after hitting "Apply Settings" following the selection of "Using Broadcom 802.11 ... (proprietary)".
-installing "bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb" upon recommendation for a similar problem (I was told that the medium for installing this program could not be found)
-followed the previously posted youtube video advice
-applied many entrees into the terminal which were recommended on here (I don't have them all written down and I am willing to retry them all upon request

**Extra information:**kevin@kevin-Aspire-V3-572PG: -$ uname - a
linux kevin-aspire-v3-572 3.16.0-30-generic #40-14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 GNU/Linux
kevin@kevin-Aspire-V3-572PG: -$ cat /etc/issue
Ubuntu 14.04.2 LTS \n \l

kevin@kevin-Aspire-V3-572PG: -$ lspci -nn | egrep '0200|0280'
02:00.1 Ethernet control [0200]: Realtek semiconductor Co., ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Control [10ec:8168] (rev 12) 
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
kevin@kevin-Aspire-V3-572PG: -$ rfkill list all
0: acer-wireless: Wireless LAN
soft blocked: no
hard blocked: no
1:acer-bluetooth: Bluetooth
soft blocked: yes
hard blocked: no
2: hci0: Bluetooth
soft blocked: yes
hard blocked: no


kevin@kevin-Aspire-V3-572PG: -$ lspci -vnn |grep -A 9 Network
0300.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359] 
Subsystem: Foxconn International, Inc. Device [105b:304b]
Flags: bust master, fast devsel, latency 0, IRQ 19
Memory at c4000000 (64-bit, non-prefetchable) [size=16k]
Capabilities: <access denied>
Kernel driver in use: bcma-pci-bridge


kevin@kevin-Aspire-V3-572PG: -$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for kevin:
E: Could not get lock /var/lib/dpkg/loc - open (11: Resource temporarily unavailabl)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kevin@kevin-Aspire-V3-572PG: -$ sudo modprobe wl
modprobe: FATAL: module wl not found

---

### Post by Hadaka on 2015-05-22
Hi, pleas COPY and paste one line at a time.
Ignore any minor errors or warnings.be sure to do each line..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg -r bcmwl-kernel-source
sudo apt-get update
```
boot
then do.
```
sudo apt-get install bcmwl-kernel-source
sudo modprobw wl
```
thanks.

---

### Post by kevin167 on 2015-05-22
Hello,

Thanks for the reply. I tried the steps that you gave me line by line, copy and paste.

For the first box of codes I received a couple messages saying that it could not be removed because it was not installed. 

The second set of code I received a message saying that 4 drivers were successfully installed. When I entered in "sudo modprobw wl" I was told that Terminal could not execute the code. I changed it to "sudo mdprobe wl" instead and it seemed to run.

I returned to the Additional Drivers screen and clicked on "Using Broadcom 802.11 Linux ... (proprietary)", then "Apply Changes". Instead of a grey screen I am now receiving the grey screen plus a loading bar next to "Applying Changes...". However, the bar does not seem to be moving since I started the process 5 minutes ago. I am going to leave it on for another 15-20 minutes to see if it will make any progress. 

Perhaps I should have asked earlier: do I need to be connected to the internet before I run these processes?

Thank you for the reply

Kevin

---

### Post by Hadaka on 2015-05-22
Hi this 
sudo modprobw wl
was a typo on my part..sorry..you corrected it correctly.
Yes..any time you see  apt-get  that means you are getting
files and should be connected to the internet by wired connection.,
also...ignore the offer of proprietary -additional drivers...that
is a bit of a long time glitch that has caused alot of problems..
so just ignore it...once you load the bcmwl-kernel-source drivers
thats all you need to do...and then modprobe wl.
thanks

---

### Post by kevin167 on 2015-05-23
Okay, so the first set of instructions went well. I received a large file of new software which I installed. 

After  running "sudo apt-get install bcmwl-kernel-source" it asks me to put in  a CD named "Ubuntu 14.04.2 LTS - Trusty Tahr -Release amd 64". However,  I installed Ubuntu using a formatted flash drive. 

I tried running the code again after putting the flash drive into the USB port before running the code. This time I get:
E: Could not get lock /var/lib/dpkg/lock - open (11:Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Hope you can help me further!! 

Thanks a lot.

Kevin

---

### Post by Hadaka on 2015-05-23
are you using a working wired internet connetion??

---

### Post by kevin167 on 2015-05-23
Yeah, I was using a wired connection to run the set of instructions. I did notice that it was difficult to connect to the ethernet. I was only able to connect after taking the ethernet plug out of the computer, booting, and reinsterting it. I may have had a poor connection when I ran the second set of instructions. The first set of instructions ran great.

Is there any other information I can supply? 

Also, when I run:
```
sudo apt-get install bcmwl-kernel-source
```

Should I expect it to prompt me for the CD-rom? What is it supposed to be doing?

---

### Post by Hadaka on 2015-05-23
its doing that because you choose additional drivers.
do this again..one line at a time..even if they fail
from a working wired connection
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg -r bcmwl-kernel-source
```
then do..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
this time dont do anything with proprietary or additional drivers

---

### Post by kevin167 on 2015-05-24
Thanks a lot for the reply.

Just to clarify, is there a point during inputting the code that will prompt me with the option to do something to the proprietary or additional drivers? I dont remember it asking me about that.

Sorry, Im new to this. 

Thanks again!

---

### Post by Hadaka on 2015-05-24
on a new install i believe it does prompt you at some point,
i dont recall when, the point is...dont do anything with additional
or proprietary drivers..ignore them.
thanks.

---

### Post by kevin167 on 2015-05-24
YEAH!!!

It worked!!! Thanks so much!

I've been looking forward to marking this thread as "solved"

---

### Post by Hadaka on 2015-05-24
Great !  I have been looking forward to you marking it SOLVED also.
enjoy.

---

