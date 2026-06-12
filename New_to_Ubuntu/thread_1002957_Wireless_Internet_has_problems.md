---
title: "Wireless Internet has problems"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by alon_lhv on 2008-12-05
Hello, I have this problem, and yesterday we tried to solve it without any success:(. I hope today will be better..

And here it is:

I am new in the Linux world. I have purchased this very old laptop: IBM Thinkpad T20 700MHz with 256MB RAM and 20 GB HD. It runs very sllow, however, this is not my biggest problem: the wireless Internet doesn't work well.

I have a NETGEAR WG111v2, connected to the USB. When I start the computer, it detects the wireless network and works good for couple of minutes, but after that it fails to connect to the Internet - it report "wireless network connection to'LahavNt' (0%)" when I put my cursor on the wireless icon. The USB is OK, because I see all the available networks. But it cannot reconnect to the Internet, until I restart the computer.

Also, sometimes even when the little icon reports 89% reception, it fails to communicate with the Internet.

It works good with my other new laptop with windows Vista, so I assume the problem is not there.

======================================

Yesterday we tried this:

Here it is:
1)
for the sudo lshw -C network, the results were:
-----------------------------------------------
*-network
description: Wireless interface
physical id:1
lagical name: wlan0
serial: 00:0f:b5:b5:af:3b
capabilities: ethernet physical wirless
configuration: broadcast=yes ip=192.168.10.102 multicast=yes wireless=IEEE 802.llg
2)
for the iwconfig, the results are:
----------------------------------
lo no wireless extentions.
irda0 no wireless extentions.
wmaster0 no wireless extentions.
wlan0 IEEE 802.llg ESSID:"LahavNet"
mode:Managed Frequency:2.412GHz Access Point: 00:14:d1:5:bf:ee
Bit Rate=1 MB/s Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragmented thr=2346 B
Link Qaulity=57/64 Signal Level=46/65
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retris:0 Invalid misc:0 Missed beacon:0
3)
for the : sudo iwconfig wlan0 rate 11M,
nothing really happened...

--> So, what now can we check or do??

Thanks.

---

### Post by wieman01 on 2008-12-05
Please also post:
> sudo iwlist scan
What chipset is your adapter?

---

### Post by alon_lhv on 2008-12-05
I tried this: sudo iwlist scan
------------------------------
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Then, After taking out the Netgear and returning it, it started to work! And the results were:

laptop@ibmlaptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:55:BF:EE
                    ESSID:"LahavNet"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/64  Signal level=45/65
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023a48761cc
          Cell 02 - Address: 00:1B:2F:DF:95:22
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/64  Signal level=9/65
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000021ad8acb0e0
          Cell 03 - Address: 00:16:B6:B9:51:75
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/64  Signal level=9/65
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000086f83488b8

I know that it works temporarly. And the problem will arrive soon eanough...

---

### Post by blackened on 2008-12-05
> **alon_lhv said:**
> I tried this: sudo iwlist scan
------------------------------
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Then, After taking out the Netgear and returning it, it started to work! And the results were:

laptop@ibmlaptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:55:BF:EE
                    ESSID:"LahavNet"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/64  Signal level=45/65
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000023a48761cc
          Cell 02 - Address: 00:1B:2F:DF:95:22
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/64  Signal level=9/65
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000021ad8acb0e0
          Cell 03 - Address: 00:16:B6:B9:51:75
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/64  Signal level=9/65
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000086f83488b8

I know that it works temporarly. And the problem will arrive soon eanough...

