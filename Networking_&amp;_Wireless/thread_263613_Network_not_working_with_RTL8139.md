---
title: "Network not working with RTL8139"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by davidviranyi on 2006-09-23
I have installed UBUNTU and the devices list shows me my RTL8139D network card but if I do ifconfig there is no eth0. If I boot with an old DEMOLINUX disk the network works OK.

---

### Post by happy-and-lost on 2006-09-24
What's the ifconfig output?

---

### Post by TTL on 2006-10-01
I had the same problem with Dapper. The solution was a manual **modprobe 8139too**. With Hoary this was not necessary.

---

