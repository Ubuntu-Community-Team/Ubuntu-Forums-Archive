---
title: "Weird network problem in 22.04"
date: 2024-01-25
forum: Networking &amp; Wireless
---

### Post by Mchel_Na_bPob on 2024-01-25
I have a weird network problem in 22.04. Every so often my internet seems to drop. When it happens I can ping my router and 8.8.8.8 but I can't ping either of my DNS servers and therefore can't resolve any hosts. The only way to resolve this is to turn off wifi and turn it on again. Or I can just wait a while. It only happens on this laptop and the rest of my network which is extensive works ok. I've followed all advice as to apt dist-upgrade.

---

### Post by just-rj on 2024-01-27
> **Mchel_Na_bPob said:**
> I have a weird network problem in 22.04. Every so often my internet seems to drop. When it happens I can ping my router and 8.8.8.8 but I can't ping either of my DNS servers and therefore can't resolve any hosts. The only way to resolve this is to turn off wifi and turn it on again. Or I can just wait a while. It only happens on this laptop and the rest of my network which is extensive works ok. I've followed all advice as to apt dist-upgrade.

I am having the same issue. It started a few days ago. Except I'm on 20.04.6 LTS and Ethernet. It drops a few minutes after waking or booting. It reconnects a minute or two later. Very annoying because some web services don't reconnect automatically. I've tried resetting the router/gateway/modem and cycling Ubuntu Wired network off and back on. No joy.

---

### Post by foxsquirrel on 2024-01-28
> **Mchel_Na_bPob said:**
>  It only happens on this laptop 

Only sane way to find out what is going on is to buy another drive for the laptop and back peddle your version to 20.04 LTS and test. If that works perfectly then you have an issue with 22.04.
 Problems like that are very difficult to track down, get a baseline first by using a known working OS and go from there.

---

### Post by avidandrew on 2024-02-01
When the dropout happens, do you see anything in /var/log/kern.log or /var/log/syslog? Does the wireless interface still have an IP address when this happens?

---

### Post by chili555 on 2024-02-02
> **Mchel_Na_bPob said:**
> I have a weird network problem in 22.04. Every so often my internet seems to drop. When it happens I can ping my router and 8.8.8.8 but I can't ping either of my DNS servers and therefore can't resolve any hosts. The only way to resolve this is to turn off wifi and turn it on again. Or I can just wait a while. It only happens on this laptop and the rest of my network which is extensive works ok. I've followed all advice as to apt dist-upgrade.Please do:

```
sudo apt purge bcmwl-kernel-source
sudo modprobe -r wl

```
Is there any improvement?

May we also see:

```
sudo dmesg | grep 8821
```

---

