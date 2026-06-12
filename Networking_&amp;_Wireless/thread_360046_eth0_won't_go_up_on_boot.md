---
title: "eth0 won't go up on boot"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by drpepper on 2007-02-12
I am fairly new to this so bare with me!

I used sudo modprobe r1000, brought it up with ifconfig eth0 up, acquired a ip address with dhclient, and then edited /etc/modules and added r1000.

the card works perfectly after this and i can ping my router. But after rebooting, I have to perform the ifconfig eth0 up and dhclient every time, how can I make it come up on boot?

Thanks for reading guys

Nick

---

### Post by Iowan on 2007-02-12
Check the **System>Administration>Networking>Connections**  to verify that eth0 is enabled (probably will be). **The /etc/network/interfaces** file should have a section similar to ```
iface eth0 inet dhcp
auto eth0

```

---

### Post by drpepper on 2007-03-13
Hey, just wanted to let u know that your suggestion worked! Thanks for your help!

---

