---
title: "netowork vanished ubuntu clone."
date: 2024-05-28
forum: Networking &amp; Wireless
---

### Post by ulao3 on 2024-05-28
Hey all, I have a few linux desktops I play with and a ubuntu server. One of my desktops is a Zorin system, ( its a ubuntu clone). I think based on 22. I tried getting help from their forum but they seem clueless and the issue maybe more generic so wanted to ask here. 

History, all was ok bug after letting the system sit for a month and come to booting it back up the network is gone. I have no way to post anything from that OS in here so I can not just copy logs. But this is what I know and have done. 

if config  -a shows just the loop back.
There is no  /etc/network/interfaces so I assume netplan.
etc/netplan is  empty folder.
The GUI shows no nics

My Nic is built on the MB ( realtech)
So I put in a USB nic. And I still have nothing to configure. 

lspci shows both networks on the system.
dmesg shows the USB was attached with no errors. 

I'm new to netplan but from what I understand the empty folder is normal. 
  [https://unix.stackexchange.com/questions/638782/after-ubuntu-18-04-upgrade-where-is-my-network-config-at](https://unix.stackexchange.com/questions/638782/after-ubuntu-18-04-upgrade-where-is-my-network-config-at)
>  
This means the /etc/netplan dir is empty, you have to go to the desktop  and search for "Advanced Network Configuration" and in that GUI you will  modify your config.

ok so fine, but Zorin, has no such a thing. Is my issue specific to Zorin?

---

### Post by currentshaft on 2024-05-28
hi

---

### Post by ulao3 on 2024-05-28
so I guess just 

auto eth0
iface eth0 inet dhcp

and reboot?


AS for the name, I see PCI-2 network unclaimed. If there  is no drive how can I assign one, lsmod shows no sign of it,  clearly it was working.

name
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

I tried to download this file
[URL="https://github.com/mtorromeo/r8168"]https://github.com/mtorromeo/r8168

[/URL]but when I do the autorun I get check old driver and unload it. I assume its on here some where then?

---

### Post by ulao3 on 2024-05-28
this is a mess and I'm not sure I can follow along with no network but this looks like my issue
[URL="https://askubuntu.com/questions/1287967/cant-get-rtl8125-realtek-driver-working-on-version-20-04"]https://askubuntu.com/questions/1287967/cant-get-rtl8125-realtek-driver-working-on-version-20-04


[/URL]I tried installing a few other network cards but they all give me error when making
saying missing files in
/*lib*/*modules*/5-15-09-*generic*/build

Is there a way to put the headers back? I could install offline but too many headers out there to pick from.

---

### Post by ulao3 on 2024-05-29
the solution was so stupid simple. All I had to do was hold shift on boot and elect my old kernel. Everything works fine.

---

