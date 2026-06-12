---
title: "&quot;Connect To Hideen Wi-Fi Network&quot; is greyed out - Ubuntu Studio 14.04-1"
date: 2015-09-14
forum: Networking &amp; Wireless
---

### Post by RobertoRecordo on 2015-09-14
In a live session of Lubuntu 15.04 I am able to easily connect to my hidden SSID: I go to the network icon in the top panel, click on it, select "Connect To Hideen Wi-Fi Network"  and the rest is easy.

I did a clean  installed Ubuntu Studio 14.04-1 and I know my wireless is on because when I go to the Network icon I see the neighbors routers in the wireless network list, and they go away when I turn the wi-fi card off with the button on my laptop.

The computer is an elderly nc4000 pentium m 1.4 Ghz 1GB  40GB drive that has seen little use. The install took two hours, and the single core processor ... well, I just want to get some idea if the JACK can be made to do anything useful under these difficult conditions, then I will put a lightweight distribution on it.

In the meantime - please help me understand why I can not make This distro work on my wifi. Mint 17, Puppy 5.7, Knoppix 7.2, Damn Small Linux, all do it with no headaches.  The hardware is known to work, the radio is on, and _when I enable SSID broadcast, I can connect_. Also greyed out is the wired LAN disconnect, create new wi-fi network and others.

Gedit refused to open the "wireless info script" results, I had to use Libre Writer to open and save as text. I couldn't see waht was wrong.

The result of the wireless info script on the working Lubuntu 15.04   => wireless-infoLubuntu15_04.tar.gz (5.9 KB)


The result of the wireless info script from the problematic  Ubuntu Studio 14.04-1 => wireless-info_UbuntuStudio14_04.tar.gz (4.8 KB)

Thnks for your help,

-Rob

---

### Post by RobertoRecordo on 2015-09-15
I did not keep track of how many times I rebooted the computer and observed the problem prior to posting.  I rebooted this morning, and the problem was unchanged. 

I decided to try the Ubuntu 14.04-1 Live DVD, and was able to connect to the hidden SSID with no problem. As I had booted with the Ethernet cable removed, I inserted the cable, rebooted and was again successful.

When I booted the installed version, I was able to connect to the hidden SSID.

I am marking this SOLVED, and will repost if it seems to be an intermittent problem not related to my hardware.

---

