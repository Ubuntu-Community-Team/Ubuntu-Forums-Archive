---
title: "dell inspiron n 5010 realtek, wifi not working suddenly"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by mithil_jain on 2013-10-02
Hi , 

I have this dell Inspiron N5010 with realtek card , my wifi was working fine but suddenly it has stopped working i did try many forums with same errors , bt trying those made it even worse!!

whn i do rfkill list all there is no report for wifi 

only bluetooth comes in :

Inspiron-N5010:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

no info on wifi

i have already done changes in boot to change wifi switch to none ..

Please help me on how to get the wifi detected and started

---

### Post by praseodym on 2013-10-02
Please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```

---

