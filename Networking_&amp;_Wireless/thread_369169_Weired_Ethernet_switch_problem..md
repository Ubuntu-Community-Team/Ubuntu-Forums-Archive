---
title: "Weired Ethernet switch problem."
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by DoktorNo on 2007-02-24
Hi there,

I have a computer room, with five machines, and one Edubuntu LTSP server, who also acts as router, two computers with Xubuntu, and two thin diskless clients. All together are connected to one 100Mbit/sec switch and secondary NIC. The ISP cable modem is connected to primary NIC of server. Routing goes fine, also the LTSP services.

My problem is, that during the booting one of the thin clients (and after the logging-in), the network transfer from server to client is tremendosly SLOW! The solution is to simply disconnect the rest of machines from switch. I noted, that even if they are turned off, their NIC are active (propably due to the Wakeup-on-LAN feature).

Can this cause the switch to this erratic behaviour?

---

### Post by mips on 2007-02-24
Hard to say. Try using a sniffer to analyse network traffic.

---

### Post by DoktorNo on 2007-02-24
This case is very weired, because these computers (that seems to be "blocking" the LAN) are TURNED OFF!! The activity LEDs are lighted up, because of WOL (maybe).

---

### Post by mips on 2007-02-24
In that case i have no idea. Is the switch a managed or unmaged switch. If managed you could probably have a look at its settings.

---

### Post by DoktorNo on 2007-02-24
It is a unmenaged switch. Yes, I know, Its a weired case. I'll try with another switch or hub.

---

### Post by mips on 2007-02-24
Another option would be to go into the pc/client BIOS and disable WOL to see if it makes a difference.

---

### Post by DoktorNo on 2007-02-24
I will also try this. Thanks for attention!

---

### Post by DoktorNo on 2007-02-25
I have solved this! Guess how? I simply took another power supply, from old 10Mbit hub. And it works, without any problems; the PXE is loading the LTSP very quickly, and meanwhile the Internet is accessible by the rest by routing.

Propably the propertiary power supply was giving some interferences, that were simply knocking down the switch...

---

### Post by mips on 2007-02-25
Glad to hear you sorted it out. I would have never suspected the PSU.

---

