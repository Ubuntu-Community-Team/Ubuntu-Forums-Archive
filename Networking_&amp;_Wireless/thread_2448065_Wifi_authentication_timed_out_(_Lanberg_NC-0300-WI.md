---
title: "Wifi authentication timed out ( Lanberg NC-0300-WI Chipset  Realtek RTL8192EU)"
date: 2020-07-31
forum: Networking &amp; Wireless
---

### Post by Andreyshel on 2020-07-31
I have a problem to connect to the wifi network. Network connection fails, after password is typed in. My network card is Lanberg NC-0300-WI(Chipset Realtek RTL8192EU)
The router is Google Nest wifi. Other devices can successfully connect to the router.
Dmesg shows authentication timed out message . 
Attached Wireless-info has all the information really. I do not have much to add.(Thanks to the script developers).
Thanks for your suggestions on where I should start.

---

### Post by praseodym on 2020-08-01
Which network do you want to connect to? Obviously, you are located in Sweden? Try

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=SE/g" /etc/default/crda 
```
Reboot and check if its working. Otherwise also try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by Andreyshel on 2020-08-01
> [COLOR=#000000]Which network do you want to connect to?[/COLOR]


AHOME

> Recommendations
Done. No effect.
Also I have tried driver from [this ]("https://github.com/clnhub/rtl8192eu-linux") github page. Same thing (I reverted back to the default driver)

---

### Post by praseodym on 2020-08-01
Try changing to channel 6 in your router. MAC-address filter is turned off there?

---

### Post by Andreyshel on 2020-08-01
> [COLOR=#000000]Try changing to channel 6 in your router.[/COLOR]
According to the product forums it is impossible to set  channel manually. 

> [COLOR=#000000]MAC-address filter is turned off there?[/COLOR]
There is no mac filter feature.

---

### Post by Andreyshel on 2020-08-01
I have used Android  hotspot to check if it will work with another router. Nope. Even when I setup   an open network without a password, connection keeps falling.
I gave  the network card to a friend of mine, to check if it will work on Windows computer. If not then it is broken and needs to be returned to the seller.

---

### Post by Andreyshel on 2020-08-08
The network card does work on Windows. So hardware is not broken.

---

