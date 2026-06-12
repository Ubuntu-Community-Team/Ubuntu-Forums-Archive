---
title: "GUI to running wireshark text mode"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2008-04-15
Hi!
My server is text based (no desktop installed).
I need to analize the traffic whithin my LAN.
I can run wireshark from an Ubuntu-Labtop, but I am afraid I won't get all the traffic.
I am pretty newbie, and I think that I will be able to scan only all packets in my Lan if I use a HUB: If using a switch (which is my case), packets will travel directly form source to destination, and won't de broadcasted.
Am I right? (sorry if not :oops:)
If yes, I would need to run wireshark directly form my server with tshark, but It seems to be quite dificult to manage.
My question: ¿can I access to a running wireshark from another pc with GUI? (something like you do with webadmin, or amuleweb)? i just need to analize all the traffic.
Thanks a lot!

---

### Post by jmvidalvia on 2008-04-15
I think I found the way.
In my server I run:
```
sudo tshark -w - > /home/usr/file -a filesize:30
```
It generates a file I can open later from my laptop with wireshark.
Thanks anyway!

---

