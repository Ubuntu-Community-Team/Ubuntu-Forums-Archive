---
title: "SD Card Reader Not Working"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by daemonkity on 2009-12-17
I'm having the exact problem with my Sd Card reader and I also have an Asus Netbook.  Originally had Xandros but I put Ubuntu Remix on.. the USB is fine.

Mod Note: Moved posts from this [thread]("http://ubuntuforums.org/showthread.php?p=8526349#post8526349").

---

### Post by daemonkity on 2009-12-18
Neither of us seem to know how to do that.  Directions or link please?

---

### Post by daemonkity on 2009-12-18
*Here is what I get from typing "lspci" into the terminal:*
[B]
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
[/B][I]
Thanks very much in advance for the help =^..^=[/I]

---

### Post by daemonkity on 2009-12-18
> **jamieleshaw said:**
> Actually just a moment
just post lspci output

Okay.. I did that... does it help?

---

### Post by daemonkity on 2009-12-19
> **jamieleshaw said:**
> Actually just a moment
just post lspci output
So can anybody get us going in a direction where our SD card drives will be recognized by Ubuntu Remix?  ..and does the lspci data have any relevance?

---

### Post by szymon_g on 2009-12-19
> **daemonkity said:**
> So can anybody get us going in a direction where our SD card drives will be recognized by Ubuntu Remix?  ..and does the lspci data have any relevance?

lspci isn't relevant (in this case)
if your card reader havent been recognised out-of-the-box there is small chance that it will be supported. try to buy external reader (one on usb2)- they (usually) works fine, out-of-the-box on most systems.

---

### Post by daemonkity on 2009-12-19
> **szymon_g said:**
> lspci isn't relevant (in this case)
if your card reader havent been recognised out-of-the-box there is small chance that it will be supported. try to buy external reader (one on usb2)- they (usually) works fine, out-of-the-box on most systems.
My SD Card reader did initially work- it's certainly not broken- when I had the "out-of-the-box" OS on it (Xandros) but since I put Ubuntu Remix on it the card reader doesn't do anything.   really don't want to have an external SD card reader in addition to the built in one that I imagine requires only some simple tweaking :/

---

### Post by daemonkity on 2009-12-20
Anybody....?  Help??

---

### Post by daemonkity on 2010-01-24
I'm still trying to get my SD Card reader to work.. and of course, help would be appreciated.  Looking around on the internet I'm finding no solutions and others with the same problem.  I do not want to purchase an external reader to plug into the USB slots that do work fine- I feel this would defeat the purpose of having the SD Card slot.

---

### Post by Sef on 2010-01-24
Applications > Accessories > Terminal

Then copy and paste this code:

```
lsusb
```

Then copy and paste the results here.

That code will list your usb devices - both internal and external.

---

### Post by daemonkity on 2010-01-24
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by daemonkity on 2010-01-26
> **Sef said:**
> Applications > Accessories > Terminal

Then copy and paste this code:

```
lsusb
```Then copy and paste the results here.

That code will list your usb devices - both internal and external.

Okay.. I did this.  Was this info a means to an end?

---

### Post by daemonkity on 2010-01-29
I'm getting the impression that posting in these forums is pointless.  I *know* there must be a solution to this problem seeing how my netbook came with Linux and my SD Card reader worked fine then, so it's not a Linux-doesn't-support-SD-Card problem.  Why am I posting info about my netbook if the people requesting it don't follow up and help?

---

