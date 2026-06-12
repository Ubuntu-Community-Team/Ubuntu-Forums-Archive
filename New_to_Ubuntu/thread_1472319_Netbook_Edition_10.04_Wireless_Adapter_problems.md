---
title: "Netbook Edition 10.04 Wireless Adapter problems"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by dannaz94 on 2010-05-04
hi all im new to the world of linux and ubuntu.
i have installed ubuntu on to my netbook because its free. but i have ran into some problems trying to hook up to my wifi network. when i type iwconfig into terminal it says 
lo no wireless connection
eth0 no wireless connection

i know that the wireless card is working as it was perfectly fine on windows xp.

thanks in advance for anyone who can help.

---

### Post by RetchingRabbit on 2010-05-04
we will need to know what kind of wireless card you have....
in a terminal, type ```
lspci grep -i net
``` and post the output back here.

---

### Post by sb5551 on 2010-05-04
I had this problem too. I manually went into the Synaptics package manager and installed every broadcom package there was. Then rebooted the computer. I now can detect all of the networks, it just won't connect to them. 
 
You will need an ethernet hook up to download the packages though. I am using a dell mini 10n.

---

### Post by dannaz94 on 2010-05-04
when i type that code into terminal i get this


reg@Regs-Netbook:~$ lspci grep -i net
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of net
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file


i have a feeling thats not correct???

---

### Post by dannaz94 on 2010-05-04
> **sb5551 said:**
> I had this problem too. I manually went into the Synaptics package manager and installed every broadcom package there was. Then rebooted the computer. I now can detect all of the networks, it just won't connect to them. 
 
You will need an ethernet hook up to download the packages though. I am using a dell mini 10n.


ill try that

---

### Post by dannaz94 on 2010-05-04
no didnt work still cant see the adapter. forgot to mention that it was a atheros 11b/g wireless LAN mini PCI Express adapter thats what it showed up in windows as.

---

### Post by sb5551 on 2010-05-04
You can try going to the Synaptics Package manager, and search for atheros and see what packages come up. Other than that I don't I am still new at ubuntu, and still havent gotten my netbook to actually connect yet. Good Luck.

---

### Post by Animal X on 2010-05-04
> **dannaz94 said:**
> no didnt work still cant see the adapter. forgot to mention that it was a atheros 11b/g wireless LAN mini PCI Express adapter thats what it showed up in windows as.
try just the lspci without all the stuff after it.

---

### Post by dannaz94 on 2010-05-04
yeh i tried that as well no luck. good luck to yourself aswell

---

### Post by Animal X on 2010-05-04
> **dannaz94 said:**
> yeh i tried that as well no luck. good luck to yourself aswell
...you tried lspci command by itself with nothing following it?

---

### Post by rubbsdecvik on 2010-05-04
we just need to know what the output of 
```
lspci
```
is. That way we can figure out what *exact* type of network card we are dealing with.

---

### Post by dannaz94 on 2010-05-04
when i did lscpi with nothing else this is what i got.....

reg@Regs-Netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)





sorry for being such a dumbass at this but this is my first install of ubuntu

---

### Post by rubbsdecvik on 2010-05-04
No need to apologize, we all had to learn too.

Looks like you are having issues with an Atheros Card. I too am having some issues with mine but it's a different model. If I see anything on yours as I'm searching for mine, I'll let you know. Otherwise, someone here maybe able to help more. In the mean time. Try doing some google searches with 10.04 and Atheros Device 002c (rev 01) in the search terms. You may get something from that.

If I see anything I'll let you know. If I find my issue out and I have some time I'll try to help you more directly too.

~Pat

---

### Post by dannaz94 on 2010-05-04
hey pat 
i worked it out i installed ndiswrapper and installed drivers i found.
ill attach the drivers if you would like to try them on your own problem.
hope it might help.

[ATTACH]155447[/ATTACH]

---

### Post by rubbsdecvik on 2010-05-04
> **dannaz94 said:**
> hey pat 
i worked it out i installed ndiswrapper and installed drivers i found.
ill attach the drivers link if you would like to try them on your own problem.
[http://ubuntuforums.org/showthread.php?t=1369304](http://ubuntuforums.org/showthread.php?t=1369304) about the third post down is a link called ndis5x.zip. hope it might help.

Glad to hear you figured it out.

Unfortunately my chipset is different, so that exact solution won't work, but it did point me in another direction I can look, thanks.

Pat

---

### Post by josergc on 2010-05-04
Hello! 

I am right now testing the Ubuntu Netbook Edition in a EeePC 901 and having troubles with the wireless network of my house that used WPA2 personal remix + TKIP + AES. It is asking me for the password all the time.

I am testing the UNE out-of-box, booting it from an USB memory stick, I have not installed yet because I wanted to evaluate it first.

The "sudo lspci" says:
04.00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

The "dmesg" shows 
[ xxxx.xxxxxx] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[ xxxx.xxxxxx] rt2860 0000:01:00.0: PCI INT A -> GSI 19 *level, low) -> IRQ 19
...
[ xxxx.xxxxxx] === pAd = f89e3000, size = 580808 ===
...
[ xxxx.xxxxxx] <-- RTMPAllocAdapterBlock, Status=0
[ xxxx.xxxxxx] rt2860 0000:01:0.0: setting latency timer to 64
...
[ xxxx.xxxxxx] <-- RTMPAllocTxRxringMemory, Status=0
[ xxxx.xxxxxx] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[ xxxx.xxxxxx] 1. Phy Mode = 0
[ xxxx.xxxxxx] 2. Phy Mode = 0
[ xxxx.xxxxxx] RTMPSetPhyMode: channel is out of range, use first channel=1
[ xxxx.xxxxxx] 3. Phy Mode = 0
[ xxxx.xxxxxx] MCS Set = 00 00 00 00 00
[ xxxx.xxxxxx] <==== RTMPInitialze, Status=0
[ xxxx.xxxxxx] 0x1300 = 00073200
...
and a lot of messages of:
[ xxxx.xxxxxx] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 172
[ xxxx.xxxxxx] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)

Can I fix this before perform installation?

Best regards,

---

### Post by dannaz94 on 2010-05-05
no i imagine you will have to install ubuntu first

---

### Post by nukleuzN on 2010-05-05
> **dannaz94 said:**
> hey pat 
i worked it out i installed ndiswrapper and installed drivers i found.
ill attach the drivers if you would like to try them on your own problem.
hope it might help.

[ATTACH]155447[/ATTACH]

Worked like a charm on my Asus Eee PC 900! Thx!

---

### Post by Animal X on 2010-11-15
thats funny, we had the same thing going on but in reverse, atheros had to have a driver downloaded for windows to work, but ubuntu kick right in.

---

### Post by Animal X on 2011-02-13
> **dannaz94 said:**
> when i type that code into terminal i get this


reg@Regs-Netbook:~$ lspci grep -i net
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of net
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file


i have a feeling thats not correct???
your feeling is correct that its not correct, lol, u wanna pipe that lspci thru grep:

> lspci | grep -i net

---

