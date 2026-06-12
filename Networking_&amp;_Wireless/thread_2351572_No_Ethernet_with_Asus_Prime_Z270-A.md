---
title: "No Ethernet with Asus Prime Z270-A"
date: 2017-02-04
forum: Networking &amp; Wireless
---

### Post by LinuXXuniL on 2017-02-04
Hello!

I've just build a new desktop PC with Asus Prime Z270-A motherboard and I do not have internet access, looks like there is no driver for it.

Is there a way to manually install the driver for Intel I219-V Gigabit LAN?

Thanks!

---

### Post by chili555 on 2017-02-04
The necessary driver is included in all recent Ubuntu versions by default. If it didn't load as expected, there is some other problem. Please open a terminal and run and post:```
lspci -nnk | grep 0200 -A2
lsb_release -a
dmesg | grep e100
```

---

### Post by LinuXXuniL on 2017-02-04
lspci -nnk | grep 0200 -A2

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
        Subsystem: AsusTek Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
        Kernel modules : e10001

lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.1 LTS
Release: 16.04
Codename: xenial

dmesg | grep e 100

[0.776295] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[0.776295] e1000e: Copyright(c) 1999-2015 Intel Corporation
[0.830903] e1000e 0000:00:1f.6: Interrupt Throttling Rate (int/sec) set to dynamic conservation mode
[1.049935] e1000e 0000:00:1f.6: The NVM Checksum Is Not Valid
[1.084914] e1000e: probe of 0000:00:1f.6 failed with error -5

Thank you for your fast reply!

---

### Post by chili555 on 2017-02-04
>  e1000e 0000:00:1f.6: The NVM Checksum Is Not ValidAs you can see, the correct driver, e1000e, attempts to load, encounters an error and bails out. That's the 'something else is wrong' that I suspected.

The fix is a bit complex: [http://superuser.com/questions/1104537/how-to-repair-the-checksum-of-the-non-volatile-memory-nvm-of-intel-ethernet-co](http://superuser.com/questions/1104537/how-to-repair-the-checksum-of-the-non-volatile-memory-nvm-of-intel-ethernet-co)

Before we get out the plasma cutters and go full geek mode, let's take a gamble that the newer driver in 16.10 might possibly work properly. Please download the 16.10 image, make a USB or DVD and try a live session. If the ethernet works, install it and we're done! If not, check again:```
dmesg | grep e100
```If you get the same message about NVM checksum, we'll install the later driver after we amend it a bit.

---

### Post by jeremy31 on 2017-02-04
The code fix isn't in linux-next, in 4.4 source code look around line 7143 for the problem

Link to the discussion with the Intel devs
[https://sourceforge.net/p/e1000/mailman/e1000-devel/thread/A10F8704-C442-4693-8FDF-1D4956A2E1EE%40gmail.com/#msg35211176](https://sourceforge.net/p/e1000/mailman/e1000-devel/thread/A10F8704-C442-4693-8FDF-1D4956A2E1EE%40gmail.com/#msg35211176)

---

### Post by chili555 on 2017-02-04
> **jeremy31 said:**
> The code fix isn't in linux-next, in 4.4 source code look around line 7143 for the problem

Link to the discussion with the Intel devs
[https://sourceforge.net/p/e1000/mailman/e1000-devel/thread/A10F8704-C442-4693-8FDF-1D4956A2E1EE%40gmail.com/#msg35211176](https://sourceforge.net/p/e1000/mailman/e1000-devel/thread/A10F8704-C442-4693-8FDF-1D4956A2E1EE%40gmail.com/#msg35211176)Yep. I hope this will compile on the OP's 4.4 kernel. It does not on my 4.8 due to, I understand, gcc incompatibilities.

---

### Post by LinuXXuniL on 2017-02-05
Hey, thanks for your replies!

I had a look on that discussion though it is a little too complicated for me to fully understand.

As jeremy31 pointed, the problem is not dependent of kernel, it is really an error in the NVM Checksum, very annoying and I am really interested to solve this on a hard way but I will need your help cause I really don't know where to start it.

Anyway for a fast workaround and assuming the risk I've done this using bootutil:

"chmod +x ./bootutil" "sudo ./bootutil64e -NIC 1 -defcfg"This made my LAN functional and I am able to access the internet now.

On the other hand I am interested in how to solve this in a none risky way, can you please let me know what should I do?
Do you think I should buy a new Network card as well as a backup?

Thank you in advance for your help!

---

### Post by praseodym on 2017-02-05
Hi,

it seems we have the same problem on the German Forum:

[https://forum.ubuntuusers.de/topic/kein-lan-nach-installation-mainboard-asus-prim/#post-8791278](https://forum.ubuntuusers.de/topic/kein-lan-nach-installation-mainboard-asus-prim/#post-8791278)

I prepared the patched driver. Please find it attached with the amendment shown there in yellow (attached)

---

### Post by chili555 on 2017-02-05
> On the other hand I am interested in how to solve this in a none risky way, can you please let me know what should I do?I'm not at all sure that the method you used is risky. After all, it is outlined on Intel's own site: [http://www.intel.com/content/www/us/en/support/software/manageability-products/000005790.html](http://www.intel.com/content/www/us/en/support/software/manageability-products/000005790.html)

My suggestion is to use it and not worry. I see no evidence that it is likely to revert. Hasn't it survived a few reboots?

If you feel uncomfortable, PCIe gigabit cards are relatively inexpensive, so a backup may be a good investment.

---

### Post by LinuXXuniL on 2017-02-05
[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497") Thank you *praseodym *, if it ever happens again I will used the patched driver!

Hey *chili555, *it survived multiple reboots and is still working. Thank you for your help and advises, will put them to good use! 

See you around!

---

### Post by stephaneducrest on 2017-03-25
Hi all,
First post here. I just wanted to share my experience about this problem.
I just built a system with an ASUS Z270 motherboard, and I ran into the NVM checksum error.
I looked at several forums to understand what happened, and as a medium experienced Ubuntu user, I must say that compiling and installing a patched driver, or as I saw in some threads, patch the firmware of the Intel network card using ethtool, seemed rather complicated to me.
In the current thread, a user spoke about using Bootutil to solve the issue. It is exactly what worked for me, but I wanted to be more precise on how to use it, as it took me quite a while to understand what to do. 
Sorry if what I describe here seems to be like forcing open doors to some users, but I would have been happy on my side to find such a walkthrough when I walked into the problem.
First, BootUtil is the way to solve this issue with Intel e1000e NVM checksum error.
BootUtil can be downloaded from[ Intel support page]("https://downloadcenter.intel.com/download/19186/Intel-Ethernet-Connections-Boot-Utility-Preboot-Images-and-EFI-Drivers"), 
Download the Preboot.tar.gz file.
I used an USB key to move the file from one computer that has internet access to my ubuntu "wounded" computer without network access.
I extracted this archive, and put myself in the directory where bootutil64e is present.
I had to make the file executable using
sudo chmod +x bootutil64e
Then I ran bootutil64e without parameter, to see if my network card would be detected. It was, showing an ID of 1.
So I ran
sudo bootutil64e -NIC 1 -defcfg
to reload my network card with a default configuration.
This action seemed to force the card to compute again the checksum, and my network was activated (I don't remember if I had to restart the network or not).
Intel cautions to use this tool at your own risk, which I suppose is normal legal language. But on my side it worked, and after 2 hours of research I was quite happy to find a solution.
I hope it will help those that will meet the same problem.
See you around.

---

### Post by ship22 on 2017-04-06
> **LinuXXuniL said:**
> Hey, thanks for your replies!


"chmod +x ./bootutil" "sudo ./bootutil64e -NIC 1 -defcfg"This made my LAN functional and I am able to access the internet now.



I have this problem too but running this command didn't get it working for me. Tried running it and rebooting, running it then restarting network-manager, eth0 still wont' come up. Am I missing something painfully obvious to everyone else? Windows10 uses the net device fine.

I have no clue what to do with the patched driver [COLOR=#000000]praseodym posted.

[/COLOR]

---

### Post by chili555 on 2017-04-06
> **ship22 said:**
> I have this problem too but running this command didn't get it working for me. Tried running it and rebooting, running it then restarting network-manager, eth0 still wont' come up. Am I missing something painfully obvious to everyone else? Windows10 uses the net device fine.

I have no clue what to do with the patched driver [COLOR=#000000]praseodym posted.

[/COLOR]Do you have the exact same device and the exact same symptoms?```
lspci -nnk | grep 0280 -A2
dmesg | grep e100
```

---

### Post by ship22 on 2017-04-06
> **chili555 said:**
> Do you have the exact same device and the exact same symptoms?```
lspci -nnk | grep 0280 -A2
dmesg | grep e100
```

lspci -nnk|grep 0200 -A2
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (5) I219-V [8086:15d6]
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (5) I219-V [1043:8672]
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b81] (rev a1)

did you mean 0200? the initial request in the thread was for 200, not 280.. assumed a typo since that command didn't return anything.
Also the dmesg|grep e100 didn't return anything.

Thank you for any insight.

---

### Post by chili555 on 2017-04-07
> **ship22 said:**
> lspci -nnk|grep 0200 -A2
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (5) I219-V [8086:15d6]
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (5) I219-V [1043:8672]
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b81] (rev a1)

did you mean 0200? the initial request in the thread was for 200, not 280.. assumed a typo since that command didn't return anything.
Also the dmesg|grep e100 didn't return anything.

Thank you for any insight.The driver e1000e is correct for your device and isn't loaded. Let's try to see why:```
sudo modprobe e1000e
dmesg | grep e100
```I suspect that some interesting errors, warnings, etc. may appear.

Quite correct; I meant 0200. Sorry for my misstep.

---

### Post by ship22 on 2017-04-07
> **chili555 said:**
> The driver e1000e is correct for your device and isn't loaded. Let's try to see why:```
sudo modprobe e1000e
dmesg | grep e100
```I suspect that some interesting errors, warnings, etc. may appear.

Quite correct; I meant 0200. Sorry for my misstep.

thank you for your help!

# modprobe e1000e
# dmesg|grep e100
[   849.594379] e1000e: Intel(R)  PRO/1000 Network Driver - 3.2.6-k
[   849.594381] e1000e: Copyright(c)  1999 - 2015 Intel Corporation.

---

### Post by chili555 on 2017-04-08
That's cra-crazy! The driver should have grabbed your device and taken off! Let's see what is going on (wrong??) on the PCI bus:```
dmesg | grep 1f.6
```

---

### Post by ship22 on 2017-04-08
> **chili555 said:**
> That's cra-crazy! The driver should have grabbed your device and taken off! Let's see what is going on (wrong??) on the PCI bus:```
dmesg | grep 1f.6
```

dmesg|grep 1f.6
[    0.211908] pci 0000:00:1f.6: [8086:15d6] type 00 class 0x020000
[    0.211939] pci 0000:00:1f.6: reg 0x10: [mem 0xdf300000-0xdf31ffff]
[    0.212017] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.212077] pci 0000:00:1f.6: System wakeup disabled by ACPI

---

### Post by chili555 on 2017-04-08
I have been Googling this for hours and I have no answer. Your driver clearly supports the device:```
chili@T440p:~$ modinfo e1000e | grep -e version -e 15D6
version:        [COLOR="#FF0000"]3.2.6-k[/COLOR]
srcversion:     A4EDE14B922EB1F645AD8AF
alias:          pci:v00008086d0000[COLOR="#FF0000"]15D6[/COLOR]sv*sd*bc*sc*i*

