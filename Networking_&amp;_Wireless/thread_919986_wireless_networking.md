---
title: "wireless networking"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by iriptan on 2008-09-14
Hi, this is my first time to use xubuntu and i need help in wireless networking. i can browse the internet using wired connection but i can't use wireless connection because the radio is off. can anybody help me on this? my old laptop is fujitsu siemen amilo m7400. thanks

---

### Post by pytheas22 on 2008-09-14
Please open up a terminal (it's located under the main menu, although I can't tell you where exactly because it's been a while since I used Xubuntu), run these commands and post the output here:
```

lshw -C Network
lspci -nn
dmesg | grep -e radio -e Radio -e wlan -e eth1
uname -m
```

With that information we can diagnose the problem better.

---

### Post by iriptan on 2008-09-15
This is the output of the commands:

papa@lorenzo-laptop:~$ lshw-c network
bash: lshw-c: command not found
papa@lorenzo-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:25:9d:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.5 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:1c:82:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
papa@lorenzo-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 61)
02:05.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
02:09.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
papa@lorenzo-laptop:~$ dmesg | grep -e radio -e Radio -e wlan -e eth1
[   49.076082] ipw2200: Radio Frequency Kill Switch is On:
[   52.958811] ADDRCONF(NETDEV_UP): eth1: link is not ready
papa@lorenzo-laptop:~$ uname -m
i686
papa@lorenzo-laptop:~$ 
papa@lorenzo-laptop:~$

---

### Post by pytheas22 on 2008-09-15
Yeah, the problem is definitely the radio--everything else looks fine.  Do you have a button to turn the wireless card on, or do you press a special key combination (something like function+F2)?  If so, please try toggling the wireless on that way.  Do it a few times, and after each each try, please run these commands and post the output:
```

iwlist scan
dmesg | tail
```

---

### Post by iriptan on 2008-09-15
Yes, there is a dedicated button for turning on the wifi. I tried it a few times and it always have this same response:

papa@lorenzo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

papa@lorenzo-laptop:~$ dmesg | tail
[   38.108180] Bluetooth: RFCOMM socket layer initialized
[   38.108196] Bluetooth: RFCOMM TTY layer initialized
[   38.108198] Bluetooth: RFCOMM ver 1.8
[   41.204263] eth0: no IPv6 routers present
[   41.211984] [drm] Initialized drm 1.1.0 20060810
[   41.215380] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.215390] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.215458] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.215468] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   41.215515] [drm] Initialized i915 1.6.0 20060119 on minor 1
papa@lorenzo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

papa@lorenzo-laptop:~$ dmesg | tail
[   38.108180] Bluetooth: RFCOMM socket layer initialized
[   38.108196] Bluetooth: RFCOMM TTY layer initialized
[   38.108198] Bluetooth: RFCOMM ver 1.8
[   41.204263] eth0: no IPv6 routers present
[   41.211984] [drm] Initialized drm 1.1.0 20060810
[   41.215380] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.215390] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.215458] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.215468] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   41.215515] [drm] Initialized i915 1.6.0 20060119 on minor 1
papa@lorenzo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

papa@lorenzo-laptop:~$ dmesg | tail
[   38.108180] Bluetooth: RFCOMM socket layer initialized
[   38.108196] Bluetooth: RFCOMM TTY layer initialized
[   38.108198] Bluetooth: RFCOMM ver 1.8
[   41.204263] eth0: no IPv6 routers present
[   41.211984] [drm] Initialized drm 1.1.0 20060810
[   41.215380] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.215390] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.215458] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.215468] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   41.215515] [drm] Initialized i915 1.6.0 20060119 on minor 1
papa@lorenzo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

