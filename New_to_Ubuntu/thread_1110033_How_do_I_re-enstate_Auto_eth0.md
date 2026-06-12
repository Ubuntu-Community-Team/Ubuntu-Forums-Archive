---
title: "How do I re-enstate Auto eth0"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Aerotha on 2009-03-29
Hey,
I mis-clicked and deleted auto eth0 in my Connections wizard, now I can't seem to pick up any nic cable connections, how do I correct this?

Thanks.

---

### Post by dfm21 on 2009-03-29
```
sudo vim /etc/network/interfaces
```
add line
```
auto eth0
```
reconnect with
```
ifdown eth0
ifup eth0
```

---

### Post by Lisa Y on 2009-03-29
Hello

To re-instate your Auto eth0, go ahead and do the following:

System> Pref> Network Configuration

When the screen pops up
1. Click Add
2. Connection Name "Auto eth0"
    1. Check Connect Automatically
    2. Click System Setting
3. In the Wired Tab, ensure your MAC is there, and set the "MTU" to Automatic

That should do for you

Cheers

---

### Post by Aerotha on 2009-03-29
> **Lisa Y said:**
> Hello

To re-instate your Auto eth0, go ahead and do the following:

System> Pref> Network Configuration

When the screen pops up
1. Click Add
2. Connection Name "Auto eth0"
    1. Check Connect Automatically
    2. Click System Setting
3. In the Wired Tab, ensure your MAC is there, and set the "MTU" to Automatic

That should do for you

Cheers
I can't just have it auto find the MAC?

---

### Post by Aerotha on 2009-03-31
Now when I click the internet thing (Wireless bars) it says Wired connection: Device not managed

---

### Post by Aerotha on 2009-04-04
anyone?

---

### Post by Iowan on 2009-04-04
[This]("http://ubuntuforums.org/showthread.php?t=1114474") thread may have helpful information about the "managed" problem.

---

### Post by Aerotha on 2009-04-05
> **CyberMando said:**
> If /etc/NetworkManager/nm-system-settings.conf contains 
[ifupdown]
managed=false
which it does by default, and /etc/network/interfaces contains wlan0 network-manager will see your wlan0 as unmanaged.

Means if I go there and change it to true it will work?

---

### Post by Aerotha on 2009-04-11
so that didn't work :S

---

