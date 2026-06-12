---
title: "new user needs help"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by jlong07702 on 2011-07-23
Hi, 
 
I am a super-newbie.
 
Unable to get a wireless connection up and running, have read through much of the wireless threads and this seems to be a common problem.
 
Is there a list of desktop pci wireless adapters that are supported by the Ubuntu 10.10 OS and are known to function properly?
 
If so, could someone be kind enough to provide me with a link that would guide me there.
 
 
 
Thanks, Jim

---

### Post by gigenieks on 2011-07-23
Hello there!

Can't really help with wireless issue right now, but I want to add this:

Please --->
[[COLOR="Purple"]**Read this!**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")
[and this]("http://ubuntuforums.org/showthread.php?t=801404")
You should edit your topic also. 


Did you check Ubuntu documentation?

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in a terminal 
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Jepic Phail on 2011-07-24
I owned one of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315096&Tpk=EDIMAX%20EW-7128G") back in the 10.04 days and it worked out-of-the-box.

---

### Post by dcsoldschool53 on 2011-07-24
> **jlong07702 said:**
> Hi, super-newby here.
 
Unable to get a wireless connection up and running, have read through much of the wireless threads and this seems to be a common problem.
 
Is there a list of desktop pci wireless adapters that are supported by the Ubuntu 10.10 OS and are known to function properly? If so, could someone be kind enough to provide me with a link that would guide me there.
 
Thanks, Jim
I have several sites you can check:
```
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer)
``````
[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)
``````
[http://linuxhcl.com/browse/categories](http://linuxhcl.com/browse/categories)
```I hope this will help.

---

### Post by jlong07702 on 2011-07-27
Hello,
 
I've been trying very hard to respond to the request for additional information about my wireless connection problem.
 
The three previous attempts have failed.
 
Is there a time-out feature in the text editor?  If so, how long do I have to prepare my reply? 
 
When I press "Submit Reply" button it informs me that I am not logged in.
 
My internet connection is reliable and solid.
 
Is there any way to save the typed text to a draft folder where I could resume my reply if I were to lose my connection or log-in status?
 
Thanks,
Jim

---

### Post by jlong07702 on 2011-07-27
Hello,
 
This is in responce to wildmanne39's request for additional information.
 
lspci -nn | grep 0280
08:00.0 Network controller [0280]: RaLink Device [1814:3062]
 
NOTE: [0280] appeared in RED type
 
 
iwconfig
 
  lo              no wireless extensions.
 
  eth0          no wireless extensions.
 
  wlan          IEEE 802.11bgn        ESSID: off/any
                  Mode: Managed         Access Point: Not Associated      Tx-Power = 20dBm
                  Retry long limit: 7      RTS thr: off    Fragment thr: off
                  Power Management: off
 
 
rfkill list all
 
0:  phy0: Wireless LAN
soft blocked: no
hard blocked: no
 
continued in next reply....

---

### Post by Noncon on 2011-07-27
Did you install the windows drivers for the card?  If not, do this:

1. Insert your Ubuntu CD in the drive
2. Do a search on the drive for "ndis" without the "
3. You should see three Software Packages, dbl-click and install each one

Now go to System|Administration|Windows Wireless Drivers

When you run this, point it to your wireless driver .inf file or at least to the installation CD with the wireless drivers.  Not all mfg's put the drivers on the CD as an .inf, sometimes they have a setup file that will install the .inf drivers automatically.  So if the program doesn't find .inf, you may have to do a search on net to find one that will work.  

Either that, or copy the drivers from another computer (you will need both the .inf and .sys driver file if that is the case. 

KJ

---

### Post by jlong07702 on 2011-07-27
lsmod

Module Size Used by
parport_pc 26058 0
ppdev 5556 0
binfmt_misc 6599 1
snd_hda_codec_atihdmi 2411 1
snd_hda_codec_realtek 217980 1
arc4 1165 2
snd_hda_intel 22107 1
rt2800pci 8565 0
snd_hda_codec 87552 3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,
snd_hda_intel
rt2800lib 28897 1 rt2800pci
rt2x00usb 9779 1 rt2800lib
snd_hwdep 5040 1 snd_hda_codec
rt2x00pci 6029 1 rt2800pci
snd_pcm 71475 2 snd_hda_intel,snd_hda_codec
crc_ccitt 1351 1 rt2800pci
rt2x00lib 27275 4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
snd_seq_midi 4588 0
led_class 2633 1 rt2x00lib
snd_rawmidi 17783 1 snd_seq_midi
mac80211 231541 3 rt2x00usb,rt2x00pci,rt2x00lib
snd_seq_midi_event 6047 1 snd_seq_midi
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event
snd_timer 19067 2 snd_pmc,snd_seq
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,sndJ_seq
cfg80211 144470 2 rt2x00lib,mac80211
joydev 8735 0
snd 49006 11 snd_hda_codec_realtek,snd_hda_intel,
snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,
snd_seq,snd_timer,snd_seq_device
eeepc_wmi 2899 0
sparce_keymap 3145 1 eeepc_wmi
psmouse 59033 0
serio_raw 4022 0
eeprom_93cx6 1345 1 rt2800pci
intel_agp 26360 0
xhci_hcd 51737 0
lp 7342 0
soundcore 880 1 snd
snd_page_alloc 7120 2 snd_hda_intel,snd_pcm
parport 31492 3 parport_pc,ppdev,lp
agpgart 32011 1 intel_agp
usbhid 36882 0
hid 67742 1 usbhid
firewire_ohci 21106 0
firewire_core 46643 1 firewire_ohci
crc_itu_t 1383 1 firewire_core
ahci 19013 0
libahci 21667 3 ahci 
e1000e 132956 0


End of listing


Thanks, Jim

---

### Post by wildmanne39 on 2011-07-27
Hi, I suspect there is a driver conflict run this command please and post the output
```
lsmod | grep rt2
```
Thank you

---

### Post by jlong07702 on 2011-07-27
Hello,
 
Thanks for getting back to me quickly.  I appreciate the assistance.
 
 
lsmod | grep rt2
 
rt2800pci       8565         0
rt2800lib       28897        1 rt2800pci
rt2x00usb      9779        1 rt2800lib
rt2x00pci       6029         1 rt2800pci
crc_ccitt         1351         1 rt2800pci
rt2x00lib       27275        4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class         2633        1 rt2x00lib
mac80211    231541       3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211     144470       2 rt2x00lib,mac80211
eeprom_93cx6  1345      1 rt2800pci
 
Jim

---

### Post by wildmanne39 on 2011-07-27
Hi, run this command and it will open gedit.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
blacklist rt2800pci 
blacklist rt2800lib 
blacklist rt2x00usb 
blacklist rt2x00pci 
blacklist rt2x00lib 

Then unplug your wired connection and restart your system, that should do it.

---

### Post by jlong07702 on 2011-07-28
Hi,
I don't have a wired connection, does it matter?  Also after entering the blacklist commands do I need to hit enter after each or do something to terminate the program prior to restarting the system?  Sorry if I come across as being obtuse but, I am very wet behind the ears yet.  I guess the worst that could happen would be a complete re-install, I tried installing 11.04 but, had display problems so I fell back to the 10.10 version without an internet connection.
Thanks, Jim

---

### Post by wildmanne39 on 2011-07-28
Hi, no you do not need a wired connection.

Black list all the drivers as said in my previous post and then click on save then exit the program and restart your system, I am sorry I left out the save part out last night.
Thank you

---

### Post by jlong07702 on 2011-07-28
Hi wildmanne39,
 
Thank you for your time, trying to help me out, I do appreciate it.
 
I made the changes you suggested and blacklisted all the rt2* files at the end of the listing then I saved the modified version of blacklist.conf and exited and selected restart from the shutdown menu.  After the reboot I had no wireless connection.  I right clicked the Network Manager icon and there was no sign of wireless anything.  I opened a terminal session and did a iwconfig, it contained the lo and eth0 lines but not the wlan line that I was expecting.  I went back to the blacklist.conf file and put comment signs in front of the five lines that I had added, saved exited and rebooted.  I am now back to my previous condition, but still not connected to the internet.  Any suggestions at this point, if and when you get the time.  I thank you again.  Jim

---

### Post by lkjoel on 2011-07-28
> **jlong07702 said:**
> Hi wildmanne39,
 
Thank you for your time, trying to help me out, I do appreciate it.
 
I made the changes you suggested and blacklisted all the rt2* files at the end of the listing then I saved the modified version of blacklist.conf and exited and selected restart from the shutdown menu.  After the reboot I had no wireless connection.  I right clicked the Network Manager icon and there was no sign of wireless anything.  I opened a terminal session and did a iwconfig, it contained the lo and eth0 lines but not the wlan line that I was expecting.  I went back to the blacklist.conf file and put comment signs in front of the five lines that I had added, saved exited and rebooted.  I am now back to my previous condition, but still not connected to the internet.  Any suggestions at this point, if and when you get the time.  I thank you again.  Jim
Could you give us the output of these commands?
```
nm-tool
```
```
uname -a
```
```
lsb_release -a
```
```
lspci -vv
```

---

### Post by wildmanne39 on 2011-07-28
Hi, sorry about that I made a mistake black list all but the rt2x00pci then reboot with out your wired connection plugged in and see if it works then.

@lkjoel good to see thank you for the assistance.

Please do what lkjoel asked then we will go from there.
Thank you

---

### Post by jlong07702 on 2011-07-29
Friday July,29 2011


additional information for the helpful folks on the Ubuntu Forum


nmtool


NetworkManager Tool


State: disconnected


- Device: eth0 ---------------------------------------------------------------------------
Type: Wired
Driver: e1000e
State: unavailable
Default: no
HW Address: F4:6D:04:AC:E5:15


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off




- Device: wlan0 -------------------------------------------------------------------------
Type: 802.11 WiFi
Driver: rt2800pci
State: disconnected
Default: no
HW Address: C8:3A:35:CF:6D:85


Capabilities:


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Point




uname -a


Linux Mirage 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux










lsb_release -a


No LSB modules are available.
Distributor ID: Ubuntu
Discription: Ubuntu 10.10
Release: 10.10
Codename: maverick






The next command requested by @lkjoel was lspci -vv. It produces a lengthy output, since I have to type in all of this, I was wondering, is it all necessary or are you only interested in the wireless parts?
I am willing to input it all if you deem it necessary but, it may take me a while to provide it for you.


Let me know and I will comply.


Thanks,
Jim

---

### Post by lkjoel on 2011-07-30
> **jlong07702 said:**
> ...
The next command requested by @lkjoel was lspci -vv. It produces a lengthy output, since I have to type in all of this, I was wondering, is it all necessary or are you only interested in the wireless parts?
I am willing to input it all if you deem it necessary but, it may take me a while to provide it for you.
...
You don't have to type it all in. Just use Copy and Paste (select the lspci -vv output, CTRL+SHIFT+C on the Terminal window, and CTRL+V in the browser)!

---

### Post by Miljet on 2011-07-30
Since the OP has already stated that he does not have a wired connection, he obviously is working on one computer and using another to access this forum. So I reckon that he is indeed having to type in his output. Either that, or go through some jump-through-hoops of copy /pasting in a file, copying to external media, tranferring to other computer, etc.

---

### Post by jlong07702 on 2011-07-30
Hello Gentleman,

Sorry to be such a pain.  Finally broke down and relocated my router and hooked it to the new computer via ethernet cable.

This will make things much easier on my request for help.  Again I thank each of you for helping me out with my delema.

Thank you @lkjoel for giving me the cut and paste routine.

Here goes my first attempt.
jim@Mirage:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe600000-fe6fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at fe729000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 849c
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 47
    Region 0: Memory at fe700000 (32-bit, non-prefetchable) [size=128K]
    Region 1: Memory at fe728000 (32-bit, non-prefetchable) [size=4K]
    Region 2: I/O ports at f040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fe727000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8436
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 50
    Region 0: Memory at fe720000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fe500000-fe5fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe400000-fe4fffff
    Prefetchable memory behind bridge: 00000000e4000000-00000000e40fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: fe300000-fe3fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe200000-fe2fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fe100000-fe1fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fe726000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 48
    Region 0: I/O ports at f090 [size=8]
    Region 1: I/O ports at f080 [size=4]
    Region 2: I/O ports at f070 [size=8]
    Region 3: I/O ports at f060 [size=4]
    Region 4: I/O ports at f020 [size=32]
    Region 5: Memory at fe725000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 844d
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 3
    Region 0: Memory at fe724000 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at f000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Device 6779 (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 03dc
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at fe620000 (64-bit, non-prefetchable) [size=128K]
    Region 4: I/O ports at e000 [size=256]
    Expansion ROM at fe600000 [disabled] [size=128K]
    Capabilities: <access denied>

01:00.1 Audio device: ATI Technologies Inc Device aa98
    Subsystem: ASUSTeK Computer Inc. Device aa98
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 51
    Region 0: Memory at fe640000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30)
    Subsystem: ASUSTeK Computer Inc. Device 8413
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at fe500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

05:00.0 SATA controller: JMicron Technology Corp. JMB362 AHCI Controller (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 8460
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at d040 [size=8]
    Region 1: I/O ports at d030 [size=4]
    Region 2: I/O ports at d020 [size=8]
    Region 3: I/O ports at d010 [size=4]
    Region 4: I/O ports at d000 [size=16]
    Region 5: Memory at fe410000 (32-bit, non-prefetchable) [size=512]
    [virtual] Expansion ROM at e4000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30)
    Subsystem: ASUSTeK Computer Inc. Device 8413
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe300000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

07:00.0 PCI bridge: Device 1b21:1080 (rev 01) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=07, secondary=08, subordinate=08, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe200000-fe2fffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

08:00.0 Network controller: RaLink Device 3062
    Subsystem: RaLink Device 3062
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fe200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

08:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (8000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at fe210000 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at c000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

09:00.0 SATA controller: Marvell Technology Group Ltd. Device 9172 (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 8477
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 49
    Region 0: I/O ports at b040 [size=8]
    Region 1: I/O ports at b030 [size=4]
    Region 2: I/O ports at b020 [size=8]
    Region 3: I/O ports at b010 [size=4]
    Region 4: I/O ports at b000 [size=16]
    Region 5: Memory at fe110000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at fe100000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

jim@Mirage:~$ 

I would have been typing for a month LOL.

Thanks, Jim

---

### Post by wildmanne39 on 2011-07-30
Hi, run these commands please
```
lsmod | grep rt2
```
```
dmesg | grep wlan
```
```
dmesg | grep firmware
```
and post the results.
Thank you

---

### Post by jlong07702 on 2011-07-30
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

jim@Mirage:~$ lsmod | grep rt2
rt2800pci               8852  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  1 rt2800pci
rt2x00lib              27339  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231927  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144790  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2800pci
jim@Mirage:~$ 

jim@Mirage:~$ dmesg | grep wlan
[    3.589311] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jim@Mirage:~$ 

im@Mirage:~$ dmesg | grep firmware
jim@Mirage:~$

no apparent output of last command

Hope that this is somewhat helpful.

Jim

---

### Post by jlong07702 on 2011-07-30
Hi wildmanne39,

A thought just struck me, earlier today I tried to upgrade to 11.04, it failed and I had to reload 10.10 by doing so I wiped out the blacklist changes you had me do.  Should I now blacklist all the rt2 files other than the rt2800pci file?  Please advise.

Thanks,
Jim

---

### Post by wildmanne39 on 2011-07-31
Hi, just blacklist rt2x00usb then disconnect the wired connection and restart your computer.

Is there a reason you decided to install 10.10 instead of 11.04?
Thank you

---

### Post by jlong07702 on 2011-08-01
Howdy, wildmanne39

I tried your suggestion but, it didn't pan out.

During a normal eth0 boot I can see that the wireless is searching for a signal to latch onto then the icon changes to show the wired connection.  When I blacklisted rt2x00usb saved, shutdown, disconnected Cat5 on the reboot there was no indication that a wireless search was in progress.  I then went into the Network Manager and selected "find hidden wireless connection, chose my network's name and told it to connect, it eventually times out and gives me the options of connect or cancel.

Thanks,
Jim

P.S.  11.04 gives me a desktop that looks like a multi-colored verticle curtin with a 3/4" square mouse pointer that moves but, does not respond to clicks.

---

### Post by wildmanne39 on 2011-08-01
Hi, you have to make your network visible for it to connect too, also since you reinstalled ubuntu, you need to run all the commands already given so we can see what has changed in the new install otherwise we are just shooting blind.

---

### Post by jlong07702 on 2011-08-02
Hey wildmanne39,

First and foremost let me again say thank you and your colleagues for the level of dedication you show in helping others get past the difficulties of learning something new (Ubuntu).

 It is kind of you to devote the time and energy to total strangers.

It takes a special breed of person to commit to giving so much of your time and experience to help us less knowledgeable folks along the path with a helping hand.

I  appreciate and praise your efforts.  You truly are a good person.

I can't help but feel that the learning curve is too steep for me to handle, right now.

 I am going to purchase and install Windows 7 on this computer.

Perhaps, somewhere down the road I'll fool around with Ubuntu by installing it on my older desktop computer and continue the learning experience.

I'll mark this thread as "solved" before I log out.

Thanks ever so much,

Jim

---

### Post by wildmanne39 on 2011-08-02
Hi, thank you and you are very welcome! if you install ubuntu at a later date and need help just start a thread.

---

