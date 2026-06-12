---
title: "USB Nano USB Wireless adapter installation"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by vs-punn on 2014-02-21
Ubuntu version: 13.10 (desktop)

I have bought a USB nano Wireless Adapter for my desktop. The Chipset is Rallink V2.5  .
In terminal I gave thecommand lsusb and the usb adapter was shown as:
Bus 002 Device 006: ID 148f:7601 Ralink Technology, Corp.

How do i configure the adapter to make it work.

---

### Post by varunendra on 2014-02-21
> **vs-punn said:**
> Bus 002 Device 006: ID **[COLOR="#0000CD"]148f:7601[/COLOR]** Ralink Technology, Corp.

This is a very new device and apparently no native linux driver yet supports it. However, a supporting proprietary driver is available on Ralink's official site. So we may try compiling it and see if it works.

Please follow these instructions to compile and install it -

First of all, make sure the basic components required to compile the driver are available in the system. While being connected to internet via cable or other means, please run the following code in a terminal to ensure that -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Then,

[INDENT]**1)** Download the "**MT7601U USB**" package from Ralink's official site here : [http://www.mediatek.com/en/downloads/mt7601u-usb/](http://www.mediatek.com/en/downloads/mt7601u-usb/)
**2)** Right-click the downloaded package (DPO_MT7601U_LinuxSTA_3.0.0.4_20130913.tar.bz2) > "Extract here..."
**3)** Assuming this extracted directory is in the "**Downloads**" directory within your **Home** directory, open a terminal (Ctrl-Alt-T) and run the following commands one-by-one (you may copy-paste them) to compile and install the driver -
```
cd Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
make
sudo make install
```
Watch out for errors and report back if there are any. Warnings can usually be safely ignored.
**4)** If the wireless doesn't automatically turn on after this, either reboot, or manually load the driver -
```
sudo modprobe -v mt7601Usta
```[/INDENT]

Does the wifi work now? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mtalha91 on 2014-09-04
I am also having this problem. I have generated the script and here is the output:



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


mtalhas 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory : 2007 MB
Uptime : 16:59:21 up 17 min,  3 users,  load average: 0.14, 0.40, 0.43




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


01:0c.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
	Subsystem: Dell Optiplex GX270 [1028:0151]
	Kernel driver in use: e1000




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 004: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1d57:0007 Xenta 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








module parameters ~~~~~~~~~~~~~~~~~~




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | e1000  | connected | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.243/0.299/0.355/0.056 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.037/0.052/0.068/0.017 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : en_PK.UTF-8)
country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x100e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=fa633c3b-598c-4d24-9224-e15ab2f08000 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.033373] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.033842] audit: initializing netlink socket (disabled)
[   22.229068] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


	======== Done ========

---

### Post by chili555 on 2014-09-04
> **mtalha91 said:**
> I am also having this problem. I have generated the script and here is the output:
<snip>
lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 004: ID 148f:7601 Ralink Technology, Corp. 
I know of no way to get this device working in 14.04. You might get the device working in 12.04 using a 3.2.0-xx kernel and I can't emphasize too much: *might*.  The package referred to above won't compile on 14.04; I know, I have attempted it myself in the last few days. The version on github is essentially the same. The most recent stable backports package, 3.16.1, does not contain the driver.

You might also send or take it back where it came from and trade it for a known working device. There are several threads on working USB wireless in this forum.

There are very few devices that I'd call unsuitable, at this time, for Ubuntu, but this is one. It may change in the future.

---

### Post by yago2 on 2014-09-07
Had the same problem and finally could find a solution after four days of trouble.
I'm running Kubuntu 14.04 on a Dell OptiPlex 760.

lsusb gives out following information:
```
Bus 001 Device 021: ID 148f:7601 Ralink Technology, Corp. 
```

I followed this instructions and am now writing using my wifi dongle:
[http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation)

Hope I could help someone with the same problem.

---

### Post by IQAndreas on 2014-10-20
> **varunendra said:**
> Download the "**MT7601U USB**" package from Ralink's official site here : [http://www.mediatek.com/en/downloads/mt7601u-usb/](http://www.mediatek.com/en/downloads/mt7601u-usb/)

