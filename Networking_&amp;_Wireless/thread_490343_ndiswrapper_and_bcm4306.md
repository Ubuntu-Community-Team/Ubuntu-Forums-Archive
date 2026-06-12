---
title: "ndiswrapper and bcm4306"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by jpl80 on 2007-07-02
I used the [steps outlined here to configure ndiswrapper and my wireless card (bcm4306)]("http://ubuntuforums.org/showthread.php?t=340689&highlight=inspiron+8500") to work with a Dell Inspiron 8500. I can now see the networks in range, but when I try to connect with them I get nothing. Here are some of my outputs.

**My output to dmesg is:**

ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
ndiswrapper: using IRQ 5
wlan0: ethernet device 00:90:4b:14:3f:14 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: '', 14E4:4320.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
usbcore: registered new interface driver ndiswrapper

**...(down a little ways)...**

NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready
ADDRCONF(NETDEV_UP): wlan0: link is not ready

**My output to lspci -v**

    02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at faff6000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
[B]
my output to iwconfig wlan0 is:[/B]

          IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by TrueJk7 on 2007-07-02
It does not look like it even know's what you are trying to do. Just to connect in terminal try
```
sudo iwconfig wlan0 essid (your network name) mode managed
dhcp wlan0
```

Good luck

Ps, got WEP or WPSK?

---

### Post by jpl80 on 2007-07-02
72 hrs later I discover:

Dell has a special wireless enable/disable button (Fn + F2). 

*Wow, I'm becoming like my parents in that, intuitively placed buttons completely evade my line of vision. *

---

### Post by TrueJk7 on 2007-07-02
heh, happens to the best of us. Make ya feel better if I told ya I did the exact same thing. Just I didn't have to tell anyone :).

---

### Post by jpl80 on 2007-07-03
Okay I'm back again because I can't connect. To reiterate my problem, I have wireless set to roaming. I see the network and when I attempt connection it just says it's connected at 0%. No bars. Yesterday I had bars... Now I don't...

I get these messages at the bottom of dmesg:

ADDRCONF(NETDEV_UP): wlan0: link is not ready

ndiswrapper -l says the driver is installed. driver present.

I went into BIOS and disabled that wireless hotkey thing... so the default is set to on...

Any ideas?

*BTW: dhcp wlan0 returns command not found*

---

### Post by Ayuthia on 2007-07-03
Does lsmod|grep ndiswrapper show that ndiswrapper is loaded?

---

### Post by jpl80 on 2007-07-03
yes it says
```

ndiswrapper   194608   0
usbcore       134280   4   ndiswrapper, ehci_hcd, uhci_hcd
```

---

### Post by kevdog on 2007-07-03
Can you post the following:
lshw - C network
/etc/network/interfaces <---This is a file
iwlist scan

---

