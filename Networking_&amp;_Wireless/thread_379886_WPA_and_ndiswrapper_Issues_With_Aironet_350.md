---
title: "WPA and ndiswrapper Issues With Aironet 350"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by mootpoint on 2007-03-09
The airo and airo_cs drivers for the Cisco Aironet 350 Wifi card don't do WPA. So I wanted to go the ndiswrapper route, but I keep getting the following. Any ideas? This is what I get after a fresh boot with the open drivers airo and airo_cs NOT loaded:

root@lapdog:~# ndiswrapper -l
Installed ndis drivers:
netx500 driver present, hardware present 
root@lapdog:~# 
root@lapdog:~# 
root@lapdog:~# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
root@lapdog:~# 
root@lapdog:~# 
root@lapdog:~# 
root@lapdog:~# dmesg | grep ndisw
[17179968.452000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179968.492000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179968.496000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

Nothing of any value in the system logs. I'm running Edgy with the current generic kernel, just made sure I'm all up to date.

Thanks,
m00t

---

### Post by mootpoint on 2007-03-09
Anyone?

---

### Post by rclark68137 on 2007-03-09
Try this instead:

sudo depmod –a
sudo modprobe ndiswrapper

If that works, then 

sudo ndiswrapper -m

so it will load at startup

---

### Post by mootpoint on 2007-03-09
Thanks for the help. Unfortunately, I still get the same error(s) after depmod -a.

doc

---

