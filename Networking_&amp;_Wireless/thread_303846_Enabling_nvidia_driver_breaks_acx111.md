---
title: "Enabling nvidia driver breaks acx111"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by daigidan on 2006-11-20
Greetings,

I had been using the nv driver for X for quite some time, but recently had a need to gain 3D acceleration and all the other benefits of using the closed-soure nvidia driver. So I changed 'nv' to 'nvidia' in my xorg.conf, restarted X, and found that I could no longer get on the Internet (although the graphics were prettier ;) . I am running the Ubuntu Edgy Eft distribution for AMD64 with an nvidia GeForce 6600 PCI-E card. My wireless card is a Netgear WG311v2. Since I am running on AMD64 and Netgear has no driver for this platform ndiswrapper is not an option for me, and so I am very grateful for the ACX project. Below is the output from various informative commands after a reboot.

```
daigidan@ado:~$ uname -a
Linux ado 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux
```

```
daigidan@ado:~$ lspci | grep ACX
04:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

```
daigidan@ado:~$ dmesg | grep acx
[   47.859128] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[   47.859131] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   47.859528] acx: found ACX111-based wireless network card at 0000:04:08.0, irq:90, phymem1:0xFEAFC000, phymem2:0xFEAC0000, mem1:0xffffc20000234000, mem1_size:8192, mem2:0xffffc20000240000, mem2_size:131072
[   49.179161] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[   49.179236] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-generic
[   49.179269] usbcore: registered new driver acx_usb
```

```
daigidan@ado:~$ dmesg | grep wlan0
[   49.179236] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-generic
[   49.227546] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[   59.992171] wlan0: duplicate address detected!
[   99.834886] NETDEV WATCHDOG: wlan0: transmit timed out
[   99.834912] wlan0: tx timeout!
[   99.834944] wlan0: recalibrating radio
[   99.882854] wlan0: successfully recalibrated radio
[  107.833165] NETDEV WATCHDOG: wlan0: transmit timed out
[  107.833173] wlan0: FAILED to free any of the many full tx buffers. Switching to emergency freeing. Please report!
[  107.833221] wlan0: tx timeout!
[  107.833280] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
[  118.411062] NETDEV WATCHDOG: wlan0: transmit timed out
[  118.411066] wlan0: FAILED to free any of the many full tx buffers. Switching to emergency freeing. Please report!
[  118.411090] wlan0: tx timeout!
[  118.411116] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
```

The above errors repeat many times.

```
daigidan@ado:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Madrid"  Nickname:"acx v0.3.21"
        Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:12:F8:A2           Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3          Retry min limit:7   RTS thr:off           Power Management:off
        Link Quality=46/100  Signal level=24/100  Noise level=0/100
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.
```

```
daigidan@ado:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:48:AC:71          UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
        Interrupt:50 Base address:0x6000

lo        Link encap:Local Loopback          inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:132 errors:0 dropped:0 overruns:0 frame:0
        TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:12291 (12.0 KiB)  TX bytes:12291 (12.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:47:F5:75          inet addr:192.168.61.4  Bcast:192.168.61.255  Mask:255.255.255.0
        inet6 addr: fe80::20f:b5ff:fe47:f575/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets:18 errors:1 dropped:0 overruns:0 frame:0
        TX packets:195 errors:13 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:2942 (2.8 KiB)  TX bytes:9843 (9.6 KiB)
        Interrupt:90 Base address:0xc000
```

So it seems like I am associating to the WAP and getting an IP here, but web browsing, pinging my router, etc. do not work.

```
daigidan@ado:~$ sudo ifdown wlan0
Password:
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3870
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:47:f5:75
Sending on   LPF/wlan0/00:0f:b5:47:f5:75
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.61.1 port 67
```

```
daigidan@ado:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:b5:47:f5:75
Sending on   LPF/wlan0/00:0f:b5:47:f5:75
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
daigidan@ado:~$ tail -10 /var/log/messages
Nov 20 21:49:35 localhost kernel: [  276.076984] acx: BUG: no free txdesc left
Nov 20 21:49:37 localhost kernel: [  276.758311] acx: BUG: no free txdesc left
Nov 20 21:49:39 localhost kernel: [  277.893861] acx: BUG: no free txdesc left
Nov 20 21:49:42 localhost kernel: [  279.029410] acx: BUG: no free txdesc left
Nov 20 21:49:44 localhost kernel: [  280.164960] acx: BUG: no free txdesc left
Nov 20 21:49:47 localhost kernel: [  281.300510] acx: BUG: no free txdesc left
Nov 20 21:49:49 localhost kernel: [  282.436059] acx: BUG: no free txdesc left
Nov 20 21:49:52 localhost kernel: [  283.571622] acx: BUG: no free txdesc left
Nov 20 21:49:54 localhost kernel: [  284.707160] acx: BUG: no free txdesc left
Nov 20 21:49:57 localhost kernel: [  285.842708] acx: BUG: no free txdesc left
```

```
daigidan@ado:~$ iwlist wlan0 scan
wlan0     Scan completed :
        Cell 01 - Address: 00:0F:B5:12:F8:A2
                  ESSID:""
                  Mode:Master
                  Frequency:2.462 GHz (Channel 11)
                  Quality=46/100  Signal level=24/100  Noise level=0/100
                  Encryption key:off
                  Bit Rates:54 Mb/s

```

I am not broadcasting SSID, so the blank ESSID is expected, I think. I am at a loss as to what to do next. Any help would be greatly appreciated.

Thanks,
daigidan

---

### Post by Neobuntu on 2006-11-20
Try blacklisting acx and use ndiswrapper with it's XP driver and see if all works that way, (and post your results).

Is acx working for ANYONE with a acx111 (802.11G) wireless device?

I have to black list acx for this "g" TI chip set and also bcm43xx for an old "b" Linksys and use ndiswrapper.

ndiswrapper is a whole lot easier (pointy clicky GUI) when the "Install windows wireless drivers"(ndis-gtk)is in the menu but it requires an Internet connection before hand; with either hardwired Ethernet Internet or another wifi card that just works in Ubuntu.

---

### Post by daigidan on 2006-11-20
I appreciate the input, but are you certain that installing 32-bit drivers on AMD64 under ndiswrapper is going to work? This seems somewhat brittle to me.

Using the nv driver I can run with acx111, WEP-enabled, with no issues. I'd rather understand why nvidia causes acx to barf. Having said that, if it comes to a choice between a new card and ndiswrapper, I'll definitely give ndiswrapper a shot.

I've sent mail to the acx100-users mailing list to see if I can get input from that direction. If I make any progress there I'll update this thread.

---

### Post by Neobuntu on 2006-11-22
Oh, my bad. I'm not sure with 64 bit.

---

### Post by daigidan on 2006-11-22
I heard back from a user on the acx100-users list who suggested that this problem is most likely caused by an IRQ conflict. He said that enabling APIC in the kernel had caused the problem to go away for him, and further suggested that moving the PCI cards around, or assigning an IRQ in BIOS, might help. Going to give these ideas a try over the holiday here in the U.S. and will report back on the results.

[And I thought my days of dealing with IRQ conflicts were a thing of the past ;]

---

### Post by daigidan on 2006-11-28
So, I never did figure this problem out. My time and energy at their ends, I went out and got a wireless ethernet bridge.

---

