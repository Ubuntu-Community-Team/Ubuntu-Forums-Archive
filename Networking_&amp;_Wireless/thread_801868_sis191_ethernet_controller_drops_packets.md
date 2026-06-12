---
title: "sis191 ethernet controller drops packets"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by dupin on 2008-05-21
I have an Asus P5S series motherboard (can't remember exact model) with an integrated sis191 Gigabit Ethernet Controller. 
When I first installed hardy, it detected the card but it did not detect the "link" status of the card (LEDs in the card were on, so it was not a hardware issue). I solved this problem by following the instruccions here: 
[http://ubuntuforums.org/showthread.php?t=188060]("http://ubuntuforums.org/showthread.php?t=188060")

I had to modify the module source and re-compile it a couple of times and I got connected. The line I added is this:

```
{ "Anything",  { 0x4d, 0xd020 }, LAN, 0 },
```

When I connected the PC to the campus network, I got a DHCP lease from the server but could not connect to internet (can't browse, no ping) and scp is not working in the LAN.
When I connect to a ADSL modem/router I get an IP from the DHCP but when pinging google (for example), I have 30% packet loss and browsing is really slow.

Does someone have a similar issue or a solution to this problem?

Thanks in advance!

---

