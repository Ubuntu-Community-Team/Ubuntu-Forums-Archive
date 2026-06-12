---
title: "Local connection is slow"
date: 2020-05-15
forum: Networking &amp; Wireless
---

### Post by amalyshev on 2020-05-15
I have a Ubuntu server 18.04. It also serves as a router and access point for my home network. The internet speed is just fine - upload/download speed is 93 Mb/s. But when I try to copy a file from the server to my local machine using scp command in terminal, the speed is just around 2.2 Mb/s. I also installed Samba server and have same problem - download speed is just a few megabytes. Even though WiFi reports 1.3 Gb/s connection. Hard Drive is Samsung SSD M.2. Read/Write speed is lightning fast:
```
amalyshev@al-serve:~$ sync; dd if=/dev/zero of=tempfile bs=1M count=1024; sync1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.330722 s, 3.2 GB/s
amalyshev@al-serve:~$ dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.0894196 s, 12.0 GB/s
amalyshev@al-serve:~$ sudo /sbin/sysctl -w vm.drop_caches=3
vm.drop_caches = 3
amalyshev@al-serve:~$ dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.417582 s, 2.6 GB/s

~: $> scp -P 2448 -i keys/amalyshev.key amalyshev@${AL_IP}:tempfile .
tempfile                                        2%   29MB   2.2MB/s   07:24 ETA

```
Where to look for the problem? I've been trying to fix for more than a year, spent countless number of nights, but with no result. I am lost.

---

### Post by praseodym on 2020-05-15
Hardware? Please show
```

lspci -nnk | grep -iA2 net
lsusb
ifconfig -a
iwconfig
lsmod
```
Internal speed is slow on both LAN and WLAN?

---

### Post by amalyshev on 2020-05-15
> **praseodym said:**
> Internal speed is slow on both LAN and WLAN?
If I understood you correctly, it is slow only on LAN. I use this Ubuntu server as an Access Point and when I connect to it from my MacBook internet (WAN?) up/down speed is 93 Mb/s, which is much faster compared to that when I try to download something from the server itself, which is weird.

Commands result is attached. I removed actual IP and MAC addresses for security.

---

### Post by amalyshev on 2020-05-22
I check with a PC that has a Ethernet adapter. With WiFi the speed is the same ~4-5 Mb/s down and 60 Mb/s up, but with a Ethernet cable it is as expected - ~100Mb/s. Looks like I am having an issue with WiFi setup.

I was trying to make WiFi work for a couple of years. I replaced two Wi-Fi cards because they did not have a Linux driver. I specifically bought a very expensive QNAP Dual-Band Wireless PCIe Expansion Card. I am connecting to it in 5GHz band and my Mac reports 1300 Mbps. Still having speed issues. Whoever is saying Linux is easy to use is not telling the truth.

---

### Post by amalyshev on 2020-05-26
No one can help? I noticed that sometimes network read speed goes up to a reasonable numbers, close to 30 Mb/s. But once I reconnect to the network drive, the speed goes back to 2-3 Mb/s. I was not able to figure out what triggers this. Any idea where to look?

---

