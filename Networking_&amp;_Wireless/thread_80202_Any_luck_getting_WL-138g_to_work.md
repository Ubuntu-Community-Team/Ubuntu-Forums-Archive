---
title: "Any luck getting WL-138g to work?"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by aivars on 2005-10-21
Hello,
Has anybody managed to get Asus WL-138g PCI wireless card working under Ubuntu 5.10? I have installed ndiswrapper, installed windows xp drivers, i can see the card with iwconfig, but when i do ifup or automatically by script it basically hangs up the system with a lot of error messages ending with: "No DHCPOFFERS received.
No working leases in persistent database - sleeping." I have seen the same symptoms on other card reading these excellent forums
Maybe there is someone who already went through all this?
PS I am a noobee (complete) in Linux
Thanks a lot

Aivars
:cool:

---

### Post by jhong on 2005-10-21
[QUOTE=aivars]Hello,
Has anybody managed to get Asus WL-138g PCI wireless card working under Ubuntu 5.10? I have installed ndiswrapper, installed windows xp drivers, i can see the card with iwconfig, but when i do ifup or automatically by script it basically hangs up the system with a lot of error messages ending with: "No DHCPOFFERS received.
No working leases in persistent database - sleeping." I have seen the same symptoms on other card reading these excellent forums
Maybe there is someone who already went through all this?
PS I am a noobee (complete) in Linux
Thanks a lot

Aivars
:cool:[/QUOTE]

Is your wireless network secured by WEP or WPA?

---

### Post by aivars on 2005-10-22
Thanks,
WEP

Aivars

---

### Post by aivars on 2005-10-22
I noticed that the access point of my card is set to 00:00:00:00:00 (see below). From man pages i understand that is something to do with configuration. And I am not able to change it with sudo iwconfig wlan0 ap. When i enter that command nothing happens.
How can i change ap to the one i need?

Thanks Aivars

+++

aivars@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-46 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0

sit0      no wireless extensions.

---

### Post by monkeyface on 2005-10-30
Have you got it to work?
I'm getting one of these in a few days too... :)

EDIT: Oh, have just seen your [thread](http://ubuntuforums.org/showthread.php?t=80406&highlight=wl-138g).
Hope i'm getting it to work too! :)

---

