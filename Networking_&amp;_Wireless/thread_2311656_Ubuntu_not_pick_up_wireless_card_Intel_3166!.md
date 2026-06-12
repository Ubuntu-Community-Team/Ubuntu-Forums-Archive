---
title: "Ubuntu not pick up wireless card Intel 3166!"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by lerequin on 2016-01-29
Hey guys. I have some problem with my new laptop, Thinkpad E460. I've been searching for solutions extensively, but alas.
I installed Ubuntu 14.04.3 on it. I have my ifconfig put here. Hope this helps.

```

$ifconfig -a
eth0      Link encap:Ethernet  HWaddr 50:7b:9d:68:a6:71  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::527b:9dff:fe68:a671/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103545496 (103.5 MB)  TX bytes:5605018 (5.6 MB)
          Interrupt:16 Memory:f1200000-f1220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126302 (126.3 KB)  TX bytes:126302 (126.3 KB)

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Intel Corporation Device [8086:3166] (rev 79)

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 003: ID 04f2:b541 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

Hoping for your assistance soon!

---

### Post by jeremy31 on 2016-01-29
Post ```
lspci -nn | grep -A2 0280; modinfo iwlwifi | grep 3166; uname -a
```

---

### Post by lerequin on 2016-01-29
Thanks jeremy31 for your time!

Voila!
```

$ lspci -nn | grep -A2 0280; modinfo iwlwifi | grep 3166; uname -a
01:00.0 Network controller [0280]: Intel Corporation Device [8086:3166] (rev 79)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:522a] (rev 01)
Linux Randi-Thinkpad 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by jeremy31 on 2016-01-30
Installing backports might be the easiest solution ```
sudo apt-get install build-essential linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/12/18/backports-20151218.tar.gz
tar -zvxf backports-20151218.tar.gz
cd backports-20151218
make defconfig-iwlwifi
make
sudo make install
```

Reboot and post ```
dmesg | grep iwl
```

If this works, a kernel update will break wireless and you will have to run the following to get it working
```
cd backports-20151218
make clean
make defconfig-iwlwifi
make
sudo make install
```

Reboot

---

### Post by lerequin on 2016-01-30
Thank you jeremy31! It is working now.

I have no idea what is happening. Since I am a newbie user of ubuntu, could you give me some explanation what went wrong with my laptop and what you did to overcome it.

Merci beaucoup!

---

### Post by jeremy31 on 2016-01-30
The results for ```
modinfo iwlwifi | grep 3166
``` returned nothing and I confirmed with a 3.19 kernel and that means your wifi card isn't supported with the 3.19 kernel however backports are easy to install and contain source code that does support some wifi cards like yours in older kernels.

---

