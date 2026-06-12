---
title: "Can't get iwp2200 to work..."
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by johannes on 2005-11-30
I see this is a quite common question, and I have been searching around to forum for many hours but have not been able to find a solution that works.

I have a iwp2200 card and a Netgear 802.11bg router that I would like to use together in Breezy. I have tried the howto at [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623) without success. I have also tried using that howto in combination with the latest drivers an firmware (ipw2200-fw-2.4, ieee80211-1.1.6 and ipw2200-1.0.8 ) but no...

I am currently not using any wpa, as I would like to get it working with open access before I start hasseling with that.

This is the output from dmesg:
```
johannes@dreamscape:~$ dmesg | grep ipw
[4294699.901000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4294699.901000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294699.903000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```

iwlist:
```
johannes@dreamscape:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:23:36:56
                    ESSID:"domherre"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=87/100  Signal level=-42 dBm
                    Extra: Last beacon: 354ms ago

```

iwconfig:
```
johannes@dreamscape:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"domherre"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

It seems it can't connect to the access point at all... Do I have to install wpasupplicant? Would that matter?

This is what happens when I try "sudo dhclient eth1"
```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:44:6c:8d
Sending on   LPF/eth1/00:12:f0:44:6c:8d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

What am I doing wrong? :-/ Please help....

---

### Post by ex` on 2005-11-30
Nevermind this post. 4AM, should be sleeping instead of trying to help out.

---

### Post by Lambert on 2005-11-30
maybe try this command to see if you can connect

```
sudo iwconfig eth1 essid domherre ap 00:14:6c:23:36:56 mode managed freq 2.462 commit
```

with iwconfig and the scan giving results the device and driver are probably working. So it's just setting configuration more then likely.

---

### Post by johannes on 2005-11-30
Thanks for the responses :)

Unfortunantly:
```
johannes@dreamscape:~$ sudo iwconfig eth1 essid domherre ap 00:14:6c:23:36:56 mode managed freq 2.462 commit
Error : unrecognised wireless request "managed"
```

---

### Post by johannes on 2005-11-30
Hehe, nevermind... I just realized I had to add the name and MAC address to the card in the router configuration (192.168.1.1) now it works as it should in open access. :KS

---

