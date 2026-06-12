---
title: "Network Settings - need the command lines please !"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by kelbed on 2007-11-30
Hi all,

The problem is simple : when i change the network settings dns servers, i save it .. after a while the  old dns server ips come back, of course i notice it because internet stops working. I keep coming back to that tool, and removed all settings then saved news ones.. it doesnt help. The old damn ones keep coming back. 
I tried to look at the doc which is ..err.. well, very limited.

Could someone post the magical lines ? 
Thanks.

(i have ubuntu 7.10 on a hp laptop)

---

### Post by 11hjpphty76lkjj on 2007-11-30
If you edit the /etc/network/interfaces file you should be able to fix it. should look something like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```eth0 would be your network adapter.  if you run

```
ifconfig
```it will tell you the correct name.

then run 

```
sudo /etc/init.d/network restart
```

Hope this helps!

A

---

