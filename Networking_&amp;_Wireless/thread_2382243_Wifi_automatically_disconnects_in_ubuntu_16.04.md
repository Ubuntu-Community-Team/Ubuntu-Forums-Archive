---
title: "Wifi automatically disconnects in ubuntu 16.04"
date: 2018-01-10
forum: Networking &amp; Wireless
---

### Post by tofazzal.haque on 2018-01-10
Hi, I am using Ubuntu 16.4 on PH Pavilion laptop. After sometime using my laptop, wifi is disconnected  and showing "Password requird". When I enter my wifi password it's worked. But it disturb again and again.
My [COLOR=#000000]wireless info Pastebin link is[/COLOR] [https://paste.ubuntu.com/26361532/](https://paste.ubuntu.com/26361532/)
Please Help me.

---

### Post by Hadaka on 2018-01-10
Hi please open a terminal..ctrl/alt/t..then Copy and Paste..
```
sudo apt-get update
```
```
sudo iw reg set BD
sudo sed -i 's/=.*/=BD/' /etc/default/crda
```
Then do..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/BLUE_WHALE
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
systemctl restart network-manager.service
```
boot and test wireless
Thanks.

---

### Post by tofazzal.haque on 2018-01-12
Now It's working better.But after long time it get disconnected forever. When I restart my computer it's connected again. I also observed that sometime the connection get slow.
[COLOR=#000000]My [/COLOR][COLOR=#000000][COLOR=#000000]wireless info Pastebin link is  [/COLOR][/COLOR]https://paste.ubuntu.com/26372628/
Thank you.

---

### Post by Hadaka on 2018-01-12
Hi, this indicates a conflict with windows..
```
 # wl: module verification failed: signature and/or required key missing - tainting kernel
```
Please go into bios and disable secure boot (UEFI)

Please also correct your typeO -typing error- by COPY and Paste of this command.
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/BLUE_WHALE
systemctl restart network-manager.service
```
Thanks.

---

