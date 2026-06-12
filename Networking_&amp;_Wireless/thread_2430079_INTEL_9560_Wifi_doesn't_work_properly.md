---
title: "INTEL 9560 Wifi doesn't work properly"
date: 2019-10-27
forum: Networking &amp; Wireless
---

### Post by canahmetdursun on 2019-10-27
Hey guys, I can connect to my wifi but there is no internet connection plus Kubuntu gives me error:
iwlwifi: bios contains wgds but no wrds
Help me out I tried bunch of things...

---

### Post by jeremy31 on 2019-10-27
See the wireless script link in my signature and post results, welcome to the forums

---

### Post by canahmetdursun on 2019-10-29
[https://pastebin.com/ffxhwtaH](https://pastebin.com/ffxhwtaH) thanks btw

---

### Post by praseodym on 2019-10-29
```
wlp0s20f3  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```
The card is turned off. Any button, switch, key or key combo?

---

### Post by jeremy31 on 2019-10-29
I would do ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
sudo iwconfig wlp0s20f3 txpower 20
```

Then see if you can connect

---

### Post by canahmetdursun on 2019-10-30
I use usb tethering maybe that's why dBm is zero.

---

### Post by canahmetdursun on 2019-10-30
Whaaaaaaaaa.... It worked THANKS MAN. You are my new hero :D
But error message is still exists on start.

---

### Post by chili555 on 2019-10-30
> But error message is still exists on start.It doesn't say it's an error or even a warning. I suggest that you ignore it.

---

