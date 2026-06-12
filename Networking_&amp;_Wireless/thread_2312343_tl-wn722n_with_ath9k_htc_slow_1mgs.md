---
title: "tl-wn722n with ath9k_htc slow 1mg/s"
date: 2016-02-03
forum: Networking &amp; Wireless
---

### Post by quetzalcoatl2 on 2016-02-03
[FONT=arial black][/FONT][COLOR=#222222][FONT=Verdana][/FONT][/COLOR][COLOR=#222222][FONT=Verdana][/FONT][/COLOR][SIZE=5][/SIZE][SIZE=4][COLOR=#222222][FONT=Verdana]Hi everyone, please i need your help[/FONT][/COLOR][/SIZE][SIZE=4]I have a problem with my tl-wn722n with ath9k_htc driver in lubuntu 15.10 64 bits. I have the last kernel. 
my network board device realtek connects perfectly but it doesnt have the signal of my tl-wn722n in w7. 
the atheros it's connected but with very slow speed, only 1mb/s, too many less than the 54mg/s of my realtek.
 I tried the tipically solution of options ath9k_htc nohwcrypt=1 but nothing resolve the issue. 
I need to change the firmware? i dont know, all other user seems to resolve the problem with "options ath9k_htc nohwcrypt=1"
 but it's not my situation. [/SIZE]

---

### Post by jeremy31 on 2016-02-03
Open a terminal window and enter ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]chmod +x wireless-info && ./wireless-info
```

Post the contents of the wireless-info.**txt** file using code tags[/FONT][/COLOR]

---

### Post by quetzalcoatl2 on 2016-02-03
Hi!!! ok. it's done! thanks for the quick answer!

---

### Post by jeremy31 on 2016-02-04
Can you change encryption settings on the wireless router to WPA2 only, it shows you are currently using WEP and Ubuntu doesn't work the greatest with WEP or TKIP enabled

And if you are in Argentina then ```
sudo iw reg set AR
```
```
gksudo gedit /etc/default/crda
```

Go to the last line and make it be ```
REGDOMAIN=AR
```
Save, exit, reboot

---

### Post by quetzalcoatl2 on 2016-02-04
I can't change the encryption because i share the internet connection with my neighbor and it's not seems being the problem. my realtek has a 54 mb/s speed and it's connected at the same network. I'm sending this answer because i'm connected with the realtek... the problem is that the signal sometimes got downtimes and it's for that that i want my tl-wn722n be working at full speed, not 1 mb/s, like the network manager says and obviously seems slow on web surfing when i disconnect the realtek. sorry for my english

---

### Post by Vladlenin5000 on 2016-02-05
Please tell your neighbor to change it to what is currently the consensus regarding wireless security as commented above, WPA2-AES, for his/her peace of mind as well, and irrespective of how many other devices/OSs seem to be fine with such settings.
Tell him/her that, in terms of potential abuse, the difference between a completely open WiFi network and one using WEP is **2 minutes or less**.

---

