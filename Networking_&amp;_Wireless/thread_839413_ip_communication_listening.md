---
title: "ip communication listening"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by eldragon on 2008-06-24
there is this clock to check in/out employees in a factory. some windows software connects with it throught tcpip.

im planning on reverse engeneer the communication and do a linux native solution based on mysql. 

i doubt the communication is encripted due to the quality of the software, but i might be wrong. anyway.

whats the best solution to listen to that communication traffic in order to figure out how it works? considering what im planning to do is legal here in argentina?

thanks a lot

---

### Post by pytheas22 on 2008-06-24
You can sniff TCP/IP traffic using tcpdump.  Just type:
```

sudo tcpdump -i [interface]
```

and from there you can pipe it out to a packet dump if you want.

If you want a nice GUI (it will really make things easier if you need to look inside the packets), use Wireshark:
```

sudo apt-get install wireshark
```

Keep in mind that depending on the topography of your network (i.e. whether it's switched or not), you'll need to figure out where to place your sniffer to catch all the traffic (or you could poison the ARP cache, but that can cause problems if you don't know what you're doing; I speak from experience).

---

### Post by timcredible on 2008-06-24
wireshark.  it's a full-featured sniffer.  it's in the repos, works great!! as for catching the traffic, either turn port mirroring on on the switch, or plug in a hub (not a switch) between the switch and clock and plug in your wireshark pc in that hub also.  you're not going to hurt the arp cache on the switch, wireshark is just a listener.

---