### Post by dolphinaura on 2010-01-29
[http://ubuntuforums.org/archive/index.php/t-1309239.html](http://ubuntuforums.org/archive/index.php/t-1309239.html)

---

### Post by Rex Bouwense on 2010-01-29
> **daemonkity said:**
> I'm getting the impression that posting in these forums is pointless.  I *know* there must be a solution to this problem seeing how my netbook came with Linux and my SD Card reader worked fine then, so it's not a Linux-doesn't-support-SD-Card problem.  Why am I posting info about my netbook if the people requesting it don't follow up and help?

Have patience.  Some of these guys and gals have full-time jobs or go to school and work.  They are on this web site because they enjoy helping people with problems that they may have had at one time or another.  Linux people are like that.  Someone will come up with the answer.  Please give them time.

---

### Post by daemonkity on 2010-01-29
> **Rex Bouwense said:**
> Have patience.  Some of these guys and gals have full-time jobs or go to school and work.  They are on this web site because they enjoy helping people with problems that they may have had at one time or another.  Linux people are like that.  Someone will come up with the answer.  Please give them time.
  Yeah, I'm trying, but it seems discouraging when the original thread I posted in ([http://ubuntuforums.org/showthread.php?t=1262443](http://ubuntuforums.org/showthread.php?t=1262443)) where my exact problem is shared has been looking for an answer since Sept 09. Having a netbook which has a very small amount of memory to begin with, not having a functioning slot for the disk you'll be storing things on is a pretty significant reason to stop using a particular operating system.  I though I might be pointed in a helpful direction when the moderator commented (aside from being told I was "hijacking" the other person's thread) asking for a certain output but there's no follow up.  Being rather new to Linux I don't even know what I might search for to educate myself on how to fix whatever the problem is.  Every quick-fix suggestion I've seen hasn't worked.

---

### Post by daemonkity on 2010-01-29
> **dolphinaura said:**
> [http://ubuntuforums.org/archive/index.php/t-1309239.html](http://ubuntuforums.org/archive/index.php/t-1309239.html)
Thanks you for the thread suggestion for more reading but my 3 USB ports work fine, it's just my SD Card slot.

---

### Post by dolphinaura on 2010-01-29
> **daemonkity said:**
> Thanks you for the thread suggestion for more reading but my 3 USB ports work fine, it's just my SD Card slot.
im implying that the disk is in /dev , but it just doesnt show up. it has to be manually mountined, which there are instructions on how to do in that thread.

---

### Post by daemonkity on 2010-01-29
> **dolphinaura said:**
> im implying that the disk is in /dev , but it just doesnt show up. it has to be manually mountined, which there are instructions on how to do in that thread.
How/where are you seeing specifically the SD slot being recognized? If I plug things into my USB ports the "lsusb" read out changes to=

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0781:555f SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


... the 4th and 6th line being removable drives.  Whether or not the SD Card is in, I get the same readout=

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

There's no change I'm seeing.  Am I missing something?  If you specifically see which is the SD port could you please post that so I can tell my computer what it's supposed to be looking for to manually mount?

---

### Post by Methuselah on 2010-01-29
You know...I never got my SD card slot to work on an Asus netbook I had even though it came with Xandros linux.
I'm not sure what was up with that thing.

---

### Post by daemonkity on 2010-01-29
> **Methuselah said:**
> You know...I never got my SD card slot to work on an Asus netbook I had even though it came with Xandros linux.
I'm not sure what was up with that thing.
D:  ....!  Oh no

---

### Post by dolphinaura on 2010-01-31
> **daemonkity said:**
> How/where are you seeing specifically the SD slot being recognized? If I plug things into my USB ports the "lsusb" read out changes to=

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0781:555f SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. **
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


... the 4th and 6th line being removable drives.  Whether or not the SD Card is in, I get the same readout=

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

There's no change I'm seeing.  Am I missing something?  If you specifically see which is the SD port could you please post that so I can tell my computer what it's supposed to be looking for to manually mount?
Problem is bolded.
All JMicron devices are a pain in the @$$ when it comes to linux/mac. Support only recently came out for its SATA controlers, so its gonna take some time for the stuff to be put in for your card reader. Its probably cause their a pretty new company.

---

### Post by daemonkity on 2010-02-01
> **dolphinaura said:**
> Problem is bolded.
All JMicron devices are a pain in the @$$ when it comes to linux/mac. Support only recently came out for its SATA controlers, so its gonna take some time for the stuff to be put in for your card reader. Its probably cause their a pretty new company.

Once again, thank you for your attempted help, but no, that is not the problem.  The **BOLDED** item is what my external hard drive shows up as.  It will show up as that in any USB port I plug it into and it is recognized/useable just fine.  The problem is with my SD CARD slot which is NOT showing up in the list.  The comparison I was trying to show was that my computer's recognized stuff changes (I deliberately plugged in stuff I had all at once in the multiple USBs to have them read as something) with external devices when it work.  Alternately, when I put my SD Card in, there is no change.  The slot is not showing up whether there's something in it or not.

---

### Post by ironside on 2010-02-05
Ok I have the same problem. 

Here is a couple of read outs;

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

Another one

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

any help would be appreciated.

---

