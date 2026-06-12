---
title: "No wireless after updates"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by sparkyjoe34 on 2008-07-01
Well I have seen this lately around the forum and now I too am a victim.
I updated my laptop several nights ago and I just booted my laptop today and now my wireless isn't working. The light for the wireless isn't even on. I tried [COLOR="Red"][**this**]("http://ubuntuforums.org/showthread.php?t=297092")[/COLOR] tutorial and still had no luck. I am using my laptop right now to access this forum but only because I am using a Belkin USB Wireless adapter. I'm not sure what else to do to get it working. :confused:

Could someone please help point me in the right direction to get this going?
Here are some details that I'm sure you may want:

**lspci**

```
joe@joe-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```

**iwconfig**

```
joe@joe-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"LinuxIP"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:39:E2:73:2E   
          Bit Rate=24 Mb/s   
          Link Quality=97/100  Signal level=36/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

**iwlist scan**


```
joe@joe-laptop:~$ sudo iwlist scan
[sudo] password for joe: 
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:18:39:E2:73:2E
                    ESSID:"LinuxIP"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=94/100  
                    Extra: Last beacon: 308ms ago

eth0      Interface doesn't support scanning.

```

If there is any other information you need please let me know so that I can get my computer back to how it was before. Thanks in advance for any help. :)

---

### Post by superprash2003 on 2008-07-01
you arent able to connect to "LINUXIP"?

---

### Post by sparkyjoe34 on 2008-07-01
I can't even get my wireless to work at all. Like I said earlier the light for the wireless isn't even on. When I left click on the network icons there is not even a mention of wireless networks. All it says is wired connection. When I right click it says Enable Networking, Connection information, Edit wireless connections, and About. I find it wierd that it says Edit wireless connections when it doesn't even see any wireless connections at all.

---

### Post by sparkyjoe34 on 2008-07-02
A little help please somebody.....anybody?

---

### Post by joatmon on 2008-07-04
I am having the exact same issue.  If anyone has any info, I'd really appreciate it.

As a possible workaround until this is resolved, is there a way to uninstall the last set of updates?

Thanks!

---

### Post by cytom on 2008-07-21
somewhere i read about the usb-problem of the SB600 and newer ubuntu-kernels
there a kernel-option and a bug in the SB600 were identified as the problem, so the poster compiled an own kernel with an option "USB Sleep" or so disabled

hope this helps, perhaps you can google for further help ...

---

