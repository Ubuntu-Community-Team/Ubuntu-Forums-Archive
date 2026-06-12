---
title: "No DHCPOFFER for wireless"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Ber P on 2008-12-01
I've just upgraded from 7.10 to 8.10. My wireless (acx_pci driver) was working perfectly in 7.10, but in 8.10 i can't get any dhcpoffer. 

I've configured my network card in rc.locals (as I did in 7.10) like this

```

ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid "Saturn"
iwconfig wlan0 mode Managed
dhclient wlan0

```

if I plug in my cable, bring eth0 up and try dhclient eth0 - I recieve an IP right away.

I've seen lots of threads on this issue, but fails an answer.

anyone?

---

### Post by Ber P on 2008-12-02
I've noticed that even though I *ifconfig eth0 down* in rc.locals, the eth0 is still up when I boot.

Can anybody shortly explain the network startup sequence? What is for instance the difference between /etc/rc.local and /etc/network/interfaces?

Also, how do I see if my acx_pci driver is ok and latest version?

---

### Post by Ber P on 2008-12-02
After some messing around, I'm currently ended up with a rc.local like this:```
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid "Saturn"
iwconfig wlan0 mode Managed
dhclient wlan0
``` 
and a /etc/network/interfaces like this:
```
auto lo
iface lo inet loopback

auto wlan0 
iface wlan0 inet dhcp

```

Seems to be working now, but the boot sequenze hangs for minutes at "reconfiguring network interfaces" (or something like that). No idea why! No idea why I suddenly do get an IP address! 

This is extremely anoing. Why does this wireless issue keep being such a pain in the butt? How come Network Manager is still unable to handle wireless connections properly? I figure this is a show-stopper for many trying out ubuntu/linux - and I haven't even started to talk about WEP and WPA! AAaarrrgghhh.....

---

