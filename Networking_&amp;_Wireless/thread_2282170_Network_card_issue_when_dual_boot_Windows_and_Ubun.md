---
title: "Network card issue when dual boot Windows and Ubuntu"
date: 2015-06-12
forum: Networking &amp; Wireless
---

### Post by Christian_Sandberg on 2015-06-12
For a mounth ago or two then I testing Wlan in Windows 8.1. After that I think I am getting problem when I rebooting computer and want to boot into Ubuntu instead. The network is down and I can't access it for about 20 minutes.
After that I can reboot into Ubuntu without any problem. But when I want to reboot into Windows again then I get the same problem and after 20 minutes the network is on.
It is sounds like the card has got a memory with a parameter that do that. I think that only thing I can do is to reinstall Windows 8.1.
I have met this problem before.

I think this problem has followed me several of years. My computer is several of years old. It is AMD 64 and the network card is Nforce 4 I think.
I can choose to boot into Windows 8.1 or Ubuntu 15.04 and I am updating it daily.
Sometimes I am reinstalling it all both Ubuntu and Windows then I've got not any problem.

---

### Post by wyliecoyoteuk on 2015-06-12
Probably a firmware issue, the card's firmware is left in a condition that the OS does not expect. Some cards load their firmware and configure it at boot time, and do not refresh it when warm booting (restart)
If you cold boot (shutdown completely, and then start from cold) it will probably work straight away.

---

### Post by Christian_Sandberg on 2015-06-12
Thank you for the answer!
I have not testing that yet.
Maybe it is that.
I have also thinking about the cards firmware. It would be a pleasure if it is some kind of commands so I can directly reset the card.

---

