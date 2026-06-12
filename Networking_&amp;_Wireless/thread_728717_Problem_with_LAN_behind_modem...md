---
title: "Problem with LAN behind modem.."
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by silentlion on 2008-03-19
Hi All

I have a setup in which my PC is connected to a modem I (this is acting as a DHCP server) and WAN side of this modem I(here it is acting as a PPPoE client) is connected to PPPoE server which is running on ppp0 interface of Linux system....eth0 interface of this Linux box (acting as a DHCP client) is connected to another modem II(acting as a DHCP server) for Internet connectivity...hope the setup is clear by now...huh..!!!

Problem is when I am running ping from my PC to any internet address, no response is coming. On the other hand when I m running ping from my modem I to any of the internet address, ping response is coming...

Note: PC can ping modem II. IP forwarding is enabled.

Please help..!!!

---

### Post by SpaceTeddy on 2008-03-19
mhm - not sure what your setup it here... 

Internet <---> modem <---> ubuntu box <---> modem <---> ???

does it look like that ? or what would change in that picture if i am wrong... ?

besides that my guess is that either the routing or address translation is not working correct, dropping the pakets or the replies not being able to be routed back to you...

---

### Post by mips on 2008-03-19
I suspect a routing issue. Probably using the wrong default gateway.

Post output of **route -n** here.

---

