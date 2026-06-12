---
title: "having trouble with my wireless conection"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by colorguardgal17 on 2007-10-09
i am a high school student learning about linux and i have it on my lap top but my wireless conection wont conect. i think it is not supported by linuxs what can i do to get it working in linux.

---

### Post by jingo811 on 2007-10-09
Can you find info about your wireless device in this database?
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by colorguardgal17 on 2007-10-09
i did not see it there is there any thing else

---

### Post by jingo811 on 2007-10-10
If you can't see your device in that database you probably won't be able to run Linux's wireless Native drivers.
That's ok because I couldn't find my Wireless device either in that database.  

That just means you'll have to solve things with the Ndiswrapper method.  Try this blog that someone suggested to me just recently.  ( I didn't follow that tutorial because I was experimenting on a Debian system, but I'm sure it will work smooth for you. )
[http://i-eat-noobs.blogspot.com/](http://i-eat-noobs.blogspot.com/)

---

### Post by kevdog on 2007-10-10
Please post

lspci -nn
lshw -C network

And then we decide the best course of action for you

---

### Post by colorguardgal17 on 2007-10-10
what does this mean  " lspci -nn
                                    lshw -C network"

---

### Post by jingo811 on 2007-10-10
It means you should open up the program Terminal and copy and paste the commands and run them.

_Applications> Accessories> **Terminal**_

Then copy and paste with your mouse the outputs of those 2 commands in here so KevDog can take a look at things.

---

### Post by colorguardgal17 on 2007-10-10
ok i will try that when i get home and see if it works. so how long have you h linux and do you like better than windows

---

### Post by jingo811 on 2007-10-10
I've been using Linux since 2005.  With a Dual Boot setup with Windows XP as my secondary operating systems for all those Windows games I've bought which won't work properly enough in Linux.

Still I would only use Linux for work, Internet and bank matters.  Because Linux have never virused on me during these 2 years and I've never had to defragment my hard drive during these years.

With Windows even without doing much writing to the disks you still have to do major defragmentations every 5 weeks or so.

---

### Post by colorguardgal17 on 2007-10-10
that is awsome i cant wait till i start work on linux more. that is great that you did not have to defrag the hard drive so far

---

### Post by colorguardgal17 on 2007-10-10
what is the text that is spouse to go were the * is in terminal

---

### Post by colorguardgal17 on 2007-10-10
it is not working to do that ndisgtk thing. do you have any suggesting

---

### Post by jingo811 on 2007-10-10
Are you following that blog I just recommended?  
It seems like you haven't played with Linux before so I don't think you should follow that tutorial anymore.  It requires some basic understanding of editing and navigating in the filesystem.  Trying to fill in all the holes for that guide will be messy!

Do as KevDog told you post the outputs of those 2 commands in Terminal and then KevDog will give you a proper strategy to this problem.

```
$ **lspci -nn**
```
```
$ **lshw -C network**
```
You are not supposed to type in the $ sign it's common convention telling ppl to insert commands into Terminal a.k.a. "Bash" or simply the "Shell".

---

### Post by colorguardgal17 on 2007-10-11
yeah i kind of did not understand all those things to type into the terminal. so i will try that and get back to you.

---

### Post by colorguardgal17 on 2007-10-11
kevdog what do i do after i put those codes in

---

### Post by kevdog on 2007-10-11
Post the results here in the forum -- cut and paste them

---

### Post by colorguardgal17 on 2007-10-11
**_for lspci -nn_**
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #2) [8086:2484] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #3) [8086:2487] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 41)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
02:04.0 Communication controller [0780]: Conexant HSF 56k HSFi Modem [14f1:2f00] (rev 01)
02:05.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 41)
03:00.0 Ethernet controller [0200]: Belkin Unknown device [1799:701f] (rev 20)
[B][U]
and for lshw -C network[/U][/B]
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 00:02:a5:6d:fb:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.0.102 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:d0215000-d0215fff ioport:3040-307f irq:10
  *-network UNCLAIMED
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 0
       bus info: pci@03:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:34000000-340003ff irq:11

---

### Post by kevdog on 2007-10-11
Just to make sure of something before we start, please do a search on google for this device to discover the chipset.  I just dont want to proceed blindly down the ndiswrapper path without at least having some solace that Im doing the right thing?

---

### Post by jingo811 on 2007-10-12
KevDog could you highlight what parts of the above 2 outputs that's most relevant in order to do the Google device search?  I'm trying to help a friend setup his wireless which I don't have any hard copy information to go by.  But I don't really see what from the above lines I should use to make a google search on.

---

### Post by kevdog on 2007-10-12
Basically all the above input states is Belkin --- there is usually a chipset listed.  In this post there is no make or model of the device.  You need to take the make and model of the device and google around to see what others have said about the chipset.  Its not listed above.

---

### Post by colorguardgal17 on 2007-10-12
ok i will not google it. so what do i do

---

### Post by jingo811 on 2007-10-13
Find some hard copy information!  Like what kind of Laptop brand and version it is from the manuals and card board packages that came with the purchase.
Or if your Wireless is a component that you added on after the PC purchase look at the box what brand name and version it says.  Then list all those informations you think is important in here.
If your machine is from Dell, HP and such companies looking at the name and version for the PC can usually give you leads.

Do it like this when you've found out about the information and put ? whenever you're not sure or don't know.
Mikeys example:

**brand:** ASUS WL-161

**specs: **
[LIST]
[*]802.11b
[*]USB 1.1
[*]Data rates: 11 ; 5.5 ; 2 ; 1 Mbps auto select
[*]WEP 64 / 128 bit
[/LIST]

---

