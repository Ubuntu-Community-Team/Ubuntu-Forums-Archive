---
title: "Trying to set up wireless on my laptop"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by Tsurabisu on 2007-11-23
Hey guys, long time fan of Ubuntu and other Linux distros but for my first time I decided to switch because Im out of gaming now (that was my reason for staying with windows).

Heres my problem:

After installing the newest vesrion of Ubuntu that I recently downloaded I am having problems setting up my wireless network. I have drivers up and running but when I select my network, I enter the WEP key and then shortly after I get promted again. That status icon goes from showing the 2 circles with the spinning thing to an auctual signal bar but still no auctual connection. :(

Right now im running on a Dell E1505. If any other details are needed let me know.

Thanks in advance for your help.

---

### Post by scrooge_74 on 2007-11-23
Broadcom wireless card?  Network manager applet still buggy. Try to connect manual and uninstall the applet

---

### Post by Tsurabisu on 2007-11-30
Not sure which kind of wireless card but right now im using the Intel(5) PRO/Wireless 3945 Network Connection driver for Linux. Its listed as a restricted driver, is there any other drivers out there that would work?

---

### Post by scrooge_74 on 2007-11-30
in a terminal type lspci and it should tell you what card you have

---

### Post by Tsurabisu on 2007-12-01
After typing in that command this is what I got for my network controller.

> Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by kevdog on 2007-12-01
Try connecting manually from the command line just to see if your network card works.  The link is in my signature.

---

### Post by Tsurabisu on 2007-12-01
After trying to connect manually this is what I got:

(I was able to get it working a while back but I don't know why It wont work now)

> travis@travis-laptop:~$ sudo ifconfig eth1 down
travis@travis-laptop:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 6573
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:bb:ae:a9
Sending on   LPF/eth1/00:13:02:bb:ae:a9
Sending on   Socket/fallback
travis@travis-laptop:~$ sudo ifconfig eth1 up
travis@travis-laptop:~$ sudo ifconfig eth1 &#8220;MYNETWORKNAME&#8221;
&#8220;WEST6232&#8221;: Unknown host
ifconfig: `--help' gives usage information.
travis@travis-laptop:~$ sudo ifconfig eth1 MYNETWORKKEY
MYNETWORKKEY: Unknown host
ifconfig: `--help' gives usage information.
travis@travis-laptop:~$ sudo ifconfig eth1 mode Managed
mode: Unknown host
ifconfig: `--help' gives usage information.
travis@travis-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:bb:ae:a9
Sending on   LPF/eth1/00:13:02:bb:ae:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
travis@travis-laptop:~$ 


Thanks again for your help, glad to see Ubuntu has a strong community behind it.

---

### Post by kevdog on 2007-12-01
Can you post iwlist scan   - You keep getting unknown host

---

### Post by Tsurabisu on 2007-12-01
After an iwilist scan here are the results I received:

```
Cell 01 - Address: 00:12:0E:1E:F3:B5
                    ESSID:"WEST6232"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-50 dBm  Noise level=-50 dBm
                    Extra: Last beacon: 20ms ago
```

---

### Post by kevdog on 2007-12-01
Go back and review the instructions again -- you are making a lot of typing mistakes

sudo ifconfig eth1 “MYNETWORKNAME”

This should be 
sudo iwconfig eth1 essid "MYNETWORKNAME"
...
...
sudo ifconfig eth1 up

---

### Post by Tsurabisu on 2007-12-01
Oh im sorry, I forgot to mention I changed those around just to make sure they were the right ones, I accidently posted my second response as opposed to the oriognal one, Ill post it up there when I get a chance.

---

