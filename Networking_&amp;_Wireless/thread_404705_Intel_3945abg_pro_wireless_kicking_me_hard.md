---
title: "Intel 3945abg pro wireless kicking me hard"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by linuxgajin on 2007-04-08
and it hurts! I have tried guide after guide and none seem to be working. I can connect through LAN to my router but as for my wireless card I can't seem to get it working. I bought a brand new Toshiba laptop and it came with this card - first thing I did was uninstall Vista and installed Ubuntu feisty fawn. So far it's been a frustrating experience as I have little experience with linux. If someone could help me out I'd really appreciate it. I don't know what to do at this point other than install windows again and I really don't want to do that =|

Linux Geeks rescue me!:guitar:

---

### Post by rolando on 2007-04-08
Isnt Feisty still in beta?

I would stick with 6.10 Edgy Eft.

What does it say for your laptop at [http://tuxmobil.org/toshiba.html](http://tuxmobil.org/toshiba.html)

:)

---

### Post by linuxgajin on 2007-04-08
i tried 6.10 and couldn't even get my LAN to work.. I tried 6.06 also and the same problem. FF is the only one that would work through LAN. After reading through the forums I've heard people recommending 7.04 for this particular wireless card. I guess those 2 reasons are why I'm using feisty fawn :)

---

### Post by linuxgajin on 2007-04-08
Oh and I went to tuxmobil and they didn't have my model number listed... I have the satellite A130. Thanks anyways for the suggestion. :)

---

### Post by rolando on 2007-04-08
Keep plugging away mate, the hours Ive spent trawling for gems.. then get them eventually.

:)

---

### Post by linuxgajin on 2007-04-08
I've spent a good 10 hours researching and trying every "tutorial" and "How-to" and I get an error here and there; nothing works. I appreciate the encouragement; I'd appreciate something that works more though. :) man drivers is a real b*tch for linux.

---

