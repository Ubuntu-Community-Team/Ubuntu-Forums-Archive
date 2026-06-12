---
title: "Unable to add resolution on laptop"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by vmayank on 2011-07-08
Hi All,

I am not sure if my laptop supports a higher resolution but xrandr gives the following output:

xrandr
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 

Can someone help me setup a better resolution? I think my laptop supports HD High resolution so should be 1366x1268 preferably..

Thanks
Mayank
i5, HP 630, Ubunutu 9.04

---

### Post by LowSky on 2011-07-08
Your still using 9.04? It isn't supported anymore. The current supported version are 10.04(LTS), 10.10, and 11.04.

We need more info about your laptop. It comes in many different flavors and it has about 5 different graphic card choices.

[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3740644-3955548-5086782.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3740644-3955548-5086782.html)


If you could please give us the output of this terminal command

```
lspci
```

---

### Post by vmayank on 2011-07-09
I re-checked - I am on ubuntu 9.10 - I think that isn't supported either anymore....

Thanks for replying! Here is the output of the command:

user@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Device 1c3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1c2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1c20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1c10 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Device 1c14 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Device 1c18 (rev b4)
00:1d.0 USB Controller: Intel Corporation Device 1c26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 1c03 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1c22 (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

Regards
Mayank

---

