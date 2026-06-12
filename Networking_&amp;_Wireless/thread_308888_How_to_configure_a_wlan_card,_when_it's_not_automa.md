---
title: "How to configure a wlan card, when it's not automatically recognised by Ubuntu?"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by naelivent on 2006-11-28
Hi!
I'm a kind of newbie to Linux. Now, as I read the forums and menuals, things are getting clear, but there are still some things that I'm uincertain in.
My main problem, that I couldn't solve yet is with my Wlan card. I'm having a card (Called SMCWPCI-G) and I simply cannot get it work. I've been reading for solutions, but whatever I tryed, I failed it, and I'm not sure, if it's my fault (my English ain't perfect, maybe I misunderstood things), or my system is so special - beside this card, my processor is an Athlon 64bit 3000+. (Now I decided to stay at Ubuntu linux, 6.10, amd64 version.)
So, generally, could someone summarize, what to do with this kind of situation?
I'v tried to set up madwifi, but the installation procedure stopped. I've tried to install networkManager, but I couldn't get it run. I haven't tried Ndiswrapper yet, do you think it would work with a 32 bit driver, when the linux is installed as 64bit? (Win XP x64 driver doesn't exsist, neighter.)
What would be the default thing to do, when the manufacturer hasn't come out with the linux driver?

---

### Post by cmichaelboyd on 2006-11-28
I'm not sure if that card is supported natively under linux or not....if it is, then you don't need ndiswrapper.  could you open up a terminal and type 

lspci -v

and copy and paste the output here

---

### Post by angryfirelord on 2006-11-28
I have the same card that runs fine under 32-bit Edgy. Try System-->Administration-->Networking and see if the card shows up or is activated. Use DHCP.

You shouldn't have to install madwifi because Ubuntu already has an Atheros driver. Give it a **modprobe ath_pci** (might have to use sudo) and if it loads, type **dhclient ath0**.

If all else fails, try 32-bit Edgy. There's no real advantage to 64-bit Operating Systems right now anyway.

---

### Post by FrodoB on 2006-11-28
The only time you should have to do anything is if you installed with the Alternate CD, if so then do the following, assuming this is and Atheros card:

1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

The normal install CD does not require this.

I would take the angryfirelord's advice and go with Regular 32bit Ubuntu, there is like he said, no advantage to running 64bit at them moment.

---

### Post by naelivent on 2006-11-29
Hi!
In the System -> Administration -> Network Settings, on Connections page there is a Wireless connection, that I have configured (hopefully well). I have set here the Essid, and the password (plain text) and let the DHCP stay checked in.
System ->Administration -> Network Tools, on Devices page there are a Loopback Interface (lo) and two "Unknown Interfaces" for wifi0 and ath0. (I cannot configure them.) It's quite strange that the wifi0 network device shows some traffic - It recieves bytes permanently.
I've tried using the dhclient-thingy, here is the output:

////////////////////////////////////////
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:f7:11:7a:77
Sending on   LPF/ath0/00:13:f7:11:7a:77
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
///////////////////////////////////////

And the output for sudo lspci -v. I hope you got closer to the solution of this problem now from this data. And thank you for all the help!! By the way, I begun to download the i386 version of Ubuntu.
FrodoB: Thanks for the advice, but I installed from a normal desktop CD, and it couldn't see the network then, neighter.

///////////////////////////////////////
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [c0] AGP version 3.0

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: 66MHz, fast devsel
        I/O ports at 5080 [size=32]
        I/O ports at 5000 [size=64]
        I/O ports at 5040 [size=64]
        Capabilities: [44] Power Management version 2

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at ff6fd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at ff6fe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80a7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at ff6fc000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Capabilities: [44] Power Management version 2

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        I/O ports at e800 [size=256]
        I/O ports at e400 [size=128]
        Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at ffa0 [size=16]
        Capabilities: [44] Power Management version 2

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 813f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        I/O ports at c400 [size=128]
        Capabilities: [44] Power Management version 2

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff400000-ff4fffff
        Prefetchable memory behind bridge: ceb00000-eeafffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        Memory behind bridge: ff500000-ff5fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited Unknown device 0200
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 209
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b800 [size=256]
        Memory at ff4f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff4c0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
        Subsystem: PC Partner Limited Unknown device 0201
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at ff4e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2

02:09.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: Accton Technology Corporation Unknown device ee24
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at ff5f0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
////////////////////////////

One more thing: I've run iwlist ath0 scan, here is what it returned:

////////////////////////////

ath0      Scan completed :
          Cell 01 - Address: 00:04:E2:FE:F8:92
                    ESSID:"SMC"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

---

### Post by FrodoB on 2006-11-29
Your signal quality is horrible, how far are you from your access point?

                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm

---

### Post by naelivent on 2006-11-29
Hmpf, two rooms away.... Do you think, thais is the main problem? From Windowser it works properly... I'm having a 125 KBps connection speed to the Internet...

---

### Post by FrodoB on 2006-11-29
That's weird, I usually get better results on Atheros with Linux than Windows.

Can you try the 32 bit version with a live CD and see it it is any better or not?

---

### Post by naelivent on 2006-11-29
Uhumm, I've tried all the tjomgs from Ubuntu x32 cd and the symptoms are the same...

---

### Post by angryfirelord on 2006-11-30
Try lowering the bit rate. You'd be EXTREMELY lucky to have a connection go at 54MB/s. Set it to 36MB/s (which even then is generous) or lower, which usually helps it transmit over a longer distance.

Only problem is, I don't know (or forgot how) to do that.

---

### Post by naelivent on 2006-12-01
Do you think that would help? Angryfirelord, even if the name of our cards are the same, I'm nor sure if the card is the same. I don't know where you are from, but there can be serious differences for e.g. between the European and American distribution of a card. (I don't know what is that good for.) And, the modell number, (that I don't know) can differ too. So I think it's totally imaginable, that your card runs perfectly, and mine doesn't.
(As mine is not recognised properly - or is it normal, if some programs call it "unknown hardware"?)
Anyway, I'm going to try to try out your idea too, and if it doesn't work neighter, I'm going to buy another card, which would be totally supported in linux, and write a "nice" letter to SMC.

---

### Post by FrodoB on 2006-12-01
He is right, just the act of setting your wireless to 11Mbps can increase the range of your equipment.  If you look at most device documentation it will tell you that  the device will have many more meters of range just by putting the device in 802.11b mode. It is worth a try.

You should set the access point to 11Mbps as well. My wife has a Windows Laptop that runs much better in 802.11b mode even though it is a broadcom wireless 8.2.11g card that runs can run at 54Mbps.

---

