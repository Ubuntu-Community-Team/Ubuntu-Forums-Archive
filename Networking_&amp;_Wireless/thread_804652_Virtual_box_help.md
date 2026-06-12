---
title: "Virtual box help"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Linux-noob123 on 2008-05-23
My host OS is windows xp . I have installed Ubuntu 7.10 through virtual box .

I have an internet connection without router .Its just a lan cable plugged inside my lan port.

My ip address is say 202.10.19.204
My gateyay is 10.129.19.4

I want to use internet inside Ubuntu. I've read many tutorials but its not making any sense to me . I'm a linux noob . So can you please help me ??

---

### Post by AliTabuger7 on 2008-05-23
I'm saying this assuming that virtualbox behaves similarly in windows, I've only used virtualbox in Ubuntu.

Where it says network for your ubuntu virtual machine, make sure you have "Enable Network Adapter" checked. For adapter type, PCnet-FAST III always works for me. Attatching it to NAT should work.

Also, make sure you have the "Cable Connected".

---

