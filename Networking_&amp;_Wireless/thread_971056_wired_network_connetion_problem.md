---
title: "wired network connetion problem"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by kapetus on 2008-11-04
I have a laptop and I installed the UBUNTU 8.10 64bit,
but i can't connect to internet, my network card (wired) gets dhcp IP and nothing else, if i install UBUNTU 32bit i can connect to network instantly.
how can i solve this problem?

---

### Post by Badjaccur on 2008-11-05
I had a similar problem, although I use the 32 bits version of Ubuntu. Both static configuration as setting it to DHCP had no result. What solved my problem was moving the network configuration file to a backup: 

```
cd /etc/network
sudo mv interfaces interfaces.old
```

After a reboot (net restart might have worked too) things went back to normal. Easy to try and I hope it helps anyone else besides me. Good luck!

---