Please wrap terminal output in CODE tags (in the "Advanced Response" dialog upper menu it's the # sign) so as to avoid the lovely little emoticons that pepper it when left to page formatting.

---

### Post by wieman01 on 2008-12-05
Weird, you adapter appears to be fine. What are the exact symptoms when you try to connect using the network applet? Can you connect while all security (e.g. WPA) is turned off? Can you ping your router?

---

### Post by alon_lhv on 2008-12-05
Well, I tried to ping, but it told me "unknown host". Also firefox don't find anything on the net.. :(
I don't understand what do you mean by: "Can you connect while all security (e.g. WPA) is turned off". Can you please help me do this (I am totally new in the linux world..).

---

### Post by wieman01 on 2008-12-06
OK, no problem.

First of all, what's your wireless network ID (SSID)? Is it "NETGEAR" as shown here?
> Cell 02 - Address: 00:1B:2FF:95:22
ESSID:"**[COLOR="Red"]NETGEAR[/COLOR]**"
Mode:Master
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=42/64 Signal level=9/65
Encryption keyn
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : **[COLOR="Blue"]TKIP[/COLOR]**
Authentication Suites (1) : PSK
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
48 Mb/s; 54 Mb/s
Extra:tsf=0000021ad8acb0e0
The scan results tell me that you have enabled security/encryption (TKIP) meaning that your network is password-protected. Therefore you cannot connect to it without entering a passphrase.

Please let me know which one of the networks is yours and we'll continue from there.

---

### Post by alon_lhv on 2008-12-06
My network ID is not NETGEAR. This is my USB wireless card, that connect my ThinkPad to the Internet. My network ID is LahavNet. Now I tried again to use "sudo iwlist scan", and no cell was with the name "NETGEAR".
The network is not encripted. I uses it with my other laptop and it works well, even when I use the same wireless USB connector (the NETGEAR).

---

### Post by alon_lhv on 2008-12-06
I also wanted to remind, that the Internet connection works well for 1-10 minutes after restarting my computer, and then it turns looses it's connection..

---

### Post by alon_lhv on 2008-12-06
Do you think it could be a driver problem? How do I know wich driver is used? And how do I know if it is the right one?

---

### Post by alon_lhv on 2008-12-06
And one more thing that I've tried: I restarted the computer, and then used iwevent to log the wireless. At the beginning ping worked fine, but after a while, it stoped working. Here is the result for the log, hope it could help:

laptop@ibmlaptop:~$ iwevent
Waiting for Wireless Events from interfaces...
14:29:38.620172   wlan0    Scan request completed
14:29:55.801806   wlan0    Scan request completed
14:29:59.861453   wlan0    Scan request completed
14:29:59.861528   wlan0    New Access Point/Cell address:Not-Associated
14:30:03.282870   wlan0    Scan request completed
14:30:03.284196   wlan0    Set Mode:Managed
14:30:03.494101   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:30:03.494197   wlan0    New Access Point/Cell address:00:141:55:BF:EE
14:30:03.498793   wlan0    Set Frequency:2.412 GHz (Channel 1)
14:30:03.498962   wlan0    Set ESSID:"LahavNet"
14:30:03.505014   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:30:03.505090   wlan0    New Access Point/Cell address:00:141:55:BF:EE
14:30:08.711320   wlan0    Scan request completed
14:30:12.715968   wlan0    Scan request completed
14:30:12.716045   wlan0    New Access Point/Cell address:Not-Associated
14:30:16.088450   wlan0    Scan request completed
14:30:16.089580   wlan0    Set Mode:Managed
14:30:16.318623   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:30:16.318698   wlan0    New Access Point/Cell address:00:14:D1:55:BF:EE
14:30:16.325433   wlan0    Set Frequency:2.412 GHz (Channel 1)
14:30:16.325538   wlan0    Set ESSID:"LahavNet"
14:30:16.331610   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:30:16.331678   wlan0    New Access Point/Cell address:00:14:D1:55:BF:EE
14:30:26.381347   wlan0    Scan request completed
14:30:30.418006   wlan0    Scan request completed
14:30:30.418085   wlan0    New Access Point/Cell address:Not-Associated
14:30:33.866477   wlan0    Scan request completed
14:30:33.868320   wlan0    Set Mode:Managed
14:30:34.076689   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:30:34.076764   wlan0    New Access Point/Cell address:00:14:D1:55:BF:EE
14:30:34.085637   wlan0    Set Frequency:2.412 GHz (Channel 1)
14:30:34.085743   wlan0    Set ESSID:"LahavNet"
14:30:34.092611   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:30:34.092691   wlan0    New Access Point/Cell address:00:14:D1:55:BF:EE
14:31:33.456553   wlan0    New Access Point/Cell address:Not-Associated
14:31:35.460163   wlan0    Custom driver event:ASSOCINFO(ReqIE0c12182432043048606c RespIE)
14:31:35.460238   wlan0    New Access Point/Cell address:00:14:D1:55:BF:EE
14:31:38.629350   wlan0    Scan request completed
14:32:24.603259   wlan0    Scan request completed
14:32:28.550955   wlan0    Scan request completed
14:32:28.551037   wlan0    New Access Point/Cell address:Not-Associated
14:32:31.653327   wlan0    Set Mode:Managed
14:32:31.871834   wlan0    Scan request completed
14:32:31.877442   wlan0    Set Frequency:2.412 GHz (Channel 1)
14:32:31.877551   wlan0    Set ESSID:"LahavNet"
14:32:45.147921   wlan0    Scan request completed
14:32:53.420994   wlan0    Scan request completed

---

### Post by alon_lhv on 2008-12-12
I solved this problem by installing Ubuntu 8.10. :)

---

