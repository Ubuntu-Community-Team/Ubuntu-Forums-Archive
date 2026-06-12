---
title: "Frusterating Wireless"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Sherman901 on 2006-12-03
I have tried Linux multiple times and each time I come back to it it keeps reminding me why I gave it up in the first place. When I saw Ubuntu I thought, hey, this looks like an easy to use Linux OS, but of course, silly me, it's not.

I cannot figure out how to get my wireless network to work. I can't get my card working, I've tried that silly ndiswrapper thing and I can't even get it installed in the package manager. I am so terribly frusterated I just can't understand how anyone can enjoy using this. Can someone please help me with getting my wireless working? I've tried reading documentation, I've tried reading through these forums and it doesn't help my situation at all.

My wireless card is a D-Link DW-G520.. please, anyone, help me.

---

### Post by spd106 on 2006-12-03
Please read through this wiki page [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and see if it helps. It might be worth providing a few more details such as which type of card you have and which chipset.

---

### Post by FrodoB on 2006-12-03
Publish the output of:

lspci -v

iwconfig

Also remove the card from the system and reboot. After reboot and login insert the card and run dmesg and provide the end part that contains the information for your wireless card.

---

### Post by Sherman901 on 2006-12-03
jordan@jordan-desktop:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at ec00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at ed003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        Memory at ed004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at ed005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at ed000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at a800 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7585
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        I/O ports at ac00 [size=256]
        I/O ports at b000 [size=128]
        Memory at ed001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at cc00 [size=16]
        I/O ports at d000 [size=128]
        Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0250
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at e400 [size=16]
        I/O ports at e800 [size=128]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: eb000000-ecffffff
        Prefetchable memory behind bridge: 50000000-500fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device a343
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-Link AirPlus DWL-G520 Wireless PCI Adapter(rev.B)
        Flags: bus master, medium devsel, latency 168, IRQ 217
        Memory at ec000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: Unknown device 0574:086c
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at ec011000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 9000 [size=128]
        Capabilities: <access denied>

02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 025c
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 225
        I/O ports at 9400 [size=256]
        Memory at ec010000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

jordan@jordan-desktop:~$ iwconfid
bash: iwconfid: command not found
jordan@jordan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

---

### Post by FrodoB on 2006-12-03
You have an Atheros card, this is lucky, it should just work.

To get this thing going with WEP you just need to go to the:

System -> Adminstration -> Networking 

menu and fill out and activate the card.

after you are through you should have a record in /etc/network/interfaces that looks like this for the device:

iface ath0 inet dhcp
wireless-essid Your_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto ath0


This example shows a 128bit WEP key in Hex format. If you want to use  an ASCII key it must be 13 characters proceeded by  "s:" like this:

wireless-key s:XXXXXXXXXXXXX

Good luck, you seem to be close.

---

### Post by Sherman901 on 2006-12-03
> **FrodoB said:**
> You have an Atheros card, this is lucky, it should just work.

To get this thing going with WEP you just need to go to the:

System -> Adminstration -> Networking 

menu and fill out and activate the card.

after you are through you should have a record in /etc/network/interfaces that looks like this for the device:

iface ath0 inet dhcp
wireless-essid Your_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto ath0


This example shows a 128bit WEP key in Hex format. If you want to use  an ASCII key it must be 13 characters proceeded by  "s:" like this:

wireless-key s:XXXXXXXXXXXXX

Good luck, you seem to be close.

It still doesn't seem to be working. I've got all my information correct. I just don't get it. I wish it would be more clear as to what is wrong and why.

---

### Post by FrodoB on 2006-12-03
Publish what you have in your interfaces file.

The output of iwconfig and iwlist:

sudo iwconfig

sudo iwlist ath0 scanning

and the dmesg output one more time.

Also how is your access point setup: wep broadcasting the SSID etc. You may want to turn off all security while you are debugging as WEP keys are usually the problem at this point.

---

### Post by Sherman901 on 2006-12-03
Turning off my wireless security definitely worked. I'm posting from Ubuntu now, but now on to the next step of getting it to work with security. I don't use WEP, I tried it and it crashed my router. I use P2K Personal or something along those lines.

interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto wlan0
iface wlan0 inet dhcp


iface ath0 inet dhcp
wireless-essid linksys
wireless-key s:

auto ath0


iwconfig:

ath0      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:D1:26:4F   
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/94  Signal level=-56 dBm  Noise level=-95 dBm
          Rx invalid nwid:106  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath0 scanning:

    Scan completed :
          Cell 01 - Address: 00:16:B6:D1:26:4F
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:39:72:3F:08
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

THanks so much for the quick replies, I really appreciate it.

---

### Post by FrodoB on 2006-12-03
OK, I have never done anything beyond WEP, so you may just want to start a new thread asking for assistance  with WPA-PSK, which is what I think you are saying.

I believe that the wpasupplicant site covers what you need to do:

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

Good luck and thanks for your patience.

---

### Post by Sherman901 on 2006-12-03
> **FrodoB said:**
> OK, I have never done anything beyond WEP, so you may just want to start a new thread asking for assistance  with WPA-PSK, which is what I think you are saying.

I believe that the wpasupplicant site covers what you need to do:

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

Good luck and thanks for your patience.

Thank *you* for the help!

---

