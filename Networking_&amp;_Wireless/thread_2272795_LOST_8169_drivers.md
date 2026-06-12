---
title: "LOST 8169 drivers"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by sachin9 on 2015-04-08
Okay Some friends suggested me to install the r8168 Realtek driver for Ubuntu 14.04 instead of the r8169 (which I previously did).
During the process, I remember executing this command: 'rmmod r8169'. I guess this basically means that my laptop no longer has any wired adapter drivers.
Sadly, the process for installation of the r168 failed, and I am now left with no drivers for the wired connection.
None of the usual commands to detect eth0 (like 'ifconfig -a') are recognizing it, the laptop waits around at bootup for network configuration, and I am frustrated. Any help please?

---

### Post by chili555 on 2015-04-08
Have you tried:```
sudo modprobe r8169
```Any errors or other interesting messages? Is it blacklisted?```
cat /etc/modprobe.d/blacklist.conf
```>  I remember executing this command: 'rmmod r8169'. I guess this basically means that my laptop no longer has any wired adapter drivers.Nope; that just means to unload the existing driver. It doesn't mean to delete it from the system. That command, in itself, wouldn't delete the driver.

---

### Post by sachin9 on 2015-04-08
> **chili555 said:**
> Have you tried:```
sudo modprobe r8169
```Any errors or other interesting messages? 
This shows the error "FATAL: Module r8169 not found"

> **chili555 said:**
> Is it blacklisted?```
cat /etc/modprobe.d/blacklist.conf
```Nope; that just means to unload the existing driver. It doesn't mean to delete it from the system. That command, in itself, wouldn't delete the driver.

It was, but I removed the blacklisting line from the end of the file and then saved it again (And rebooted). I did that before I posted on this forum. No success!

---

### Post by chili555 on 2015-04-09
Let's search for it:```
sudo updatedb
locate r8169
```In my case, it sees:```
/lib/modules/3.16.0-28-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.16.0-29-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/3.16.0-31-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
/lib/modules/[COLOR="#FF0000"]3.16.0-33-generic[/COLOR]/kernel/drivers/net/ethernet/realtek/[COLOR="#FF0000"]r8169.ko[/COLOR]
/usr/src/linux-headers-3.13.11-03131111-generic/include/config/r8169.h
/usr/src/linux-headers-3.16.0-28-generic/include/config/r8169.h
/usr/src/linux-headers-3.16.0-29-generic/include/config/r8169.h
/usr/src/linux-headers-3.16.0-31-generic/include/config/r8169.h
/usr/src/linux-headers-3.16.0-33-generic/include/config/r8169.h

```Compare this to your running kernel version:```
uname -r
```In my case:```
3.16.0-33-generic
```So the module exists in my system.

I wonder if it was renamed from r8169.ko to, perhaps, r8169.bak or r8169.old. If so, simply rename it again:```
sudo mv /lib/modules/3.16.0-33-generic/kernel/drivers/net/ethernet/realtek/r8169.bak  /lib/modules/3.16.0-33-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
```And then load it:```
sudo modprobe r8169
```I will add more suggestions once we learn what you have currently.

---

### Post by sachin9 on 2015-04-09
After 'uname -r', I came to know that my running kernel version was 3.13.0-48-generic.

From 'updatedb' and 'locate', I saw that there was a file called 'r8169.bak' in [COLOR=#000000][FONT=Ubuntu Mono]/lib/modules/3.13.0-48-generic/kernel/drivers/net/ethernet/realtek.

I renamed it to r8169.ko, and rebooted.

However, modprobe still gives 'MODULE NOT FOUND'.

Any reason why this may be happening?

[/FONT][/COLOR]

---

### Post by praseodym on 2015-04-09
Did you run
```

sudo depmod -a
sudo update-initramfs -u
```
before reboot?

---

### Post by sachin9 on 2015-04-10
Its working now!! Thanks!

---

