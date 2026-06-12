---
title: "Netgear A7000 Wirless Adapter Trouble"
date: 2018-05-24
forum: Networking &amp; Wireless
---

### Post by joshualsd on 2018-05-24
I recently decided to try out linux out of curiosity, and downloaded the latest version of Ubuntu. I have a netgear a7000 wireless adapter, but it does not connect to the INTERNET when I am using linux, and no amount of searching else where has helped me so far. I have downloaded supposed drivers that will apparently work for my product from the wikidev page, but I can't seem to find out how to make it all work. Apologies for being a huge noob.


[COLOR=#333333][FONT=Verdana][[CENTER][COLOR=#777777][FONT=FontAwesome][/FONT][/COLOR][/CENTER]]("https://forums.linuxmint.com/viewtopic.php?f=53&t=269964&sid=dc6e00ed5d248a6a96074e6307bb2806#top")[/FONT][/COLOR]

---

### Post by kerry_s on 2018-05-24
run these commands in terminal:
```

sudo apt-get update
sudo apt-get install git dkms
git clone https://github.com/zebulon2/rtl8814au.git
sudo dkms add ./rtl8814au 
sudo dkms build -m rtl8814au -v 4.3.21
sudo dkms install -m rtl8814au -v 4.3.21

```

then reboot

---

### Post by joshualsd on 2018-05-24
I do not have any access to internet connection without my adapter, so this won't work for me, any other solutions?

---

### Post by kerry_s on 2018-05-24
don't know then the drivers are online.

---

### Post by wildmanne39 on 2018-05-24
If you have a cell phone that is hotspot capable you can plug it into your usb port and turn on the tethering button on the phone and it will establish a connection just like you are plugged into an ethernet connection.

---

### Post by joshualsd on 2018-05-25
I'm not sure why I didn't think of this earlier... Thanks a lot man, and thank [**[COLOR=#000000]kerry_s[/COLOR]**]("https://ubuntuforums.org/member.php?u=132335") for the commands!

---

