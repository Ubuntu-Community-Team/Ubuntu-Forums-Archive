---
title: "Can't see any wireless network"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by greenkey on 2007-04-10
Hi all, I tried to find this problem somewhere, but I didn't find it.

I've installed my wireless network card with ndiswrapper and I think it worked:
```
$ iwconfig
[...]
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=0/3  
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So I tried to configure a network with graphical tools, but nothing worked.
Then I check via shell:
```
$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:02:72:44:4b:17
Sending on   LPF/wlan0/00:02:72:44:4b:17
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
And also:
```
lorenzo@portatile-casa:~$ iwlist wlan0 scan
wlan0     No scan results

```

I can't understand why the card is working but I can't see any network (I'm sure there are, I can connect at one of them with $redmond_os).

Thanks

---

### Post by greenkey on 2007-04-12
... is that problem so difficult?
should I contact Ubuntu support?

---

### Post by NICU on 2007-04-12
Hi, when you use iwconfig you need to setup a few things.  Try ```
sudo ifdown wlan0
sudo iwconfig wlan0 essid your_routers_essid
sudo ifup wlan0
```

If you have any other settings like encryption or modes you'll need to configure those too you can get more information about iwconfig by using ```
iwconfig --help
```

---

### Post by greenkey on 2007-04-12
Do I really need it?
If so, why I can see all the wifi nets around me without any config in Windows?

Anyway, I'm going to try your solution this night.... :)

---

### Post by NICU on 2007-04-12
The newer tools in Ubuntu Feisy (7.04) which should be available in a few weeks make wireless networking quite a bit easier.  The commands I gave you are to explicitly connect to your network.  If those commands do not work, then your drivers may not be installed 100% correctly.  Let me know how you make out with the suggestion above.

---

### Post by ittiam on 2007-04-12
I guess if you have WPA for ur wifi network, then you to need to do little bit more configuration of setting up wpa_supplicant. Howto is [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