### Post by PilotJLR on 2007-04-08
Sorry for the basic question, but did you enable the restricted driver for the card? Feisty should support this.
Check this out: [http://www.michaellarabel.com/?k=blog&i=129](http://www.michaellarabel.com/?k=blog&i=129)

---

### Post by rolando on 2007-04-08
I have a nx6325 and my wireless card is not supported by Ubuntu, I used ndiswrapper and it has worked ever since.

I suppose you seen this one for your card

[http://ubuntuforums.org/showthread.php?t=368134](http://ubuntuforums.org/showthread.php?t=368134)

---

### Post by linuxgajin on 2007-04-08
> **PilotJLR said:**
> Sorry for the basic question, but did you enable the restricted driver for the card? Feisty should support this.
Check this out: [http://www.michaellarabel.com/?k=blog&i=129](http://www.michaellarabel.com/?k=blog&i=129)

Yes. Upon boot up it showed my card was "enabled and in use" under the restricted drivers.

---

### Post by linuxgajin on 2007-04-08
> **rolando said:**
> I have a nx6325 and my wireless card is not supported by Ubuntu, I used ndiswrapper and it has worked ever since.

I suppose you seen this one for your card

[http://ubuntuforums.org/showthread.php?t=368134](http://ubuntuforums.org/showthread.php?t=368134)

```
light@Deathnote:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D4:96:DF:6C  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe96:df6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13000663 (12.3 MiB)  TX bytes:2694848 (2.5 MiB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

lsmod |grep ipw3945 does nothing at all

```

light@Deathnote:~$ lsmod | grep ipw3945

```

The universe explode when I modprobe...

```

light@Deathnote:~$ sudo modprobe ipw3945
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw3945 (/lib/modules/2.6.20-14-386/kernel/ubuntu/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2007-04-08 21:29:53: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```


If I need a clean install I can do that easily. But what am I doing wrong?:confused:

---

### Post by rolando on 2007-04-08
If it works in Windows ndiswrapper should work.  This is what I tried when I hit a brick wall with my onboard wireless (HP nx6325), and I havent looked back since.  I wanted to get the wireless working at any cost. I just wont work in windows any more.

---

### Post by sabi on 2007-04-08
Please post the results of:

sudo lshw -C network
sudo ifconfig -a
sudo iwconfig

I will try to help you resolve this issue.

Sabi

---

### Post by linuxgajin on 2007-04-08
sudo lshw -C network

```
light@Deathnote:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:d8000000-d8000fff irq:10
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:96:df:6c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:5000-50ff iomemory:da000000-da000fff irq:18

```

sudo ifconfig -a

```
light@Deathnote:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D4:96:DF:6C  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe96:df6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19117958 (18.2 MiB)  TX bytes:4103045 (3.9 MiB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

sudo iwconfig

```
light@Deathnote:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```


Thanks for taking a look at my problem sabi :)

---

### Post by sabi on 2007-04-08
Some more background.

Is this a new install of Feisty?

Has the card ever worked in Feisty?

Have you installed any updates to your system?

What does:

sudo uname -r 

return?

Sabi

---

### Post by linuxgajin on 2007-04-08
It's a new install.

Has it ever worked? No - only through LAN but not wirelessly.

I ran updates in update manager.

uname -r:

2.6.20-14-386

If it would help my problem I can do a fresh install.

---

### Post by sabi on 2007-04-08
No, a fresh install won't produce any different results. We need to find the underlying problem and fix that.

```

Code:

sudo cp /sbin/ipw3945d-2.6.20-14-generic /sbin/ipw3945d-2.6.20-14-386
sudo modprobe ipw3945
sudo /sbin/ipw3945d-2.6.20-14-386


```

Try this and post the results.

Sabi

---

### Post by linuxgajin on 2007-04-08
I copy/pasted your code to make sure I made no syntax mistakes. I type in the first command and nothing happens. *scratches head* it prompts me for my root password and nothing happens. I tried again with the same result.

```
light@Deathnote:~$ sudo cp /sbin/ipw3945d-2.6.20-14-generic /sbin/ipw3945d-2.6.20-14-386
Password:
light@Deathnote:~$ 

```

Ok next line... this looks painful.

```
light@Deathnote:~$ sudo modprobe ipw3945
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-14-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw3945 (/lib/modules/2.6.20-14-386/kernel/ubuntu/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2007-04-08 22:15:35: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```

Moving along... more suprises here.

```
light@Deathnote:~$ sudo /sbin/ipw3945d-2.6.20-14-386
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-04-08 22:15:53: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```


Looks like none of them came out the way they were intended too.:confused:

---

### Post by sabi on 2007-04-08
When you click on:

System-Administration-Restricted Drivers Manager

do you see this image 

[http://www.michaellarabel.com/external/feisty-network1.jpg](http://www.michaellarabel.com/external/feisty-network1.jpg)

Sabi...

---

### Post by linuxgajin on 2007-04-08
Yes. But it says it needs a computer restart. So I'm going to do that now. Brb then I'll post results.

---

### Post by linuxgajin on 2007-04-08
I've restarted twice now... here's what I see when I open up restricted drivers.
Once was a "restart."
The next was a "turn off" and "turn on" approach. Both times yielded the same results.

[http://i11.tinypic.com/437c8kj.png](http://i11.tinypic.com/437c8kj.png)

---

### Post by sabi on 2007-04-08
Can't see the image, link is not working for me.

Tell me what you see ...

Sabi

---

### Post by linuxgajin on 2007-04-08
it looks the same with the exception under "status" it says "needs computer restart"`

---

### Post by linuxgajin on 2007-04-08
let me rephrase... instead of the "in use" category it says "status" and it says "needs comptuer restart" under that category.

The "enabled" box is checked, however.

---

### Post by sabi on 2007-04-08
Made a slight change to the first line. Try this again.

```
sudo cp /sbin/ipw3945d-2.6.20-12-generic /sbin/ipw3945d-2.6.20-14-386
sudo modprobe ipw3945
sudo /sbin/ipw3945d-2.6.20-14-386
```

Sabi

---

### Post by linuxgajin on 2007-04-08
Identical results as first time.

Are you confused yet, sabi? :grin:

---

### Post by sabi on 2007-04-08
Also, if you click on:

System-Administration-Update Manager

Does it show a kernel update available?

Sabi

---

### Post by linuxgajin on 2007-04-08
i had 2 updates, installed both. Neither said anything about kernel.

---

### Post by sabi on 2007-04-08
Run this command and post the results:

```
sudo cat /etc/network/interfaces
```

Sabi

---

### Post by linuxgajin on 2007-04-08
```
light@Deathnote:~$ sudo 
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

light@Deathnote:~$ 

```

---

### Post by sabi on 2007-04-08
Do you know how to use an editor, like gedit?

Try this:

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
sudo gedit /etc/network/interfaces

Insert a # sign in front of every line except the first two dealing with lo.

After you do that:

sudo /etc/init.d/networking restart

Sabi

---

### Post by linuxgajin on 2007-04-08
I'll try this tomorrow. I have to get going. I appreciate your kindness though. I'll PM you tomorrow with updates.

---

### Post by sabi on 2007-04-08
Talk with you later. I know this may be frustrating but your wireless card will work in Feisty, we just need to find the problem.

This is sort of like doing brain surgery via text messaging.

When you get back and after you modify the interfaces file.

Type this at the command line:

```
sudo lsmod | grep 3945
```

The output should look like:

```
ipw3945 124576 1
ieee80211 35272 1 ipw3945
```

Post your results...

Sabi

---

### Post by HotShotDJ on 2007-04-09
Just a word of encouragement for OP... I have the same card in my laptop and it works perfectly.  Sabi's solution is the correct one.  I wish I had happened upon this thread earlier and perhaps saved you a couple pages of hair-pulling.

---

### Post by linuxgajin on 2007-04-09
Ok I've typed in the commands; here's the results (nothing promising I'm afraid).

After typing this in I get prompted for the root password and then nothing happens.
```
light@Deathnote:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
Password:
light@Deathnote:~$ 

```

Next is this command:
light@Deathnote:~$ sudo gedit /etc/network/interfaces
This pulls up gedit automatically for me and I was able to edit the code exactly to your instructions:

```
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

Next is to restart the network. Looks like it worked ok. There was a little box that said "[OK]" but for some reason it didn't copy/paste over with the other terminal text.

```
light@Deathnote:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...    
```

Next is the grep | 3945:

```
light@Deathnote:~$ sudo lsmod | grep 3945
light@Deathnote:~$ 

```

This yields no results I'm afraid. Or at least nothing shows up in terminal. Hopefully I'll catch you online soon; I'll send you a PM incase you have email notification turned on.

---

### Post by sabi on 2007-04-09
Well, this tells us that the module is missing. This module is default in kernels 2.6.14 and newer. This development brings up several questions:

1. Did you install Feisty from CD? 
2. When did you download the iso and make the CD?
3. Have you removed any modules?

Sabi

---

### Post by linuxgajin on 2007-04-09
Yes I installed it from a CD. I downloaded/burned/used/etc the CD about 4 days ago. I don't recall removing any modules but I may have while following another guide. Would it be helpful to do a clean install from the live CD?

---

### Post by sabi on 2007-04-09
Well, it looks as if you are away for the moment. So, upon your return try the following:

```
sudo apt-get install linux-restricted-modules-generic

```

After this install, restart and try this command again:

```
sudo lsmod | grep 3945
```

As before, post the results.

Sabi

---

### Post by linuxgajin on 2007-04-09
Sorry didn't expect such a speedy reply. Here's the results:

```
light@Deathnote:~$ sudo apt-get install linux-restricted-modules-generic
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
linux-restricted-modules-generic set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sudo lsmod | grep 3945 still does nothing

---

### Post by sabi on 2007-04-09
Okay, back to the basics:

```
sudo lspci | grep 3945
```

Post the results

Sabi

---

### Post by linuxgajin on 2007-04-09
Results:
```
light@Deathnote:~$ sudo lspci | grep 3945
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

---

### Post by sabi on 2007-04-09
Okay, that tells us that the hardware is present.

Some more questions:

1. Did you disable the wireless via the keyboard (using a key sequence like Fn+ F2)?
2. Have you used the wireless on Windows on this PC?

Sabi

---

### Post by linuxgajin on 2007-04-09
1) I never intentionally disabled it; but maybe my cat walked on my keyboard when I was away and did it (not likely).

2) Card hasn't been tested on windows. I actually uninstalled windows before I really messed around with it. Card should be fine; this is brand new from Toshiba.

---

### Post by sabi on 2007-04-09
Well, back to the brain surgery analogy. I have been focused on repairing the damaged brain, but you forgot to tell me you performed heart surgery earlier and the patient is actually dead. Interesting intellectual exercise but the end result is less than satisfying.

I believe your numerous comments about reinstalling may be your subconscious telling us that something is missing from previous changes.

I hate to admit defeat. And, I am a firm believer that one should never have to reinstall to fix a problem. We have two choices:

1. Wait for someone else to come along, who can diagnose and repair the problem or ....
2. Reinstall

If you should take option 2, then I would ask that you make no changes until we start this diagnostic process again. I will be happy to assist.

I am quite confident that this wireless card will work with Feisty.

Sabi

---

### Post by linuxgajin on 2007-04-09
One of the reasons I wanted a fresh install is this: before I made some updates I would get results when I typed the grep commands in terminal. So I'm thinking if I could revert back I could give you more promising results. I'm going to boot up the live CD now and reinstall =) 

I'll update/message you when I'm done. It shouldn't take too long. Off I go.

---

### Post by sabi on 2007-04-09
Forgot to mention a few good practices to follow in general:

1. Download the release iso and check the md5sum to ensure the bit integrity.
2. Burn the the cd at a low speed (4-6x).
3. Boot up the in  "live CD mode" and select the check option from the boot menu.

Hope this helps....

Sabi

---

### Post by Krolik on 2007-04-09
Hi!
this is not problem with a hardware, I have the same problem with my Intel ipw3945 wireless card,
I try do things from this thread but it does't working too,
On v13 and v14 kernel wifi card has disapered. Linux restricted modules has been installed etc.

I'm using Asus A3FC laptop.

//edit
Now i'm using this card but on an older kernel (2.6.20-11-generic), works fine.

---

### Post by sabi on 2007-04-09
> **Krolik said:**
> Hi!
this is not problem with a hardware, I have the same problem with my Intel ipw3945 wireless card,
I try do things from this thread but it does't working too,
On v13 and v14 kernel wifi card has disapered. Linux restricted modules has been installed etc.

I'm using Asus A3FC laptop.

//edit
Now i'm using this card but on an older kernel (2.6.20-11-generic), works fine.

Thanks for the feedback.
Did the wireless card work in 2.6.20-12-generic ?

Sabi

---

### Post by sabi on 2007-04-09
> **linuxgajin said:**
> One of the reasons I wanted a fresh install is this: before I made some updates I would get results when I typed the grep commands in terminal. So I'm thinking if I could revert back I could give you more promising results. I'm going to boot up the live CD now and reinstall =) 

I'll update/message you when I'm done. It shouldn't take too long. Off I go.

Given the latest information, after you complete the reinstall, **do not perform any updates** !

We will start from the original cd image with no updates !

Are you using this iso from:

[http://releases.ubuntu.com/releases/feisty/ubuntu-7.04-beta-desktop-i386.iso](http://releases.ubuntu.com/releases/feisty/ubuntu-7.04-beta-desktop-i386.iso)

You have been very patient through all of this, so I know this is important to you!

One point I forgot to emphasize. Feisty 7.04 is beta software. As such, it is undergoing constant changes. The previous comment by Krolik illuminates this fact. One version of the kernel will work with certain hardware, only to experience a failure after a routine update. When we get your hardware working you might consider holding off on kernel upgrades until the final release on 19-April.

Sabi

---

### Post by linuxgajin on 2007-04-09
Ok I'm back with a fresh install.

uname -r reveals:

```
2.6.20-12-generic
```

I haven't run any updates.

sudo lshw -C network shows:
```
light@Deathnote:~$ sudo lshw -C network
Password:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d8000000-d8000fff irq:17
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:96:df:6c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:5000-50ff iomemory:da000000-da000fff irq:18

```

sudo ifconfig -a shows:

```
light@Deathnote:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D4:96:DF:6C  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe96:df6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1862984 (1.7 MiB)  TX bytes:250108 (244.2 KiB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

sudo iwconfig shows:

```

light@Deathnote:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Also my "restricted drivers" showed that my card was "enabled" and "in use." I hope this is a good start; I wasn't sure what other commands to run.

---

### Post by linuxgajin on 2007-04-09
heh I'm determined to never use windows again; so I appreciate your help. I understand it's beta software and the official release is just around the corner. I couldn't get any LAN to work with the other ubuntu releases so I'm sticking with this one.

I got the iso from the official ubuntu website (I made sure).

---

### Post by sabi on 2007-04-09
Just so we are on the same page ....

This is Feisty Ubuntu 7.04 and not Feisty Kubuntu, Xubuntu, right ?
This is not an alternate install, right ?

Sabi

---

### Post by linuxgajin on 2007-04-09
correct, this is the beta release of ubuntu 7.04 Feisty Fawn which was downloaded off the official website [www.ubuntu.com](www.ubuntu.com) etc etc

---

### Post by sabi on 2007-04-09
Okay, from the beginning again:

Type this at the command line:

Code:

sudo lsmod | grep 3945

The output should look like:

Code:

ipw3945 124576 1
ieee80211 35272 1 ipw3945

Post your results...

Sabi

---

### Post by linuxgajin on 2007-04-09
hurrah, results!

```
light@Deathnote:~$ sudo lsmod | grep 3945
Password:
ipw3945               118816  1 
ieee80211              34760  1 ipw3945
light@Deathnote:~$ 

```

i'm glad something happened this time :) now what? :confused:

---

### Post by sabi on 2007-04-09
If you do:

system>administration>network

Post your results

Sabi

---

### Post by linuxgajin on 2007-04-09
[http://www.imagedumpwitheasy.com/uploads/2a1406a9a7.jpg](http://www.imagedumpwitheasy.com/uploads/2a1406a9a7.jpg)

can you view this link? this is a screenshot of system > administration > network

---

### Post by sabi on 2007-04-09
cannot use the link

Do you see 3 entries:

Wireless connection
Wired connection
Modem connection

Sabi

---

### Post by linuxgajin on 2007-04-09
I see wired and modem only. There is no "wireless."

---

### Post by sabi on 2007-04-09
Try from a command line:

```
sudo modprobe -c
```

Careful, make sure -c is lowercase !

Sabi

---

### Post by linuxgajin on 2007-04-09
ok i did it... and like 500 lines of text came up (I can't past it all because terminal cut some out). But it kept spitting out lines like: alias symbol: blah blah blah

It definitely did something but I don't know what

```
alias symbol:hpsb_destroy_hostinfo ieee1394
alias symbol:genphy_config_aneg libphy
alias symbol:unregister_sound_dsp soundcore
alias symbol:nat_t120_hook nf_conntrack_h323
alias symbol:tipc_set_portimportance tipc
alias symbol:spk_serial_release speakupmain
alias symbol:ieee80211_remove_wds_addr wlan
alias symbol:sas_slave_destroy libsas
alias symbol:arpt_unregister_table arp_tables
alias symbol:alloc_irdadev irda
alias symbol:hci_send_acl bluetooth

```

i got hundreds of lines that look like that after typing in "sudo modprobe -c" (i made sure it was lowercase)

---

### Post by sabi on 2007-04-09
Okay, try:

```
sudo modprobe ipw3945
```

Post the results.

Sabi

---

### Post by sabi on 2007-04-09
Now, try:

```
sudo dmesg | grep ipw3945
```

Post the results

Sabi

---

### Post by linuxgajin on 2007-04-09
```
light@Deathnote:~$ sudo modprobe ipw3945
light@Deathnote:~$ 

```

nothing happened...:confused:

---

### Post by linuxgajin on 2007-04-09
```
light@Deathnote:~$ sudo dmesg | grep ipw3945
[   14.880000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   14.880000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.880000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.828000] ipw3945: Radio Frequency Kill Switch is On:
light@Deathnote:~$ 

```

results!?

---

### Post by sabi on 2007-04-09
> **linuxgajin said:**
> ```
light@Deathnote:~$ sudo dmesg | grep ipw3945
[   14.880000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   14.880000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.880000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.828000] ipw3945: Radio Frequency Kill Switch is On:
light@Deathnote:~$ 

```

results!?

And, finally the truth is known!

Remember, my question about the kill switch !

We need to activate the wireless. What is the keystroke sequence for doing this. Look through the manual. I fear that the key sequence will only work in Windows, but it's worth a try.

Sabi

---

### Post by linuxgajin on 2007-04-09
Well i guess this is good news then... what happens if we can't get the key sequence to work in ubuntu?

brb im gonna search the manual

---

### Post by sabi on 2007-04-09
If the key sequence doesn't work.

Reboot and enter bios setup to see if you can turn on the wireless card from there.

Sabi

---

### Post by linuxgajin on 2007-04-09
ok - is bios the same as if I had windows installed? or is it that "grub" menu I see everytime I boot up?

(still searching through my manual.... i wish I could ctrl+F through real books haha)

---

### Post by sabi on 2007-04-09
If you were dual booting, then you could simply boot into Windows, use the advertised key sequence, activate wireless. Then you shutdown Windows, reboot into Linux and the wireless card will still be activated.

If you cannot boot into Windows, then either activate via bios or ....

I will do some research on the kill function.

Sabi

---

### Post by sabi on 2007-04-09
> **linuxgajin said:**
> ok - is bios the same as if I had windows installed? or is it that "grub" menu I see everytime I boot up?

(still searching through my manual.... i wish I could ctrl+F through real books haha)

No, you would enter bios prior to the grub screen, usually through a key sequence like F2 (maybe different on your Toshiba)

Sabi

---

### Post by linuxgajin on 2007-04-09
ok i found an actual "switch" on my laptop which I didn't notice before. This seems to have turned it on. Now when I type sudo dmesg | grep ipw3945 I get this:


```
light@Deathnote:~$ sudo dmesg | grep ipw3945
[   14.880000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   14.880000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.880000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.828000] ipw3945: Radio Frequency Kill Switch is On:
[ 5484.468000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)

```

---

### Post by linuxgajin on 2007-04-09
system > adminstration > networks

now shows a "wireless" mode... now for connecting to my WPA network... I've read I may need additional installations; any idea? How do I scan for local networks?


(Funny how after everything - I forgot to turn on a simple switch on my card :chuckle: )

---

### Post by sabi on 2007-04-09
> **linuxgajin said:**
> system > adminstration > networks

now shows a "wireless" mode... now for connecting to my WPA network... I've read I may need additional installations; any idea? How do I scan for local networks?


(Funny how after everything - I forgot to turn on a simple switch on my card :chuckle: )

Ensure that the wireless entry shows roaming enabled.

Then, on the right side of the system menu bar you should see a network icon. Right click on it to ensure wireless is enabled. Then left click and you should see a list of access points to connect with.

Sabi

---

### Post by linuxgajin on 2007-04-09
I disconnected my LAN cable and I'm attempting to post wirelessly. *Crosses fingers*


*edit* Success! Thank you very much. My wireless works!

Now to work on my nvidia card drivers... for now I have to go. Thank you veryveryveryveryvery much sabi. Should I refrain from running the "282 available updates" on my notebook then? (would it mess up my settings or not be worth the risk?)

---

### Post by sabi on 2007-04-09
> **linuxgajin said:**
> system > adminstration > networks

now shows a "wireless" mode... now for connecting to my WPA network... I've read I may need additional installations; any idea? How do I scan for local networks?


(Funny how after everything - I forgot to turn on a simple switch on my card :chuckle: )

WPA Question:
If you left-click on the network icon and choose:

Connect to other wireless network

You will get a dialog box with a drop down list for wireless security, you can select WPA personal.

Sabi

---

### Post by linuxgajin on 2007-04-09
yup! i'm connected to my wpa now :) thank you very much :)

---

### Post by sabi on 2007-04-09
> **linuxgajin said:**
> I disconnected my LAN cable and I'm attempting to post wirelessly. *Crosses fingers*


*edit* Success! Thank you very much. My wireless works!

Now to work on my nvidia card drivers... for now I have to go. Thank you veryveryveryveryvery much sabi. Should I refrain from running the "282 available updates" on my notebook then? (would it mess up my settings or not be worth the risk?)

Since, we know that later kernels have problems with ipw3945, my advice would be to postpone updates until the final version is released. But, if you want to live on the wild side then update now. You are now an expert on troubleshooting wireless so you can fix it yourself after it breaks.

Good luck...
Sabi

---

### Post by linuxgajin on 2007-04-09
thanks again sabi :) now to migrate to the video card board haha

---

### Post by SDE on 2007-04-11
this thread has been a sanity check for me.  i have the EXACT same issue with my toshiba p105-s6084 / intel 3945ABG

i've spent the entire last 2 nights trying to get my wireless working ..  no joy here either.

---

### Post by SDE on 2007-04-11
ugh, .. i didn't see the last page which turned out to be the switch .. my switch is on but still have no luck.

---

### Post by zarmando on 2007-04-22
Wow. That IPW3945 is driving me nuts.

It worked once. Doesn't work anymore. Can't connect to my router, WPA.

What's up with Feisty?
It worked perfectly with PCLinux OS, Mandriva and Pardus. But, interestingly it also didn't work with Linux Mint which is based on Ubuntu.

How come it worked once, but doesn't work anymore... Haven't touched anything...????

Any advice ?

---

### Post by zarmando on 2007-04-23
Ok. I have miraculously solved my problem. Here's how I did it (and I might post the solution elsewhere) 

**** THIS WORKAROUND ONLY WORKS IF YOUR CARD IS ALREADY DETECTED, IF YOU CAN DETECT NETWORKS, etc. BUT STILL CAN'T CONNECT****

-A-
1- "Right click" on the network manager Icon
2- Enable (check) the "enable Wireless"
3- Make sure the card is ON (fn+F2 on my keyboard, Inspiron 6400 laptop)

-B-
Left click on the Icon, choose your network - It should be detected

-C-
Then
1- Disable (uncheck) the "Enable networking" option
2- re-enable (recheck) networking.

It should then connect.
If it doesn't work, retry C, retry again. Make sure the proper network is selected

Strange workaround. But it's a workaround that works...!!! At least for me.

Z.

---

