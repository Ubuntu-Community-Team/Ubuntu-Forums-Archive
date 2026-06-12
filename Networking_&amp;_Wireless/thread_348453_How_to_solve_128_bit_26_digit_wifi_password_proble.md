---
title: "How to solve 128 bit 26 digit wifi password problem"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by abygomez on 2007-01-28
hi,

i am new to ubuntu. i was able to configure my wifi card (belkin) using this procedure.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

It works well in a 64 bit wifi atmosphere because the password length is small. but when it comes to a 128 bit wifi atmosphere i could not type in all the 26 charecters in to the password box. is there any way to enter all the 26 hexadecimal charecters in to the password box.

---

### Post by chili555 on 2007-01-28
Actually, I think you can just keep typing because it only looks like it won't fit.

You could also sudo gedit /etc/network/interfaces to make it look similar to this:

auto wlan0  <--or whatever your wireless interface is.
iface wlan0 inet dhcp
wireless-essid GBR1
wireless-key 096c7fxxxxxxxxxxxxxxxxxx4e4afe

Save, quit and sudo ifup wlan0.

Good luck.

---

