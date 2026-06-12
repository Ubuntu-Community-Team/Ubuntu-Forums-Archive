---
title: "I lose sound after I close my laptop lid..."
date: 2010-10-05
forum: New to Ubuntu
---

### Post by michiganitis on 2010-10-05
Ok...so I have a Compaq Presario CQ62-225NR. I have Windows 7 and Ubuntu 10.04LTS on it. Everything works fine until my computer sleeps or hibernates. Then it loses sound. Sometimes, restarting the computer doesn't even restore sound. In that case, I have to completely turn the computer off and turn it back on...or if restart into Windows 7 and restart again back in to Ubuntu, I get sound back.

I did a search on the forums...

alsa force-reload

That did nothing.

alsa-utils restart
alsa-utils rest

They also did nothing.

Any help? Thanks!

---

### Post by khelben1979 on 2010-10-06
If the problem is software related, then for starters it's good to know more in details about the hardware inside it. If the software got bugs, it would be because of bad drivers for instance, so type;```
lspci
``` from a text terminal to show us how it looks like and we'll go from there.

---

### Post by michiganitis on 2010-10-07
> **khelben1979 said:**
> If the problem is software related, then for starters it's good to know more in details about the hardware inside it. If the software got bugs, it would be because of bad drivers for instance, so type;```
lspci
``` from a text terminal to show us how it looks like and we'll go from there.

typed it...and got a whole list of stuff! hope someone can help! here's the output of lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by khelben1979 on 2010-10-07
> **michiganitis said:**
> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
You got the sound above.

You can check in your log: **/var/log/messages** what driver is getting loaded at startup. By using the modprobe command you can load any kernel module you want at any time.

```
man modprobe
``` to know more about how to use the command. Also, if you find this too difficult, you can attach your messages log file and I guess I or someone else can have a look at that. :)

---

### Post by michiganitis on 2010-10-09
> **khelben1979 said:**
> You got the sound above.

You can check in your log: **/var/log/messages** what driver is getting loaded at startup. By using the modprobe command you can load any kernel module you want at any time.

```
man modprobe
``` to know more about how to use the command. Also, if you find this too difficult, you can attach your messages log file and I guess I or someone else can have a look at that. :)

when i type i that first command, i get the following: bash: /var/log/messages: Permission denied

:(

---

### Post by Dougie187 on 2010-10-09
You want to do something like this
```
tail /var/log/messages
```

or 

```
nano /var/log/messages
```

It's just a file and typing

```
/var/log/messages
```

assumes it's an executable file and tries to run it (which of course it can't).

Something you might try doing, is after it happens try this command in a terminal

```
lshw -c multimedia
```

it should give you something like this

```
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: **driver=HDA Intel** latency=0
       resources: irq:17 memory:fe220000-fe223fff
```

If you notice the bold part, that is telling me that I have a driver loaded for my audio. You could see if you are having any issue with that.

---

### Post by dcsoldschool53 on 2010-10-09
[B]In a terminal

```
lsof | grep pcm
```

This wil show all programs connected to your sound. Kill or close all of those programs. Next, type this in the terminal.

```
sudo /etc/init.d/alsa-utils restart
```

Type in your password, and reopen a program that uses sound to test it.
[/B]

---

### Post by scrooge_74 on 2010-10-09
You should take some time and search through all threads a a couple of years back for an answer. That used to happen to people, I remember vaguely it had to to with hibernate scripts and the drivers for the sound card (even for the video card in some instances).

At present this Inspiron 1501 Im using when comming back from hibernate wil screw up the resolution and I have to either reboot or try to go to the panel and adjust the resolution till it comes back.

So do a search for hibernation utilities also, in some cases there are specific twicks for your brand and model

---

