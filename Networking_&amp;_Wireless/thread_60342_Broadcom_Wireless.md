---
title: "Broadcom Wireless"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by Qylvaran on 2005-08-27
Hello.  I've been at this problem for almost two days, and I'm hoping one of you guys can help.  First of all, I have the following wireless card:

```
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

I also have version 1.2 of ndiswrapper installed and modprobed, with the bcmwl5 driver inside of it (bcmwl5.inf and bcmwl5.sys).  The little light under my laptop's touchpad tells me that the wireless card is on.

The following is as far as I've been able to get with setting things up.  Note that the essid, key, and channel are 100% correct, according to the router which I have logged into on the computer immediately behind me.

```
ender@jane:~$ sudo iwconfig wlan0 channel 6 key open 0000000000 essid default
ender@jane:~$ sudo iwconfig
lo        no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:0000-0000-00   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

ender@jane:~$ sudo iwlist wlan0 scan
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     No scan results
ender@jane:~$
```

I have tried following the instructions on the ndiswrapper website, as well as the ones in the broadcom guide in the tips and tricks section.  Each time, I am careful to remove all traces of previous attempts.  I have used the version of ndiswrapper that comes in the package manager, as well as 1.3 rc-something and 1.2 from the ndiswrapper site.

Also, I have gotten wireless working on this laptop before while running Gentoo, and on my sister's identical laptop running Ubuntu.  I'm not sure what I'm doing differently now, and can't compare since she left for college.

Please help me.

---

### Post by Qylvaran on 2005-08-31
I thought I had it.  It has gotten so that I can set the ESSID, and the mac address of an access point is found, but this supposed address is different every time, and NOT the same as my router.  I have tried using dhclient to get an ip address, but it fails.  Any help?  It's nearing a week since I first ran into this problem.  It's also kind of disheartening that I haven't even gotten one response to this thread.  I'm feeling a little stranded.

Here's my current iwconfig.  Note that the number after 'Access Point:' is not the mac address of my router (should it be?) and I had to set the mode to 'auto' in order to change the ESSID.
```

wlan0     IEEE 802.11g  ESSID:"default"
          Mode:Auto  Frequency:2.437 GHz  Access Point: AA:08:46:2A:A6:91
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:0000-0000-00   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-57 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Any form of help will be greatly appreciated.

EDIT:  C'mon, people.  Even something like 'I have no idea, but you might try this other forum, where people actually know what they're talking about' would be appreciated at this point.  I feel like I'm talking to thin air.

---

