---
title: "wifi problems on acer aspie laptop"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by thedoctor818772 on 2014-12-13
Hi. I have an Acer Aspire M5 laptop and am running Ubuntu 14.10. I posted a few months ago about problems connecting to wifi and got a resolution. Then machine went in for repair and i needed to reinstall ubuntu and i need to know how to find my post with the explanation of the code on how to fix my issue. Thanks!

---

### Post by chili555 on 2014-12-14
I've looked through all of your prior posts and find nothing about wireless. Let's start from scratch. Let's gather a few details. Please run and post:```
lspci -nn | grep 0280
lsusb
rfkill list all
```Thanks.

---

### Post by moi3 on 2014-12-14
I have a similar problem with my wireless connection on Ubuntu 14.04. 
It seems it's harware blocked but i can use wifi on windows so it's quite troublesome since I need it.

```
moi@moi-X550VC:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
moi@moi-X550VC:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5188 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
moi@moi-X550VC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I already check some topic on the forum and tried it, but it didn't work.

---

### Post by chili555 on 2014-12-14
> Hard blocked: yesLet's try a driver parameter:```
sudo -i
echo "options asus-nb-wmi wapf=1"  >  /etc/modprobe.d/asus-nb-wmi.conf
exit
```Reboot and then run:```
rfkill list all
```Are you still hard blocked? If not, the wireless should be working.> 148f:5370 Ralink Technology, Corp. RT5370 Wireless AdapterBefore you reboot, remove the USB wireless as we probably don't need it.

---

### Post by moi3 on 2014-12-14
```
moi@moi-X550VC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Thanks you very much !

---

### Post by chili555 on 2014-12-14
> **moi3 said:**
> ```
moi@moi-X550VC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Thanks you very much !Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by moi3 on 2014-12-14
I'd like but i'm not the one who opened this thread.

---

