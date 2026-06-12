---
title: "not able to see any other computer which is connected to same n/w"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by Yateesh on 2015-10-10
hi, I am a new ubuntu user.(version 14.04). I have installed samba. But I am not able to see any computer which is connected to same n/w.(All other pc's use windows 7 system)

---

### Post by TheFu on 2015-10-10
Ubuntu uses IP and DNS for name resolution.  That means you can use a DNS server or edit /etc/hosts to locate other systems on the network.  Many home routers have DNS servers built-in, so adding the name-to-IP mapping isn't too hard. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

If you want to use some sort of "broadcast" protocol to find some other computer - that is how netbios works - you can setup zeroconf. Be prepared for some downsides with zeroconf. [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
mdns is another method that I've seen used - think that may just be another name for zeroconf.

[https://www.samba.org/samba/docs/using_samba/ch07.html](https://www.samba.org/samba/docs/using_samba/ch07.html) has more options.
For my effort, it is just easier to use static IPs on my LAN and let the /etc/hosts files deal with name resolution.

---

