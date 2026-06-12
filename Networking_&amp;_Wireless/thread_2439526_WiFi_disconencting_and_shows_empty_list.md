---
title: "WiFi disconencting and shows empty list"
date: 2020-03-29
forum: Networking &amp; Wireless
---

### Post by Crazy01 on 2020-03-29
Hi,
I a using Ubuntu 19.10 on my HP laptop which have wifi rtl8723be. Problem is whenever i start my laptop my wifi conenctec  but after 5-10 minutes it's disconnected and always trying to connect but always  failed. When open Wifi all listed wifi disappeared and none of any wifi shows in the list. 
I downlowd and install github.com/lwfingure/rtlwifi_new and install it. And created /etc/modprobe.d/rt8327be.conf with following content
SUSPEND_MODULE="rtl8723be"
options rtl8723be fwlps=N ips=N
But didn't work. 

I am new and want to use Ubantu.

---

### Post by jeremy31 on 2020-03-29
See the wireless script link in my signature and post results

---

### Post by Crazy01 on 2020-03-29
I followed your steps and created this:
[COLOR=#333333][FONT=Consolas]
[/FONT][/COLOR][https://pastebin.com/8tJd5BjB](https://pastebin.com/8tJd5BjB)
[COLOR=#333333][FONT=Consolas]
This is very frustrating. Please help.[/FONT][/COLOR]

---

### Post by Crazy01 on 2020-03-29
and another problem is, even my  internet is not working even i use physical connection through Ethernet.

---

### Post by praseodym on 2020-03-29
Just load that LAN driver via
```

sudo modprobe -v r8169
sudo depmod -a
sudo update-initramfs-u -k all
```
Please show 
```
lsmod
```

completely

---

### Post by Crazy01 on 2020-03-29
I don't  have update-initramfs-u in my system.

---

### Post by jeremy31 on 2020-03-30
For the wifi do ```
echo "options rtl8723be fwlps=N ips=N ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by Crazy01 on 2020-04-16
> **jeremy31 said:**
> For the wifi do ```
echo "options rtl8723be fwlps=N ips=N ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

Nope. Still facing same issue. Along with this, after screen lock it's don't connect to any WiFi.

---

