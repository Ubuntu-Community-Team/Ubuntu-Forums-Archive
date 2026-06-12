---
title: "wireless sniffer for msn messenger"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by probing_tool on 2008-09-24
hi all, 
How can I sniff all the MSNMessenger communication that is going through my WEP encrypted wireless network at home using UBUNTU?

I tried installing Kismet. But couldn't figure out how to make it do what I need. :(

p.s,
I'm new to linux... so bare with me :P

---

### Post by willca on 2008-09-24
if you got tcpdump installed then use that as such...

sudo apt-get install tcpdump

tcpdump -nvvv -i wlan0 host 

Or you can use wireshark if you prefer gui.

sudo apt-get install wireshark

---

