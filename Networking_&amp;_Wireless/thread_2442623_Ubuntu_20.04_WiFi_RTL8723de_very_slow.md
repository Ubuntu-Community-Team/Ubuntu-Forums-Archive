---
title: "Ubuntu 20.04 WiFi RTL8723de very slow"
date: 2020-05-05
forum: Networking &amp; Wireless
---

### Post by gary.allan.garibaldi on 2020-05-05
I know with Ubuntu 18.04 I was able to select an antenna to use that would speed up my WiFi connection. Is there any way that can be done with the 20.04 system?ThanksGary

---

### Post by CelticWarrior on 2020-05-05
Doesn't the same command work?

---

### Post by gary.allan.garibaldi on 2020-05-05
[SIZE=3][FONT=arial]Tried this with a reboot each time with no change.
[/FONT][/SIZE][FONT=arial][/FONT][SIZE=3][FONT=arial][COLOR=#333333][/COLOR][COLOR=#333333]echo "options rtl8723de ant_sel=**3**" | sudo tee /etc/modprobe.d/rtl8723de.conf[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=arial]Also try 1, 2, 3, or 4 to see which works best.[/FONT][/COLOR]

---

### Post by jeremy31 on 2020-05-05
Please see the wireless script link in my signature and post results.  From what I have seen the extended branch of lwfinger's rtlwifi-new github site doesn't compile in 20.04 and the kernel driver used is rtwpci and that doesn't have an antenna select parameter

---

### Post by gary.allan.garibaldi on 2020-05-05
See attached file.

---

### Post by jeremy31 on 2020-05-05
See if it is better after disabling wifi power management with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by gary.allan.garibaldi on 2020-05-05
Thank you Jeremy. That seems to have fix things. I've marked this as solved.

---

