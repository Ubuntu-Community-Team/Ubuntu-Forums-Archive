---
title: "VPN with WiFi vs Ethernet"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by mshade on 2007-04-24
My first post here :)

Alright, I've succeeded in getting the VPN plugin for NetworkManager, however I've encountered a problem:

I can't connect to the VPN when I'm using wireless.  If I plug in using ethernet, no problems, but it just says "VPN Connection Failed" if I try to connect while on wifi.

Perhaps it doesn't know which connection is active at this point?  I have a feeling I can specify something in the "Custom PPP Options..." field, but not sure what.

Pointers or ideas?

---

### Post by munozm on 2007-04-24
I don't know if this will help, but I have the Cisco VPN client installed.  I noticed that now in Feisty, I have to shutdown the Ethernet interface for the VPN to work over the wireless interface, even if the Ethernet interface isn't connected.

sudo ifdown eth0

Good luck finding your answer.

---

### Post by mshade on 2007-04-25
Thanks, munozm, but that's not doing it for me. :(

I even tried commenting out the section in /etc/networking/interfaces for eth0 and restarting -- no love.

Anyone else have ideas?

---

