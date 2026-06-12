---
title: "how to add a VPN connection in Ubuntu 18.04 Lightdm Lxde"
date: 2020-10-27
forum: Networking &amp; Wireless
---

### Post by thosecars822 on 2020-10-27
Hello

Whenever I go to the networks icon on the task bar of Lubuntu 18.04 Lightdm Lxde, VPN connection, the option "add a VPN connection" does not get enabled and therefore I do not know how I can add a VPN connection.

Does anyone know how this can be done?

Thanks in advance

---

### Post by yapidumoac on 2020-10-27
[COLOR=#333333][FONT=Consolas]sudo apt install network-manager-openvpn network-manager-openvpn-gnome[/FONT][/COLOR]

---

### Post by thosecars822 on 2020-10-27
Thanks but that did not work for me in Lubuntu 18.04 Lightdm Lxde. I restarted the computer but it did not work after that either.

---

### Post by thosecars822 on 2020-10-28
[COLOR=#000000][FONT=Arial]The following command made it work:
sudo systemctl restart network-manager[/FONT][/COLOR]

---

