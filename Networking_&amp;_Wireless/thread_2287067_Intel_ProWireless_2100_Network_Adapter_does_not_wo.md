---
title: "Intel Pro/Wireless 2100 Network Adapter does not work in Lubuntu 15.04"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by penuel1310 on 2015-07-16
Intel Pro/Wireless 2100 Network Adapter does not work in Lubuntu 15.04

lspci output

```

Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

iwconfig output

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

dmesg | grep ipw2100 output

```

[  389.696140] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[  389.696144] ipw2100: Copyright(c) 2003-2006 Intel Corporation

```

lsmod | grep ipw2100 output

```


ipw2100                77824  0 
libipw                 36864  1 ipw2100
cfg80211              462848  2 libipw,ipw2100


```

---

### Post by chili555 on 2015-07-16
We'd also love to see:```
dmesg | grep ipw
rfkill list all
```Thanks.

---

### Post by penuel1310 on 2015-07-17
Hi chili555, there were no output after running the following code: 
```
 
dmesg | grep ipw 
rfkill list all

```

---

### Post by chili555 on 2015-07-17
Let's go back to basics:```
lspci -nnk | grep 0280 -A2
```One of the pieces of information it will reveal is the bus number. Here is an example from my machine:> [COLOR="#FF0000"]03:00.0[/COLOR] Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239]
<snip>I'd also like to see what the PCI bus is doing, so please run and post:```
dmesg | grep 03:00
```Of course, substitute the first four digits of the bus number you found if not 03:00.

Thanks.

---

### Post by penuel1310 on 2015-07-17
Here are the outputs from the commands:

lspci -nnk | grep 0280 -A2 (output)
```

02:07.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04) 
Subsystem: Intel Corporation Device [8086:0000]

```

dmesg | grep 02:07 (output)

```

[    0.079327] pci 0000:02:07.0: [8086:1043] type 00 class 0x028000
[    0.079347] pci 0000:02:07.0: reg 0x10: [mem 0xd0002000-0xd0002fff]

```

---

