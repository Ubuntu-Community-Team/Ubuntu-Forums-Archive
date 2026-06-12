---
title: "Atheros QCA9377 (rev 31) doesn't detect certain WiFi networks on Ubuntu 19.10"
date: 2019-12-14
forum: Networking &amp; Wireless
---

### Post by skooner on 2019-12-14
Running Ubuntu 19.10 on an Acer A315-41-R45R and sometimes particular  WiFi networks don't show up at all. The hotspot I create on one of my Android  phone doesn't show up as a network sometimes and sometimes it does. Is  there any fix for this?


  So, it seems that if I change the name of the Android hotspot it shows up and I can connect to it. Any reason for this?


  Also attaching the result of the wireless-info script: [https://pastebin.com/kAHV536Q](https://pastebin.com/kAHV536Q)

---

### Post by praseodym on 2019-12-15
Which country do you live?

---

### Post by skooner on 2019-12-16
India. Why?

---

### Post by praseodym on 2019-12-16
Setting the country code

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=IN/g" /etc/default/crda 
```
Reboot and check
```

iwlist chan
```

---

### Post by skooner on 2019-12-17
Did that. These are the results of ```
iwlist chan
```

```
enp1s0f1  no frequency information.

lo        no frequency information.

wlp2s0    26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Channel 169 : 5.845 GHz
          Current Frequency:5.745 GHz (Channel 149)
```

---

### Post by praseodym on 2019-12-17
Obviously, a problem with the EPROM, only 12 channels visible in the 2,4 GHz region. Do the other network broadcast on channel 11 or other not shown in your output?

---

### Post by Mujaheiden on 2019-12-28
Same here, I'm in the Netherlands, with 32 channels available but not channel 13, where the desired network is broadcasting. In Windows its working fine.

---

### Post by wildmanne39 on 2019-12-28
Hello Mujaheiden, if you need support for an issue please start your own thread instead of posting in someone else's so you and the OP of this thread can both get the individual help you need,

Thanks

---

### Post by praseodym on 2019-12-29
Please try

```
echo 'options cfg80211 ieee80211_regdom="[COLOR="#FF0000"]IN[/COLOR]"'| sudo tee /etc/modprobe.d/cfg80211_options.conf
```
and reboot.

@Mujaheiden. Try it with "NL" or "EU" instead of "IN"

---

### Post by Mujaheiden on 2019-12-29
No avail, but thanks. Missing chanel 13 seems to me to point [here]("https://askubuntu.com/questions/894283/qualcomm-atheros-device-cant-find-channel-13-wifi-ubuntu-16-04-2/895331#895331").

---

### Post by jeremy31 on 2019-12-31
Ok, I finally had time to attempt a fix for 19.10 with 5.3 kernel.  Secure Boot needs to be disabled so check
```
mokutil --sb-state
```

If it is not installed or says Secure Boot disabled then
```
sudo apt install git dkms
git clone https://github.com/jeremyb31/ath-5.3.git
sudo dkms add ath-5.3
sudo dkms install ath-5.3/1
```
Reboot

If it fails and you have no wifi, reverse with
```
sudo dkms remove ath-5.3/1 --all
```

---