```Here is your device:> 00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (5) I219-V [8086:[COLOR="#FF0000"]15d6[/COLOR]]
Subsystem: ASUSTeK Computer Inc. Ethernet Connection (5) I219-V [1043:8672]And you have the same driver version:> [ 849.594379] e1000e: Intel(R) PRO/1000 Network Driver - [COLOR="#FF0000"]3.2.6-k[/COLOR]As to why yours doesn't start and run, I haven't any idea. I deeply regret that I have no other suggestions.

By any chance, is the BIOS fully updated?

---

### Post by ship22 on 2017-04-08
> **chili555 said:**
> I have been Googling this for hours and I have no answer. Your driver clearly supports the device:```
chili@T440p:~$ modinfo e1000e | grep -e version -e 15D6
version:        [COLOR=#FF0000]3.2.6-k[/COLOR]
srcversion:     A4EDE14B922EB1F645AD8AF
alias:          pci:v00008086d0000[COLOR=#FF0000]15D6[/COLOR]sv*sd*bc*sc*i*

```Here is your device:And you have the same driver version:As to why yours doesn't start and run, I haven't any idea. I deeply regret that I have no other suggestions.

By any chance, is the BIOS fully updated?

thank you so much for checking, I was pretty lost on what to try. I'll check the bios.. if that doesn't work I guess I'll try to get a compatible nic

---

### Post by chili555 on 2017-04-08
> I'll check the bios.. if that doesn't work I guess I'll try to get a compatible nicPerfect.

Although I wonder how effective it may be, you might also try contacting Asus about this. Feel free to refer them to this thread.

---

### Post by djchapm on 2017-12-01
Hey everyone - Want to relay my experience too - the bootutil64e worked for me as well (sudo ./bootutil64e -NIC 1 -defcfg).  I have the Asus Z270-CODE mobo but my adapter matches.
Wanted to show people the output of bootutil64e because it tells me there's no flash etc so I thought I had a diff situation.  Even after running the util, still says no flash.  But all is good and you have to restart after you do it.
My info follows - which I did** after** the reboot:
**djchapm@covert:~$ dmesg |grep e100**
[    0.911766] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.911767] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.977070] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.183446] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    1.250392] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 2c:4d:54:4e:33:2f
[    1.250392] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.250498] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    1.250876] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[    6.353247] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
**djchapm@covert:~$ lspci -nnk | grep 0200 -A2**
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
	Kernel driver in use: e1000e
**djchapm@covert:~$ lsb_release -a**
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

BEFORE I ran defcfg - the bootutil identified my network adapter at least... but now after the restart, and with the adapter working fine, it shows this which looks bad:
djchapm@covert:~/Install/IntelBootUtil/APPS/BootUtil/Linux_x64$ sudo ./bootutil64e 
[sudo] password for djchapm: 
Connection to QV driver failed - please reinstall it!


Intel(R) Ethernet Flash Firmware Utility
BootUtil version 1.6.56.0
Copyright (C) 2003-2017 Intel Corporation


Type BootUtil -? for help


Port Network Address Location Series  WOL Flash Firmware                Version
==== =============== ======== ======= === ============================= =======
  1   (Cannot initialize adapter)


SO - now it seems this bootutil64e can't connect or do anything - but Linux is happy and as you saw above it is working great.

--
Also - I thought I'd use the "SAVEIMAGE" option before running defcfg to be safe - but as it was reporting no flash firmware, it said it couldn't save anything.

Hope this helps.

Dan C.

---

