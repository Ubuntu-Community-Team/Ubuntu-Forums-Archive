---
title: "Wireless IPW2100 Not working Ubuntu 7"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by jchinyou on 2007-08-19
Hey Folks,

Im a total noob to Ubuntu and Linux in general. Either way I am having a really hard time setting up wireless on my Toshiba Tecra M2. I have tried several different things and im reallly stumpt as to what else to do. 

- On first install Ubuntu detected my wireless card as an Intel Pro 2100 (Using Centrino). However for some reason I couldnt figure out where to configure the card but then I started troubleshooting and found this...

abx@smz:~$ dmesg |grep ipw
[   18.124000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   18.124000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   18.200000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   18.324000] ipw2100: eth1: Error initializing Symbol
[   18.324000] ipw2100: eth1: Error loading microcode: -5
[   18.324000] ipw2100: eth1: Failed to power on the adapter.
[   18.324000] ipw2100: eth1: Failed to start the firmware.
[   18.328000] ipw2100Error calling register_netdev.
[   18.328000] ipw2100: probe of 0000:02:05.0 failed with error -5
abx@smz:~$ 

After finding this error here are the steps i have taken...

- downloaded latest firmware, drivers and IEEE80211 I could find on sourceforge (Not that it really mattered as they are the same version on the Ubuntu INstall)

- I extracted ieee80211 and from the extracted folder did this:
   - sh remove-old
   - said yes to all the prompts
   - make install
   - no errors came up so i assumed it was installed no problem

- Extracted the ipw2100 drivers
   - sh remove-old
   - said yes to all the prompts
   - make install
   - no errors so i assumed everything went well and that it was installed

- Extracted the firmware; now I wasnt sure where to copy the firmware to however I did this:

   - locate *.fw
   - came back all fw files were in /lib/firmware/2.6.20.15-generic 
   - copied the the firmware files to that folder

Restarted the laptop and prayed it would work....no such luck still got the same thing as I had before...Please Help me!! 

Thanks in advance!

---

### Post by jchinyou on 2007-08-22
Some more info:

root@smz:/home/abc# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@smz:/home/abc# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

root@smz:/home/abc# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

Is there any hope this will work???

---

### Post by bluefightingcat on 2007-08-29
Hi, 

It seems your IPW2100 card is not recognised. When you type iwconfig your wireless card should show up. Since its not showing up it seems your driver is not installed properly. 

Type: 

lsmod 

and see if you can find ipw2100 in the list. If its not there then type: 

modprobe ipw2100 

then it should load the required driver. Type iwconfig and see if your wireless card shows up. 

BFC

---

### Post by jchinyou on 2007-08-29
HI,

I just gave it a try and the driver does show up in the lsmod list. Thanks for the effort but the card i still a no go at this point. :(

---

### Post by inanis on 2007-09-14
I have the exact same system with the exact same problem. Toshiba Tecra M2 w/ Intel 2100 using Centrino Mobile running Feisty.   I can't figure out for the life of me why I can't get this to work. 

When I run iwconfig I don't even see the adapter listed. I do see the card listed with lspci so the system knows about it. I'm sure that the card is turned on since the M2 uses a hardware switch and not software. It worked fine in Windows before I removed it and installed Ubuntu.  

Any help would be greatly appreciated. I've been pulling my hair out over this for days. I've actually installed Ubuntu 3 different times on this thing trying to get the card to work. I've given up every single time and gone back to Windows. I'd *really* like to figure this out.

I've even tried to install the driver using ndiswrapper and while it finally let me see the wireless networks I wasn't able to connect to anything. I've since removed ndiswrapper since it didn't help.

Thanks in advance.

---

### Post by 18x on 2007-11-28
Hello I'm using Ubuntu 7.10 Gutsy and I have a Toshiba Tecra S1. 
I am having the same problem. Is this a known bug?

modprobe ipw2100 brings no console output.

Output from lsmod:
```

lsmod | grep ipw2100
ipw2100                72240  0 
ieee80211              35656  1 ipw2100

```

Output from /sys/class/firmware/timeout is "100".

Output from dmesg:
```

dmesg | grep 2100
[    0.000000] ACPI: SSDT 7FFFAA20, 029A (r1 INSYDE   GV3Ref     2000 INTL 20021002)
[ 2406.975293] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[ 2406.975297] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[ 2407.887555] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[ 2409.694681] ipw2100: eth1: Error initializing Symbol
[ 2409.694687] ipw2100: eth1: Error loading microcode: -5
[ 2409.694697] ipw2100: eth1: Failed to power on the adapter.
[ 2409.694699] ipw2100: eth1: Failed to start the firmware.
[ 2409.694716] ipw2100Error calling register_netdev.
[ 2409.695015] ipw2100: probe of 0000:02:04.0 failed with error -5

```

Firmware files are present in /lib/firmware.

I'm stuck :(

---

### Post by der_vegi on 2008-03-09
I had the same problem, having the '...error -5'. Reinstalling the kernel package linux-image-generic solved the problem for me...

---

### Post by inanis on 2008-03-25
Thanks for the reply but even after reinstalling the kernel package it didn't resolve my issue. I have also upgraded to Hardy hoping it would fix the problem, which it didn't. 

In case it helps here is the output from dmesg: 

```
dmesg |grep ipw2100

[62404.957949] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[62404.957954] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[62404.991267] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[62407.554346] ipw2100: eth1: Firmware 'ipw2100-1.3.fw' not available or load failed.
[62407.554351] ipw2100: eth1: ipw2100_get_firmware failed: -2
[62407.554353] ipw2100: eth1: Failed to power on the adapter.
[62407.554355] ipw2100: eth1: Failed to start the firmware.
[62407.554359] ipw2100Error calling register_netdev.
[62407.554907] ipw2100: probe of 0000:02:05.0 failed with error -5
```

At this point I'm fairly confident that the problem is that the card just won't power on. Here is the relevant output from lshw:

```
 *-network:0 UNCLAIMED
                description: Network controller
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64 maxlatency=34 mingnt=2
```

What I'm not sure about is if the card won't power on because of a firmware problem or because the card is just powered off. On my laptop (Toshiba Tecra M2) there is both a hardware and a software switch. I'm 100% positive that the hardware switch has it powered on (there is an indicator) I'm not sure if the software switch is causing the problem. There is nothing in the BIOS to control the wifi card. 

Any help would be appreciated. I've been trying to get this issue resolved for close to 2 years. 

If there is any other information that might be helpful please let me know.

---

### Post by maniaq on 2008-05-06
I too am having problems with ipw2100 on a Tecra S1 - running Hardy.

I'm running dual boot with XP and it seems if I try to boot either OS after linux the machine will hang (both systems will hang fairly early into the boot process) 

BUT

if I boot into Windows (safe mode because it hung last boot) then the next time I can boot EITHER Linux or XP (normal mode this time) - and if I happen to boot into Linux (which works this time) then the NEXT time I try to boot it hangs - no matter which OS I try to boot into...

Is there something Ubuntu is not doing on on shutdown that Windows is doing?

It hangs during the ACPI phase, trying to initialise ipw2100 and failing, infinitely looping (unless my last boot was XP, in which case it just goes right ahead and boots up no problems) so I'm thinking ACPI, maybe BIOS issue - but I don't know enough about either to know where to begin addressing the problem?

---

