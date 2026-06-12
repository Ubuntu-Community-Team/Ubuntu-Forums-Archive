---
title: "Wireless driver installed but won't work!"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by evy2 on 2013-09-19
Hi everyone, 

I got a new windowslaptop from work and after installing Linux 13.04, I had to install the wireless driver. So I've done everything that needs to be done, but it still won't work. Hereby my terminal output:

```

evy@Boltop:~$ ndiswrapper -l
bcmwl6 : driver installed
    device (14E4:4359) present (alternate driver: bcma)
evy@Boltop:~$ sudo depmod -a
evy@Boltop:~$ sudo modprobe ndiswrapper
evy@Boltop:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether d4:be:d9:68:6d:24 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::d6be:d9ff:fe68:6d24/64 scope link 
       valid_lft forever preferred_lft forever
evy@Boltop:~$ iw config
nl80211 not found.
evy@Boltop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

Conclusion: still no wireless!

I really hope someone can help me, because working in windows is no option for me! Thanks in advance!

---

### Post by praseodym on 2013-09-19
Hi,


after uninstalling ndiswrapper```

sudo apt-get remove --purge ndiswrapper* ndisgtk
```
please show:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
If it really is device **14E4:4359** you should install the Broadcom-STA driver:

Update-Manager -> "Additional drivers"

via cable connection.

---

### Post by evy2 on 2013-09-19
Hi, 

Thank you very much for your answer. Unfortunately now I get the error that he can't find the packages purge and ndiswrapper*. 

Also I don't have acces to wired network. There's only wifi around here. I'm using Windows to go online... Of course, I can download Broadcom-STA and put it on a usb stick.

---

### Post by praseodym on 2013-09-19
Please show:
```

uname -a
```
I can give you the right links afterwards.

---

### Post by evy2 on 2013-09-19
Here you go:

Linux Boltop 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686 i686 i686 GNU/Linux

Thanks!

---

### Post by praseodym on 2013-09-19
Download these files and save them in "Downloads":

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.8.0-19_3.8.0-19.30_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.8.0-19_3.8.0-19.30_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.8.0-19-generic_3.8.0-19.30_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.8.0-19-generic_3.8.0-19.30_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_i386.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
```
Load the driver and check wireless:
```

sudo modprobe -v wl
```
If it works update your system:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic build-essential
```

---

### Post by evy2 on 2013-09-19
Super, it's working, finally! Thanks so much! You're my hero!

---

