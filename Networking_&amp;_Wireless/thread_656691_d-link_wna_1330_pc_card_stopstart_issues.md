---
title: "d-link wna 1330 pc card stop/start issues"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by md11driver on 2008-01-02
i have an internet account at a part-time location that is tied to a mac address on my wife's laptop. with windows, i simply spoofed the mac address using freeware in order to log on with my then windows laptop. it's now (i'm proud to say) a pure linux machine. i know how, via the forums, how to change the transmitted mac address, but i have a weird problem. the default linux driver (ath_pci) works beautifully with my home network, but when i change the mac address (using sudo ifconfig ath0 down, change the mac address with the appropriate commands, then restart) i cannot connect to my home network. some outputs follow:

sudo ifdown ath0 returns:
ifdown: interface ath0 not configured

iwconfig returns:

lo no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"songbird" Nickname:""
Mode:Managed Frequency:2.437 GHz Access Point: 00:12:17:39:42:91
Bit Rate:54 Mb/s Tx-Power:18 dBm Sensitivity=1/1
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=54/70 Signal level=-40 dBm Noise level=-94 dBm
Rx invalid nwid:27761 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

iwlist scanning returns:

lo Interface doesn't support scanning.

wifi0 Interface doesn't support scanning.

ath0 Scan completed :
Cell 01 - Address: 00:12:17:39:42:91
ESSID:"songbird"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality=57/70 Signal level=-38 dBm Noise level=-95 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Cell 02 - Address: 00:40:96:5C:5D7
ESSID:"apdestpt"
Mode:Master
Frequency:2.412 GHz (Channel 1)
Quality=7/70 Signal level=-88 dBm Noise level=-95 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
Cell 03 - Address: 00:40:96:5B:F6:31
ESSID:"apdestpt"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality=2/70 Signal level=-93 dBm Noise level=-95 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
Cell 04 - Address: 00:18:3F:AA0:49
ESSID:"2WIRE426"
Mode:Master
Frequency:2.447 GHz (Channel
Quality=7/70 Signal level=-88 dBm Noise level=-95 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100

ifconfig returns:

ath0 Link encap:Ethernet HWaddr 00:15:E9:5E:EA9
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::215:e9ff:fe5e:ead9/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2318 errors:0 dropped:0 overruns:0 frame:0
TX packets:2013 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1961735 (1.8 MB) TX bytes:272598 (266.2 KB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

wifi0 Link encap:UNSPEC HWaddr 00-15-E9-5E-EA-D9-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:76318 errors:0 dropped:0 overruns:0 frame:47859
TX packets:2775 errors:1 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:8806946 (8.3 MB) TX bytes:366802 (358.2 KB)
Interrupt:9

cat /etc/network/interfaces returns:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

none or all of the above commands shut down my wireless connectivity, and i think the combination probably should.

the isp provider won't provide another mac address unless i sign up for another account, and i don't want to do that. can someone please tell me why my card isn't responding like most pc cards i read about in the forums?

this 60-something old n00b would certainly appreciate some help from you whizzes.

---

### Post by LastChanceLeeward on 2008-01-02
I am just a n00b, but I have a little info you might appreciate.

I do not know much about your wna 1330 pc card, except that people writing in forums seem to give its brother, the wna 2330 pc card, much better marks at consistent performance. However, what I do know for sure from first hand experience less than 10 min ago is that the Linksys WUSB54GC works after running one script from Hendrick!!!! BTW, I just priced the 2330 at 30 dollars, and the WUSB54GC for 40 dollars.

[http://ubuntuforums.org/showthread.php?t=95380](http://ubuntuforums.org/showthread.php?t=95380)

I Apologize that I could not be more help on your specific problem: WNA 1330

---

### Post by md11driver on 2008-01-03
thank you lastchanceleeward.  i took your advice and bought a wna 2330 today.  no help.  i also have a linksys wusb54gsc but as of right now, madwifi doesn't support usb devices.  as much as i hate to do it, i guess i'll give up.  most of my forum entries go unanswered anyway.  thank you for your reply.

---