papa@lorenzo-laptop:~$ dmesg | tail
[   38.108180] Bluetooth: RFCOMM socket layer initialized
[   38.108196] Bluetooth: RFCOMM TTY layer initialized
[   38.108198] Bluetooth: RFCOMM ver 1.8
[   41.204263] eth0: no IPv6 routers present
[   41.211984] [drm] Initialized drm 1.1.0 20060810
[   41.215380] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.215390] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.215458] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.215468] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   41.215515] [drm] Initialized i915 1.6.0 20060119 on minor 1
papa@lorenzo-laptop:~$

---

### Post by pytheas22 on 2008-09-15
It looks like the radio switch doesn't do anything at all.  Is there an option in your BIOS regarding the radio on the wireless card?  Please check there to see if there's a way to turn the radio permanently on, or to tell it to be controlled by an application instead of the button.  The posters [here]("http://ubuntuforums.org/showthread.php?t=680256") had an issue with your wireless driver that they solved that way.

---

### Post by iriptan on 2008-09-15
There are two options in the bios for the wireless networking, I put on enabled and it still does not work.
Thanks

---

### Post by Red-Shield on 2008-09-15
please give the iwconfig when you try using the button it will output if the card is on/off see my example post your results:

sick-****@linuxuser:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      **[COLOR="Navy"]radio off[/COLOR]**  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by pytheas22 on 2008-09-15
Yes, please provide the iwconfig output as mentioned in the post above, as well as the output of:

```
iwlist scan
dmesg | grep -e ipw -e radio -e Radio
```

Also what specifically did BIOS say about enabling the radio?  Were the options 'always on' or 'turn on by switch' or something?  What state does BIOS say it's in now?

---

### Post by iriptan on 2008-09-16
This is the output:

papa@lorenzo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

papa@lorenzo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

papa@lorenzo-laptop:~$ iwlistscan
bash: iwlistscan: command not found
papa@lorenzo-laptop:~$ dmesg | grep -e ipw -e radio -e Radio
[   26.570146] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.570150] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.801110] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   29.800510] ipw2200: Radio Frequency Kill Switch is On:
[   29.901983] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
papa@lorenzo-laptop:~$ 

in the Bios:

default wireless device:enabled (select default device when system boots up)

---

### Post by iriptan on 2008-09-16
i found something on the internet here:
[http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/](http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/)

i follwed what he did

sudo modprobe fsam7400 radio=1

then 

iwlist and this is what i got:

papa@lorenzo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:68:6B:FD:D5
                    ESSID:"O2wireless1A6B30"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 1948ms ago
          Cell 02 - Address: 00:18:F6:5D:BA:5F
                    ESSID:"BTHomeHub-6E5F"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    Extra: Last beacon: 0ms ago
          Cell 03 - Address: 00:01:38:A8:4F:77
                    ESSID:"enzo"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-47 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 108ms ago
          Cell 04 - Address: 00:18:4D:61:77:DA
                    ESSID:"joanna"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=76/100  Signal level=-53 dBm  
                    Extra: Last beacon: 944ms ago
          Cell 05 - Address: 00:18:4D:B0:7D:78
                    ESSID:"SKY19403"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4348ms ago

the netwrok are showing but i still cant connect to them wirelessly, 
when i go to network list there's nothing there.

---

### Post by pytheas22 on 2008-09-16
That's good news that you can see the networks at least from the command line.  Did you try waiting a few seconds to see if they show up in Network Manager (the graphical connection manager utility)?  They don't always appear right away.  You may also want to try using [wicd]("http://wicd.sourceforge.net") instead of NM to connect.

If that doesn't help, tell me the name of your network and I'll give commands so that you can try to connect from the command line.

---

### Post by iriptan on 2008-09-16
It worked already. I changed from xubuntu to ubuntu, when i click on network options i can see the wireless network available. thanks for all your help.:):)

---

### Post by stui_7@hotmail.com on 2008-11-24
Hi!

i Don't know if this might help...

on my amilo m7400 the wifi **_will_**not work unless the hotbuttons driver is load......
driver awaileble from fujitsu

---