It's **really** suspicious when you say "download from *Ralink's official site*", but then link to a Tiwanese company's website (and every website looks shady when you are asked to trust in them and download a binary from it).

After some digging, I found that [MediaTek is the parent company of Ralink]("http://en.wikipedia.org/wiki/MediaTek#Ralink"), so my suspicions are relieved, but you my want to adjust your wording or incorporate that information into your post.

---

### Post by varunendra on 2014-10-22
Those who are too innocent or careless won't care anyway, and those who do care like you will figure it out by themselves like you did.

Any method to search for the "Official" Ralink drivers from an authentic source will eventually lead to the same link I gave, so I don't think adjusting the wording is going to make any difference for anybody.

---

### Post by wireguy2 on 2015-01-20
I am Having an issue getting the code to compile make spits out:

make -C tools
make[1]: Entering directory `/home/kevin/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kevin/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/home/kevin/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /home/kevin/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.2.0-70-generic/build SUBDIRS=/home/kevin/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make: *** /lib/modules/3.2.0-70-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


can someone please tell me what i did wrong? I installed linux-headers-generic and build-essential with out an issue.

---

### Post by chili555 on 2015-01-21
Your error is a sign that linux-headers are not installed or not installed correctly. Check:```
sudo dpkg -s linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~. We hope we see:```
Status: install ok installed
```If not, try:```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall linux-headers-generic
```And try again.

If it still isn't working, we will have another suggestion.

---

### Post by wireguy2 on 2015-01-21
thank you the headers where the issue and with your advise i was able to make it past that point it's all working now

---

### Post by JZach on 2015-07-28
I followed the same instructions and got the device working. Thank you for the hint.

However I encountered one problem: Radio streaming was interrupted every 5 minutes. I figured out that it comes from a network scan, which is started by the driver if the activity is "low", which is set by some transmission statistics to "70" hardcoded in the source code, see below. However an audio stream only produces something like "12" in these units. Setting the limit to "5" in the source code and recompiling solved the problem. 

I hope this helps, if someone has the same problem. And here is the patch:
```
--- common/mlme.c~      2015-07-29 01:20:21.000000000 +0200
+++ common/mlme.c       2015-07-29 01:20:21.000000000 +0200
@@ -1538,7 +1538,7 @@
                /* Check traffic is less than about 1.5~2Mbps.*/
                /* it might cause data lost if we enqueue scanning.*/
                /* This criteria needs to be considered*/
-               if ((pAd->RalinkCounters.LastOneSecTotalTxCount < 70) && (pAd->RalinkCounters.LastOneSecRxOkDataCnt < 70))
+               if ((pAd->RalinkCounters.LastOneSecTotalTxCount < 5) && (pAd->RalinkCounters.LastOneSecRxOkDataCnt < 5))
                {
                        MLME_SCAN_REQ_STRUCT            ScanReq;
                        /* Fill out stuff for scan request and kick to scan*/

```

---

### Post by chili555 on 2015-07-29
> **JZach said:**
> I followed the same instructions and got the device working. Thank you for the hint.

However I encountered one problem: Radio streaming was interrupted every 5 minutes. I figured out that it comes from a network scan, which is started by the driver if the activity is "low", which is set by some transmission statistics to "70" hardcoded in the source code, see below. However an audio stream only produces something like "12" in these units. Setting the limit to "5" in the source code and recompiling solved the problem. 

<snip>Awesome! We appreciate your expertise. We also appreciate that you shared it with the community.

---

### Post by batko_marto on 2015-12-04
I just found that there is a ppa that has the driver that you need. See here: [https://code.launchpad.net/~thopiekar/+archive/ubuntu/mt7601](https://code.launchpad.net/~thopiekar/+archive/ubuntu/mt7601)
I just did the installation from there and it works like a charm.

---

### Post by JZach on 2015-12-30
I have checked the source code of this ppa and found that the problematic code, which interrupts connections with low traffic rate, is still in. So you will need to apply the patch from my previous post and rebuild the package, if you want to ensure uninterrupted audio streaming.

Joachim Zach

---

