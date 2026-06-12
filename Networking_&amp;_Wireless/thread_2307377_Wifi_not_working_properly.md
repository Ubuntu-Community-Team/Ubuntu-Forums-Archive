---
title: "Wifi not working properly"
date: 2015-12-24
forum: Networking &amp; Wireless
---

### Post by naveen_chakravarth on 2015-12-24
I use Ubuntu 14.04 on my Lenovo laptop. When I login into Ubuntu, the wifi works fine initially and suddenly it stops working after some time. Can anyone please help?

---

### Post by Hadaka on 2015-12-24
Hi, please open a terminal ctrl/alt/t then copy and paste one line at a time.
```
lspci -nnk | grep 0280 -A2
rfkill list all
uname -a
```
post the output.
thanks

---

### Post by naveen_chakravarth on 2015-12-24
Yes, the following is what I obtained:

[FONT=arial]
$ lspci -nnk | grep 0280 -A2[/FONT][FONT=arial]
[/FONT]
[FONT=arial]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723][/FONT]
[FONT=arial]    Subsystem: Lenovo Device [17aa:b736][/FONT]
[FONT=arial]    Kernel driver in use: rtl8723be


$ rfkill list all

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


$ uname -a

Linux Space 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux





[/FONT]

---

### Post by naveen_chakravarth on 2015-12-26
@Hadaka I've provided the details, could you please help me?

---

### Post by praseodym on 2015-12-26
Please run

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=[COLOR="#FF0000"]DE[/COLOR]/g" /etc/default/crda  
```
Change the country code with yours and reboot

---

### Post by naveen_chakravarth on 2015-12-27
I did what you have said... I have to wait and see if it solves the problem. 
Thank You.

---

