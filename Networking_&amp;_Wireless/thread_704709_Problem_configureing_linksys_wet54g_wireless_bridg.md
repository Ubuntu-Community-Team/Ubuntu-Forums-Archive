---
title: "Problem configureing linksys wet54g wireless bridge"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by Programmerer on 2008-02-22
I have a Linksys WET54G, and I had it configured until something happened when I changed some settings (from firefox). I had to reset all settings, but now I can't connect (to configure) to my WET54G bridge.

I don't know if the default ip-address I found is wrong, so I would be happy if someone can post it.
It's version is 1.1, I don't exacly know what firmware version it have.


Here is what I have been trying:

1. I reset my WET54G bridge
2. I plug in cables to my machine(and power)
3. I open System>Administration>Network and change it to static ip:
    ip-address: 192.168.1.22 (I don't know that too much with network, but I think it have to be different from the ip of my bridge, and 192.168.1.225 is what I believe is the default ip-address)
    Subnet Mask: 255.255.255.0
    Gateway address: 192.168.1.1
4. Reboot my computer
5. After login, I type 192.168.1.225 in the address in the location bar in firefox
6. Firefox can't reach server...
7. I get stuck
8. Find my ten meters long network cable and plug it in so I can get internet
9. Post this thread



I hope anyone know what to do.

---

### Post by nixscripter on 2008-02-22
Try just a broadcast ping, in case the IP is wrong. Open a terminal and type: ```
 ping -b -c 1 192.168.1.255
``` and see if you get "REPLY FROM 192.1268.1.225" or whatever. There should be either nothing (in which case your computer is having a problem or your router is stupid), or one response, which is its IP address.

---

