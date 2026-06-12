---
title: "D-link 131"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by davevr on 2014-03-24
Can someone help me install a driver. It's the infamous d-link 131.

Is i do lsusb I get

Bus 001 Device 005: ID 2001:330d D-Link Corp. 
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 002: ID 26bd:9917  
Bus 008 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so, anyone? I've got the latest Ubuntu. Newly installed today :)

---

### Post by chili555 on 2014-03-24
It uses the driver rtl8192cu that is already present in Ubuntu 13.10. Is it loaded?```
lsmod | grep rtl
```Are there any clues in the message logs?```
dmesg | grep -i rtl
```The driver requires firmware. If it is not installed, the log should complain about it. It is included in the package *linux-firmware* that *should *be installed by default. Let's also see:```
iwconfig
nm-tool
```

We will know more when we see your readings.

---

### Post by davevr on 2014-03-26
This is the answer I get, 

 dave@HAL-3000:~$ lsmod | grep rtldave@HAL-3000:~$ dmesg | grep -i rtl
[    1.836866] r8169 0000:06:00.0 eth0: RTL8168c/8111c at 0xffffc90000620000, 00:26:18:67:73:7f, XID 1c4000c0 IRQ 68
dave@HAL-3000:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


dave@HAL-3000:~$ nm-tool^C
dave@HAL-3000:~$ 


I downladed the driver from the website, unzipped it, and now I'm stuck....

---

### Post by chili555 on 2014-03-26
Let's just try the driver that's already in the kernel:```
sudo modprobe rtl8192cu
dmesg | grep rtl
iwconfig
```

---

