---
title: "Netgear MA521 PCMCIA wireless solution"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by Tolaris on 2005-11-18
I can't edit the Ubuntu Wiki, which I now assume is for developers only.  Someone please change this page:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Please note under the entry for "Netgear MA521 Realtek 8180" that it works with ndiswrapper and the Windows 2000 driver.  Gentoo-specific instructions may be found here:

[http://www.linuxforum.com/forums/index.php?showtopic=134066&st=0&#entry597453](http://www.linuxforum.com/forums/index.php?showtopic=134066&st=0&#entry597453)

My Ubuntu-specific instructions (tested on Breezy 5.10 stock release):

How-To setup Netgear MA521 PCMCIA wireless card (Realtek 8180L chipset)

1. Install the necessary tools.

# apt-get install ndiswrapper

2. Download the Windows 2000 driver for the Realtek 8180L chipset.

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?software=True&compamodel=RTL8180L](http://www.realtek.com.tw/downloads/downloads1-3.aspx?software=True&compamodel=RTL8180L)

3. Unzip the file and install it with ndiswrapper.

# ndiswrapper -i NET8180.INF
Installing net8180
# ndiswrapper -l
Installed ndis drivers:
net8180 driver present, hardware present

4. Insert card, check it is recognized.
# cardctl ident
Socket 0:
   no product information
   manfid: 0x0000, 0x024c
   function: 6 (network)

5. Load the ndiswrapper kernel module.

# modprobe ndiswrapper

5.1. Add "ndiswrapper" to /etc/modules to make this change stick at boot time.

6. Verify the card is detected with dmesg.

# dmesg

ndiswrapper version 1.1 loaded (preempt=yes, smp=yes)
ndiswrapper: driver net8180 (Realtek, 07, 09, 2004, 5.170.0709.2004) loaded
PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
ACPI: PCI Interupt  0000:02:00.0 [A] -> GSI 7 (level, low) -> IRQ 7
PCI: Setting latency timer of device 0000:02:00.0 to 64
ndiswrapper using irq 7
wlan0: ndiswrapper ethernet device XX:XX:XX:XX:XX:XX using driver net8180, configuration file 10EC: 8180.5.conf
wlan0: encription modes supported WEP, WPA with TKIP, WPA with AES/CCMP

7. Setup the network in /etc/network/interfaces

iface wlan0 inet dhcp
wireless-mode managed
wireless-encryption on
wireless-essid linksys54g
wireless-key open 00112233445566778899aabbcc

8. Bring it up!

# ifup wlan0

---

### Post by kozimodo on 2005-11-30
Can't seem to get it to work...  I get
> $ ndiswrapper -l
Installed ndis drivers:
net8180 invalid driver!
Same thing if I use the Netgear driver (NETMA521.inf).  Any ideas?

---

### Post by Tolaris on 2005-11-30
Sorry, don't know why you had the problem.  Two guesses:

1. Did you download the correct Win2000 driver?  I have "ndis5x-8180(173).zip", md5sum e893ce24cb869b84da7657cb91b362f6.

2. Do you have a Netgear MA521 that uses the RealTek chipset?  I understand that some MA-series hardware is a different chipset with no easy way to tell.

Suggestion 2 is less likely.  Given that your error message is "invalid driver", it's probably the wrong file.

---

### Post by Lambert on 2005-11-30
Tolaris is correct. Make sure you're using the correct driver if you have the rtl8180 chipset.

[LIST=1]
[*]Card: Netgear MA521[LIST]
[*]Chipset: RTL8180 FCC_ID: PY3MA521
[*]Driver: [RTL8180L]("http://www.realtek.com.tw/downloads/downloads1-3.aspx?software=True&compamodel=RTL8180L") - Use the ndis5x-8180(xxx).zip driver. (NOT NETGEAR DRIVER! NETGEAR DRIVER UNSTABLE!! -- Seconded: The Netgear driver caused my machine to drop interrupts)
[*]Other: Works well even with DHCP on SUSE 9.0 Pro. 128 bit wep, managed mode. Will be trying WPA/PEAP/MSCHAP v 2 sometime later on. Check [http://hastingswireless.homeip.net/index.php?page=articles&number=2004.11.22]("http://hastingswireless.homeip.net/index.php?page=articles&number=2004.11.22") for information.  Ubuntu Hoary: Working with Ndiswrapper 1.1 - see [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto]("http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto") .[/LIST]Also make surae you copy all the files into a directory on your harddrive. .inf .sys etc... 
  [/LIST]

---

### Post by kozimodo on 2005-12-02
Thanks for the replies.  

Tolaris, I downloaded the same file.  I also tried the .inf file from netgear.

So the problem must be that I do not have the realtek chipset, is there any way to identify which one I do have?

---

### Post by juicybananahead on 2005-12-02
Hi Kozi,

Can you post the output of the following command?
```
lspci -vvv
```

---

### Post by kozimodo on 2005-12-03
[QUOTE=juicybananahead]Hi Kozi,

Can you post the output of the following command?
```
lspci -vvv
```[/QUOTE]
Sure, juicy.  It looks like the realtek chipset though... I've also attached the driver I downloaded.
```
$ lspci -vvv
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV+ VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: fc100000-fdffffff
        Prefetchable memory behind bridge: fff00000-000fffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B+

0000:00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
        Subsystem: Dell: Unknown device 009e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x20 (128 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 08000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 08400000-087ff000 (prefetchable)
        Memory window 1: 08800000-08bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
        16-bit legacy interface ports at 0001

0000:00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
        Subsystem: Dell: Unknown device 009e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x20 (128 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 08001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 08c00000-08fff000 (prefetchable)
        Memory window 1: 09000000-093ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-i f 80 [Master])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 64
        Region 4: I/O ports at 1090 [size=16]

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog- if 00 [UHCI])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin D routed to IRQ 5
        Region 4: I/O ports at 1060 [size=32]

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Interrupt: pin ? routed to IRQ 9

0000:00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
        Subsystem: Dell: Unknown device 009e
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 6000ns max)
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at 1400 [size=256]
        Capabilities: <available only to root>

0000:00:10.0 Communication controller: Lucent Microelectronics WinModem 56k (rev  01)
        Subsystem: Actiontec Electronics Inc: Unknown device 2100
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=256]
        Region 1: I/O ports at 1080 [size=8]
        Region 2: I/O ports at 1800 [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M A GP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 009e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: I/O ports at 2000 [size=256]
        Region 2: Memory at fc100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.1 1b MAC (rev 20)
        Subsystem: Netgear: Unknown device 4700
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 4000 [disabled] [size=256]
        Region 1: Memory at 08800000 (32-bit, non-prefetchable) [disabled] [size =512]
        Capabilities: <available only to root>

```

---

### Post by Jakanden on 2006-01-29
Hello,

I am having the same problem as well. I verified I am running a ReakTek chipset and when i attempt to run  ndiswrapper -l I also get "net8180 invalid driver!"

I attempted to run removal and got this:

```
root@ubuntu:~/Desktop# ndiswrapper -e NET8180.INF
Driver NET8180.INF is not installed. Use -l to list installed drivers
root@ubuntu:~/Desktop#
```

I attempt to reinstall it and get:

```
root@ubuntu:~/Desktop# ndiswrapper -i NET8180.INF
net8180 is already installed. Use -e to remove it
root@ubuntu:~/Desktop#
```

So now I am stuck in this cycle. I came across another thread that suggested using the WinXP drivers and that is why I am attempting to uninstall what is there. I have already manually deleted the contents of the /etc/ndiswrapper directory and have also completely reinstalled ndiswrapper using the package manager.

I admit that I am newbie with linux period not just ubuntu so it is quite possible (and likely probable) that this is my inexperience. 

Thanks in advance for any help!

---

### Post by direwolf on 2006-01-29
There is a link to another thread about the RTL8180 chipset below.  There is a link to a pre-compiled RTL8180 binary .deb package for i386 kernels in the thread. 

[http://ubuntuforums.org/showthread.php?t=95879](http://ubuntuforums.org/showthread.php?t=95879)

It can also be found by searching for "rtl8180".

This card (Netgear MA521) has been found to work with the drivers from sourceforge. However, those with kernels other than i386 may have to compile their own (from the CVS).
[http://rtl8180-sa2400.sourceforge.net](http://rtl8180-sa2400.sourceforge.net)

---

### Post by BiggoCharley on 2006-01-31
[QUOTE=Jakanden]Hello,

I am having the same problem as well. I verified I am running a ReakTek chipset and when i attempt to run  ndiswrapper -l I also get "net8180 invalid driver!"

I attempted to run removal and got this:

```
root@ubuntu:~/Desktop# ndiswrapper -e NET8180.INF
Driver NET8180.INF is not installed. Use -l to list installed drivers
root@ubuntu:~/Desktop#
```

I attempt to reinstall it and get:

```
root@ubuntu:~/Desktop# ndiswrapper -i NET8180.INF
net8180 is already installed. Use -e to remove it
root@ubuntu:~/Desktop#
```

So now I am stuck in this cycle. I came across another thread that suggested using the WinXP drivers and that is why I am attempting to uninstall what is there. I have already manually deleted the contents of the /etc/ndiswrapper directory and have also completely reinstalled ndiswrapper using the package manager.

I admit that I am newbie with linux period not just ubuntu so it is quite possible (and likely probable) that this is my inexperience. 

Thanks in advance for any help![/QUOTE]

I 've been watching this thread since you posted the above hoping that some one will come up with an answer. I'm experiencing exactly the same thing.  (including the "newwbie" part :confused: ) The only difference is that I'm using "sudo" to run as root because I can't seem to figure out how to get a root shell opened. (another newbie problem). I thought it might be encouraging to know that you're not alone.

---

### Post by robotgeek on 2006-01-31
[QUOTE=Tolaris]I can't edit the Ubuntu Wiki, which I now assume is for developers only.  Someone please change this page:
[/QUOTE]

No, it's not only for developers. You have to login to edit, and create a wiki account if you have don't have one.

---

### Post by Tolaris on 2006-01-31
<i>The only difference is that I'm using "sudo" to run as root because I can't seem to figure out how to get a root shell opened. (another newbie problem). I thought it might be encouraging to know that you're not alone.</i>

Try: sudo -i

Also, after default install there is no root password.  Try setting one: sudo password root

Then you can get a root prompt with: su -

---

### Post by BiggoCharley on 2006-02-01
[QUOTE=Tolaris]<i>The only difference is that I'm using "sudo" to run as root because I can't seem to figure out how to get a root shell opened. (another newbie problem). I thought it might be encouraging to know that you're not alone.</i>

Try: sudo -i

Also, after default install there is no root password.  Try setting one: sudo password root

Then you can get a root prompt with: su -[/QUOTE]

I entered "sudo password root" as you showed above but i got a "command not found" message. Do I have to be in any particular directory?

---

### Post by bscbrit on 2006-02-01
The command is 'passwd' and not 'password'.

---

### Post by ykronberg on 2007-05-20
> **kozimodo said:**
> Can't seem to get it to work...  I get

Same thing if I use the Netgear driver (NETMA521.inf).  Any ideas?

Yo, try to unistall you driver and reinstall them

---

### Post by bir7 on 2007-06-06
This HowTo works for me. Thank you for the solution.

---

