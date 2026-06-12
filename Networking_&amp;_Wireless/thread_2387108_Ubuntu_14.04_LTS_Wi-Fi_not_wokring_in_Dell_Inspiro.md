---
title: "Ubuntu 14.04 LTS: Wi-Fi not wokring in Dell Inspiron 7577"
date: 2018-03-14
forum: Networking &amp; Wireless
---

### Post by santhoshsivan on 2018-03-14
Hello All,

I am new to Ubuntu. I have installed Ubuntu 14.04 LTS (ubuntu-14.04.5-desktop-amd64) in my new Dell Inspiron 15 7000 Gaming Series - 7577 laptop, with the dual boot option of Windows-10 Pro (64 bit).

When I installed ubuntu 14.04 LTS, my Wi-Fi is not working. But it works fine in the Windows OS.

Here are the details of my Wi-Fi:
Manufacturer: Intel Corporation

Description: Intel(R) Dual Band Wireless-AC 8265

Driver version: 20.10.1.3

Can anyone please help me in making the Wi-Fi work for in my Ubuntu 14.04 LTS.

Thanks in advance.

---

### Post by chili555 on 2018-03-14
Please open a terminal Ctrl+Alt+t and run:```
lspci -nnk | grep 0280 -A3
rfkill list all
dmesg | grep iwl
uname -r
```Please post the result.

---

### Post by santhoshsivan on 2018-03-15
santhosh@santhosh:~$ lspci -nnk | grep 0280 -A3
3c:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0050]
3d:00.0 Non-Volatile memory controller [0108]: Toshiba America Info Systems Device [1179:0116]
    Subsystem: Toshiba America Info Systems Device [1179:0001]
santhosh@santhosh:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
santhosh@santhosh:~$ dmesg | grep iwl
santhosh@santhosh:~$ uname -r
4.4.0-116-generic


These are the result when I ran it. Please help me in what should i do further in getting the Wi-Fi working.

---

### Post by chili555 on 2018-03-15
Please check here: [https://askubuntu.com/questions/858546/wifi-not-working-intel-on-hp-spectre-x360-13/859263#859263](https://askubuntu.com/questions/858546/wifi-not-working-intel-on-hp-spectre-x360-13/859263#859263)

---

### Post by santhoshsivan on 2018-03-16
Thank you very much for your help. Wi-Fi is now working fine.

---

