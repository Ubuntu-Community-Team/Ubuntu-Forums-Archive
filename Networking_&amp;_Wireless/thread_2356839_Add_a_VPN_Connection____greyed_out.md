---
title: "Add a VPN Connection    greyed out"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by jg-jguk on 2017-03-27
Hello!


Unfortunately my "Add a VPN Connection  " is greyed out. Anyone using 16.04 and see the same?


Been using Ubuntu for a long time. Trying to get a VPN setup, I've installed all the openVPN paages, and PPTP


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial




I was going to try out [https://hide.me/en/vpnsetup/ubuntu/pptp/](https://hide.me/en/vpnsetup/ubuntu/pptp/)


My laptop was installed recently, I don't have any changes to networking etc, it's all default. ie I've not created a bridge, or running vmware etc
Thank you for any ideas

---

### Post by #&amp;thj^% on 2017-03-27
Do you have this installed yet?

```
network-manager-openvpn-gnome
```

> network-manager-openvpn-gnome: network management framework (OpenVPN plugin GNOME GUI)

---

### Post by jg-jguk on 2017-03-29
Hello
Thank you for your reply
Yes I have  network-manager-openvpn-gnome installed

I found that the only way to add it is acutaly via "Edit Connections..." then click [Add]

However, hide.me service didn't really solve the issue I still can't access Afternic.com via various different locations of the VPN. I wonder why that is?

I also found a guide for tinyproxy, installed this on my AWS server. Even via that I could not get the HTTPS site of afternic.com load (after login).

This seems to be all very difficult :(

---

