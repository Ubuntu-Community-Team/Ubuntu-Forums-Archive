---
title: "[Wifi problem] Can scan networks but fail to connect"
date: 2020-01-28
forum: Networking &amp; Wireless
---

### Post by lucas-42 on 2020-01-28
I am having a problem with wifi. I can scan the networks around me but I usually can not connect to them, I have already connect successfully to my home wifi but usually I can not, it seams a little random. However I have no problem connecting to the hotspot I create with my smartphone. 

I use an Asus K56 and this is my network device:
```
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
```

Here is the logs my wifi card produces:

```

[  818.637873] wlp3s0: send auth to 0c:98:38:17:9f:5b (try 1/3)
[  818.641257] wlp3s0: authenticated
[  818.647546] wlp3s0: associate with 0c:98:38:17:9f:5b (try 1/3)
[  818.661172] wlp3s0: RX AssocResp from 0c:98:38:17:9f:5b (capab=0x431 status=0 aid=3)
[  818.661323] wlp3s0: associated
[  967.552655] wlp3s0: deauthenticating from 0c:98:38:17:9f:5b by local choice (Reason: 3=DEAUTH_LEAVING)
```

Is there a known solution for this problem or a way to debug it?

---

### Post by jeremy31 on 2020-01-28
Please see the wireless script link in my signature and pist results

---

### Post by lucas-42 on 2020-01-28
> **jeremy31 said:**
> Please see the wireless script link in my signature and pist results

Thanks for your answer, as I said this problem seems a little bit random, today I could connect the wireless, but it can probably fail in future. I did the steps that are told in wireless scripts and I already ran it to see the wireless-info.txt, I will posted here if the problem persists.

---

### Post by jeremy31 on 2020-01-28
I would bet it is because of channel restrictions because of the EEPROM on the wifi card and if your router is on auto channel it can change to a legal channel that isn't allowed on the AR9485

---

### Post by lucas-42 on 2020-01-28
Well I will check that, but for now the wifi is working. In the case that this is the problem what should I change? Wifi card or router settings?

---

### Post by jeremy31 on 2020-01-28
I could give more options if you post script results, but setting to channel between 1-11 should be fine

---

### Post by lucas-42 on 2020-01-29
Here it is the wireless-info.txt: [https://pastebin.com/Ep8ZgT6U](https://pastebin.com/Ep8ZgT6U)

---

### Post by jeremy31 on 2020-01-29
Lets set the country code ```
sudo iw reg set ES
```
If you can change the wifi router settings, change encryption to WPA2 only with no WEP or TKIP as those old encryption methods cause some issues and change the channel to channel 1
And run these 2 commands to keep Network Manager from trying to enable wifi power management
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by lucas-42 on 2020-01-29
> **jeremy31 said:**
> Lets set the country code ```
sudo iw reg set ES
```
If you can change the wifi router settings, change encryption to WPA2 only with no WEP or TKIP as those old encryption methods cause some issues and change the channel to channel 1
And run these 2 commands to keep Network Manager from trying to enable wifi power management
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

Already did that, but I am from portugal should I put "PT" for the code country,  "ES" or it does not really matter?

---

### Post by jeremy31 on 2020-01-29
Use PT, not sure what differences there might be

---

### Post by CelticWarrior on 2020-01-30
> **jeremy31 said:**
> Use PT, not sure what differences there might be

No differences except national pride ;)
I wouldn't mind having PT as well.

---

