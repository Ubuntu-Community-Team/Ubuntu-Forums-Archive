---
title: "[SOLVED] Packets are lost between NIC and app layer"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by kungmidas on 2007-11-26
We have made a custom software for routers. To spare you the details, basically what we want to do is to send a IPv6/UDP/SIP response packet from a router to an Ubuntu computer... However we have some problems accomplishing this =/

- The packet is sent from the router properly, and it arrives at the computer NIC without any error according to Wireshark. IPv6 address, ports etc is all correct, so is SIP content, packet lengths and everything else.

- However, the SIP software running on the computer does not receive anything at all. (It does, however, when sending something to it from the same computer, so we have verified that that works and that it listens to the correct port).

- iptables are all empty and has only ACCEPT policies. (input/output/forward, filter/mangle, iptables/ip6tables. nat not installed)

So, it appears that the packet is discarded somewhere between NIC and the application layer. We have tried to see if it reaches iptables, but we can't get the logging to work (have added a bunch of "-j LOG" in different tables but nothing shows up in /var/log/messages).

Some theories of what might cause this, is:

- The packets source IP address is not actually from the router that has that IP. Maybe the kernel does some MAC/IP checking, finds that they don't match somehow and discards the packet?

- We disable the checksumming in the UDP header by setting the checksum to 0. Maybe the kernel doesn't like packets with checksumming disabled?


Any ideas, suggestions or help is appreciated!

Thank you!

---

### Post by kungmidas on 2007-11-27
We found that IPv6 require UDP checksumming being enabled... We enabled it and now it works... =)

---

### Post by loell on 2007-11-27
thanks for posting this, even if no one was able to help you, as this might be of great use , to someone doing a similar setup you posted above. :)

---

