---
title: "strange pcmcia card problem (AT-WCL452)"
date: 2005-11-21
forum: Networking &amp; Wireless
---

### Post by nofear0720 on 2005-11-21
hello, greetings to all :) i'm new here and this is my first post and i saw lots of  topic posted here but it still cannot solve my problem so i decide to start a new thread.

i'm having a problem using my pcmcia card to connect to internet and for your information i'm using the Ubuntu 5.10 with a compiled kernel version 2.6.14.1, here is the model of the card:

root@nofear0720:~# cardctl ident

Socket 0:
product info: "Allied Telesyn", "AT-WCL452 Wireless PCMCIA Radio", "Ver. 1.00", ""
manfid: 0xc00f, 0x0000
function: 6 (network)

since there is no pre-installed driver for the card in the current distro and the "Network Manager" doesn't show up anything apart from the some default configuration ( ethernet connection & dial-up connection), then i have to look for the driver myself and i downloaded from the manufacturer which is a wlan-ng driver but unfourtunately i failed to compile the module. Mad

after googling, i found out another driver that can support my card (hostap driver). This time i can successfully compiled and installed the module. i found the hostap configuration file: /etc/pcmcia/hostap_cs.conf

after reboot the machine, i went to check my "Network Manager" and the wireless configuration stuff is appeared. Surprised I thought i'm going to the right path, but the fact is not Confused .

i tried to check whether my card is up or not:

root@nofear0720:/etc/pcmcia# ifconfig
eth0 Link encap:Ethernet HWaddr 00:90:F5:33:1E:F6
inet addr:192.168.0.151 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::290:f5ff:fe33:1ef6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:977 errors:0 dropped:0 overruns:0 frame:0
TX packets:961 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:398448 (389.1 KiB) TX bytes:128043 (125.0 KiB)
Interrupt:11 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:5872 errors:0 dropped:0 overruns:0 frame:0
TX packets:5872 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:534801 (522.2 KiB) TX bytes:534801 (522.2 KiB)

wifi0 Link encap:UNSPEC HWaddr 00-30-84-1F-A5-81-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:8748 (8.5 KiB)
Interrupt:10 Base address:0x100

wlan0 Link encap:Ethernet HWaddr 00:30:84:1F:A5:81
inet6 addr: fe80::230:84ff:fe1f:a581/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:8748 (8.5 KiB)
Interrupt:10 Base address:0x100
and :

root@nofear0720:/etc/pcmcia# iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

Warning: Driver for device wifi0 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

wifi0 IEEE 802.11b ESSID:"nofear0720"
Mode:Master Frequency:2.422 GHz Access Point: 00:30:84:1F:A5:81p
Bit Rate:11 Mb/s Sensitivity=1/3
Retry min limit:8 RTS thr:off Fragment thr:off
Encryption key:******* Security mode:restricted
Power Management:off

wlan0 IEEE 802.11b ESSID:"nofear0720"
Mode:Master Frequency:2.422 GHz Access Point: 00:30:84:1F:A5:81
Bit Rate:11 Mb/s Sensitivity=1/3
Retry min limit:8 RTS thr:off Fragment thr:off
Encryption key:******* Security mode:restricted
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:3603 Missed beacon:0


i simply ignore the warning message because it's not a major problem here and one thing had suprised me enough Shocked ; that is the access point's mac address. perhaps i'm wrong but the mac address for the access point should be my wireless router mac address instead of the pcmcia card's mac address Question anyone has any idea about this?????

here is my iwlist scan result and dmesg result:

root@nofear0720:/etc/pcmcia# iwlist wlan0 scan
.
wlan0 No scan results

root@nofear0720:/etc/pcmcia# dmesg
....
[17179631.752000] pcmcia: Detected deprecated PCMCIA ioctl usage.
[17179631.752000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17179631.752000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[17179631.752000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f
[17179631.756000] cs: IO port probe 0xc00-0xcf7: clean.
[17179631.756000] cs: IO port probe 0xa00-0xaff: clean.
[17179631.760000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[17179631.996000] hostap_crypt: registered algorithm 'NULL'
[17179632.040000] ieee80211_crypt: registered algorithm 'NULL'
[17179632.088000] hostap_cs: 0.4.5 - 2005-09-25 (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179632.156000] hostap_cs: setting Vcc=33 (constant)
[17179632.156000] hostap_cs: CS_EVENT_CARD_INSERTION
[17179632.156000] hostap_cs: setting Vcc=50 (from config)
[17179632.156000] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[17179632.156000] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[17179632.156000] io->flags = 0x0046, io.base=0x0000, len=64
[17179632.156000] hostap_cs: Registered netdevice wifi0
[17179632.196000] hostap_cs: index 0x01: Vcc 5.0, irq 10, io 0x0100-0x013f
[17179632.396000] prism2_hw_init: initialized in 200 ms
[17179632.396000] wifi0: NIC: id=0x801b v1.0.0
[17179632.396000] wifi0: PRI: id=0x15 v1.1.0
[17179632.400000] wifi0: STA: id=0x1f v1.4.9
[17179632.400000] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[17179632.404000] wifi0: registered netdevice wlan0
[17179632.936000] hostap_crypt: registered algorithm 'WEP'
[17179633.592000] Bluetooth: Core ver 2.7
[17179633.592000] NET: Registered protocol family 31
[17179633.592000] Bluetooth: HCI device and connection manager initialized
[17179633.592000] Bluetooth: HCI socket layer initialized
[17179633.688000] Bluetooth: L2CAP ver 2.7
[17179633.688000] Bluetooth: L2CAP socket layer initialized
[17179633.736000] Bluetooth: RFCOMM ver 1.5
[17179633.736000] Bluetooth: RFCOMM socket layer initialized
[17179633.736000] Bluetooth: RFCOMM TTY layer initialized
[17179643.884000] wlan0: no IPv6 routers present
[17181489.360000] wifi0: Deauthenticate all stations
[17181489.384000] wlan0: Host AP mode does not support 'Any' essid
[17181501.996000] Scan result translation succeeded (length=0)
...

if any further information needed, please inform Wink
thanks for paying attention to me .....

---

