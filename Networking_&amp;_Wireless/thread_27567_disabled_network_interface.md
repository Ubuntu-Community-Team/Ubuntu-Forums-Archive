---
title: "disabled network interface"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by brutus on 2005-04-16
Ia have problem with network interface. It is disabled and i can't change it in Kde. How to enable this interface in terminal or editing files?

---

### Post by domesticatewhat on 2005-04-16
I don't know about kde but it gnome you can go to system --> Administration -->Networking 

although I am sure there is an easier way than installing ubuntu-desktop.

---

### Post by wfx on 2005-04-16
hmmm,
very many information...
Is it also down if you reboot?
Do "ifup DEVICE" 
DEVICE is: 
eth0  (first network card)
eth1  (second ...)
ppp0 (first modem)

---

### Post by brutus on 2005-04-17
When system starts, "configure newtork interfaces" takes some time. I don't have Gnome yet. It is fresh instalation of Kubuntu. I tried "ifup Device"   - "interface eth0 already configured"
In KDE network settings, everything is gray but a see information interface eth0 disabled. When I want to change it, I press "administrator mode" then password and nothing is changed. 
It doesn't matter is it after reboot. Network interface is disabled. I had problems wiith dns settings and resolv.conf but I found solution to uncomment function in dhcp3 script and it worked. But after few reboots network is disabled.
i'll give more info but I don't know what is important.


PS. I Don't speak english so I'm sorry for my mistakes.

---

### Post by wfx on 2005-04-18
ok, maybe the module(driver) for you card is not loading.
Open a terminal and do:
lspci | grep Ethernet

It should output some similary line:
0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

If you have the same chip then look if the modules up:
lsmod | grep 8139

You say you have change something in dhcp3 (please full path)  script.
What have you changed?

How do you get youre IP (via dhcp server)?

---

### Post by kooldino on 2007-11-20
Bump - having a similar issue.

---

