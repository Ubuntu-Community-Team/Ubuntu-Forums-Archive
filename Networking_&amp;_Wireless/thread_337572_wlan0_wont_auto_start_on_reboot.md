---
title: "wlan0 wont auto start on reboot"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2007-01-13
Greetings

I have a laptop with Kubuntu 6.10 running 2.6.17-10 (SMP)
I also have a wireless network running on WEP/Open

I have got my wireless card (Netgear WG511 v3) working with ndiswrapper as per other threads in this forum, but it will only work manually.

By this, I mean everytime I reboot I have to go to "K, Internet, Wireless Assistant Wireless LAN Manager" enter root password and simply click on my ESSID.  I dont need to re-enter the WEP key or anything - that's literally all I have to do to reconnect.

I really would prefer that it comes up automatically, as this is for my 10 y/o son, to whom I'd rather not give root access.

This, from /etc/network/interfaces :

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid mywlanessidname
wireless-channel 9
wireless-nick sons_name
wireless-key xxxxxxxxxxxxxxxxxxxxxxxx
```

There must be something simple I'm missing somewhere, because if a simple mouse click (albeit with root perms) is all I need to do to manually raise the WLAN, then I must be able to script it auto on-boot, no? ](*,) 

Thanks
Steve

---

### Post by hal10000 on 2007-01-13
Perhaps you should install one of the discover1 or discover2 packages, which detects your hardware at boot time.

---

### Post by sparky-steve on 2007-01-13
I dont think the hardware was the problem.

I've since solved this, anyway:

I created a bash script /etc/init.d/wifi_go

```
#!/bin/bash
#
iwconfig wlan0 key open <network_key> essid <essid>
dhclient3 wlan0
```

then 

```
chmod +x /etc/init.d/wifi_go
then ln -s /etc/init.d/wifi_go /etc/rcS.d/S99wifi_go
```

So far it works like a charm. Probably a nasty way of doing it, but it works nonetheless.

(Bash script was my work; Thanks to Jalad for help with the rcS.d)

---

### Post by sparky-steve on 2007-01-14
Ignore the above resolution. it causes a whole heap of problems.

Kubuntu and wireless just arent meant to be, for me.

---

