---
title: "Network interface eth0 not found"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by dileepdinesh on 2010-03-23
Hi all,
       I installed ubuntu 8.10. I setup my network and ran the system update. After updating, the network interface is not found. The network applet shows "no network devices are found".

These are the results for ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10874 (10.8 KB)  TX bytes:10874 (10.8 KB)

These are the results for "cat /etc/network/interfaces"

auto lo
iface lo inet loopback

Somebody help me :P

---

### Post by OriginalName on 2010-03-23
Hi,

Try running ```
dmesg | grep eth
``` in the terminal and see what the output is - Something like this will show the hardware is being recognized properly - ```
[    1.862368] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection

```If it's not recognized then there could be a hardware issue (I know it shouldn't be changed after an update!) if it is showing then try ```
ifconfig eth0 up
```(By system update do you just mean an apt / synaptic update or a full upgrade (e.g. 9.04 to 9.10) - If you've done a full upgrade it might be best to backup your files and do a clean install.

---

### Post by Iowan on 2010-03-23
**sudo lshw -C network** (run from a terminal) is another tool that provides valuable information about your interfaces.

---

