---
title: "Weak wifi connection in ubuntu 18.10 with rtl8723be"
date: 2019-02-24
forum: Networking &amp; Wireless
---

### Post by amankh99 on 2019-02-24
[COLOR=#000000]Hi, I was having problem with wifi in ubuntu 18.04 lts after having recent upgrade, so I followed the steps mentioned here - [/COLOR][https://askubuntu.com/questions/1058...with-rtl8723be]("https://askubuntu.com/questions/1058379/wifi-signal-is-weak-in-ubuntu-18-04-with-rtl8723be")[COLOR=#000000], but was not able to solve the problem, in another answer I read that upgrading to 18.10 (kernel version 4.18.0-15-generic) will solve the problem but all in vain. Please help to resolve the problem.[/COLOR]

---

### Post by chili555 on 2019-02-24
Perhaps the well-known bug has re-emerged in 4.18.0-15. Is there any improvement if you select -14 at the GRUB menu and boot into -14 instead?

---

### Post by amankh99 on 2019-02-24
[COLOR=#242729][FONT=Arial]There is no entry in grub for boot through 4.18.0-14 kernel, also ant_sel = 0 doesn't work also I don't know why but the ant_sel = 2 and 1 setting, now not giving any results for command "iwlist scan | egrep -i 'ssid|quality'".[/FONT][/COLOR]

---

### Post by jeremy31 on 2019-02-24
See the wireless script link in my signature and post results

---

