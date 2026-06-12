---
title: "Wireless card won't work in Intrepid"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by obliviousdream on 2009-07-01
I tried installing the driver, It's a Broadcom, and the driver is there and "enabled", but it won't connect.

I ran iwconfig, and got this:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

I don't know what's wrong. It's installed, but it won't work >_>

---

### Post by TeoBigusGeekus on 2009-07-01
If you have access to wired connection on your pc, replace gnome-network-manager with wicd
```
sudo apt-get install wicd
```
It's much better on wireless connections.

---

### Post by obliviousdream on 2009-07-01
It won't let me install it because it can't find it. 

Also, it won't let me install the .deb file because it "conflicts with Network-manager"

Help please...?

---

