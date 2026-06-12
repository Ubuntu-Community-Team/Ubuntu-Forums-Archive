---
title: "Wol on wired and all traffic on wifi"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by huangyingw on 2017-11-18
My server has two NICs:
 
enp4s0 --> wire connect to a very weak wifi-wired converter(this will convert the wifi to ethernet connection). I only use it for wol(wake on lan), since once the data traffic in high speed, the wifi-wired converter would die...
wlp3s0 --> my pcie wifi NIC, the os support not so well, after pm-suspend, could not recover wifi connection, so, wol on it not work, but I want all the data traffic go through this.
My plan is wol packet to enp4s0 to wake it up, and ssh through enp4s0, to login and reboot.
And wait for rebooting and once wlp3s0 is connected, I could ssh through wlp3s0, and use rsync to copy data through wlp3s0.
I should not rsync through enp4s0, for behind it is a very weak wifi-wired converter, high volume of data traffic would make it die quickly.
How to achieve this ?
Bellow is my interfaces ```
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp4s0
iface enp4s0 inet static
address 192.168.2.125
```
But I find I still need to manually run 
```
route del -net 192.168.2.0/24 dev enp4s0
```

---

