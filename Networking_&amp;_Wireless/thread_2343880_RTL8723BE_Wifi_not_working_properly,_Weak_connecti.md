---
title: "RTL8723BE Wifi not working properly, Weak connection status and very very slow speed"
date: 2016-11-20
forum: Networking &amp; Wireless
---

### Post by Divyansh_Kumar_Sin on 2016-11-20
My wifi shows very weak connection on my ubuntu and is very slow if connected to the network.
Also the hotspot made by my ubuntu doesnt work as well.

All the problems however do not exist on the windows 10 OS which I have dually booted as the secondary OS.

lspci -vnn grep | Network gives this

```

13:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]

```

---

### Post by howefield on 2016-11-20
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by jeremy31 on 2016-11-20
Is the computer made by HP?
If so see [https://ubuntuforums.org/showthread.php?t=2327483&p=13502516#post13502516](https://ubuntuforums.org/showthread.php?t=2327483&p=13502516#post13502516)

---

### Post by praseodym on 2016-11-20
Please try:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot? Not better? Then replace **ant_sel=1** with **ant_sel=2**

---

### Post by Divyansh_Kumar_Sin on 2016-11-23
@[COLOR=#000000]praseodym[/COLOR]Thanks for the commands. Now I can see the wireless networks properly and fully.

But i am still unable to use it as hotspot.
I switch it on to be used as hotspot but it doesnt show on my phone.
[COLOR=#000000][/COLOR]

---

### Post by wildmanne39 on 2016-11-23
Please mark this thread solved and start a new one for the following issue:
>  I switch it on to be used as hotspot but it doesnt show on my phone.
they are separate issues.
Thanks

---

