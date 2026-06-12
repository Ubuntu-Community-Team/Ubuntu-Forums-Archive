---
title: "Network autoconfiguration failed &amp; simple (local) dev server setup"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Palu on 2009-06-23
**Issues solved: I had the ethernet cable unplugged. Since I wasn't sure how to correct things, I simply reinstalled the OS.**

During an Ubuntu Server 9.04 install, I got the error message...

```
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.
```

I selected the option...

```
Do not configure the metwork at this time
```

From what I can tell, this is not an intended result from the tutorial site I'm using. :D I don't know what it means, but I suspect it means I don't have network connectivity. This is my first attempt in a few years outside the GUI, so I'm not even sure how to test that.

Hardware:
-An Everex cheapo machine from Walmart (originally with gOS).
-a 2Wire router
-my personal PC (runs Vista, sorry :()

Selections during setup included LAMP and Samba.

Goals:
-use the server as a file server
-AND a dev server for testing php scripts. I'll need to FTP to it from my personal PC, I imagine. FTP from external locations would be nice, but I suppose I don't have a static IP address. If I get one, that will be later.
-It only needs to be able to be accessed within my local network.

Thanks :popcorn:

---

### Post by Bachstelze on 2009-06-23
The message you're getting simply means that the installer couldn't find any DHCP rserver running on your network. If you are sure your router has DHCP enable, this could indeed be a connectivity problem. Do you know whethet your router has DHCP enabled?

---

### Post by Gone fishing on 2009-06-23
Were you connected to a router or something that would assign an IP address? If not you should have done it manually and given it an IP address during install.

However, you could give it an IP address now vi /etc/network/interfaces and make it look something like

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

You could test its current state with ifconfig.

---

### Post by Palu on 2009-06-23
Both computers are plugged into my router which is 2Wire brand (see hardware list).

output of ifconfig:
```
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:0
RX bytes:1040 (1.0 KB  TX bytes:1040 (1.0 KB)
```

I Googled DHCP and read a wiki article to see basically what it is and then Googled "2Wire DHCP" and it seems to be a basic function of that model router... from what I can tell.

---

### Post by Palu on 2009-06-23
Shoot... the ethernet cable MIGHT have been loose, but I might have just knocked it when looking just now. I made sure the cable was secure and rebooted. ifconfig gives the same output. Granted, it might not have been loose in the first place.

---

### Post by Palu on 2009-06-24
Ethernet cable was loose... Reinstalled the OS and it all works now. :popcorn:

---

