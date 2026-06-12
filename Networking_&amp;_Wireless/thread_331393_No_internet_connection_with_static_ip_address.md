---
title: "No internet connection with static ip address"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by ctokar on 2007-01-04
Hello,
I am new to Ubuntu. I recently had my ISP give me a static IP address and my internet connection stopped working on my Ubuntu partition (my Windows partition works fine).
Previously it worked fine. I fiddled around with the network settings to no avail. Do my network settings have to be manually set now? 
Regards,
Chris

---

### Post by mojoman on 2007-01-04
Have a look at the file etc/network/interfaces. It should contain, among other things, your IP. Here's a sample of how mine look (I'm currently on my laptop,  running Debian Etch but it's basically the same):

```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
up iwconfig ra0 essid MYESSID
up iwconfig ra0 channel auto # or if you have specified a channel
up iwconfig ra0 key XXX
```

Now, MYESSID should be exchanged for whatever name you have on your essid, and if you have WEP, the key should be entered where the XXX are.

Also, you probably should have a look at the file etc/resolv.conf. It should contain your namesevers, something like this:

```

nameserver 81.26.228.3
nameserver 81.26.227.3
```

Now, if you're going through a router chances are that you should have the router address.

Best regards
/Mojoman

---

