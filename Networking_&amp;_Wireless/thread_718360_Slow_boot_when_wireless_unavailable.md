---
title: "Slow boot when wireless unavailable"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by timr92 on 2008-03-08
Hi, I'm having trouble with my wireless. When the wireless router is not available, the loading bar goes about 3/4 the way and then stops, but then soon displays the login screen. I log on, but it takes 5 minutes for all my panel icons and desktop to load, but it is fine when the wireless router was ok. Someone suggested to put the default stuff back into /etc/network/interfaces, which put it into roaming mode, but i needed to be able to put the gateway and static IP address in, so that didn't suit me. I then tried [This HOWTO]("http://ubuntuforums.org/showthread.php?t=684495"), but it still goes 3/4 the way when it is booting, and hangs for a little longer than it should.

Does that HOWTO assume that i dont use Network Manager? I dont really use it, but it is still there.

What i did from that tutorial was set it up for WEP with static IP address:
```
sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig eth0 192.168.100.60 netmask 255.255.255.0 up
sudo route add default gw 192.168.100.1
sudo ifconfig eth0 essid "OURHOUSE"
sudo ifconfig eth0 key FB622816FC
sudo iwconfig eth0 mode Managed
sudo dhclient eth0
```

And i changed my /etc/dhcp3/dhclient.conf file, to include my DNS servers, and some other stuff

Then i put the following in /etc/rc.local
```

ifconfig eth1 down
ifconfig eth0 down
dhclient -r eth0
ifconfig eth0 192.168.100.60 netmask 255.255.255.0 up
route add default gw 192.168.100.1
ifconfig eth0 essid "OURHOUSE"
ifconfig eth0 key FB622816FC
iwconfig eth0 mode Managed
dhclient eth0
```

And, as i said, it still hangs for a little while when booting, when the status bar is 3/4 the way done. Apart from that, it works, and it doesn't take 5 minutes to load my icons and panels, **when the wireless router is on**, i haven't yet tried with it off.

---

