---
title: "No wi-fi network after install"
date: 2016-10-20
forum: Networking &amp; Wireless
---

### Post by ozozuz on 2016-10-20
[COLOR=#111111][FONT=Ubuntu]i just installed ubuntu 16:10 on my Xiaomi Air 13 "uncommon device i know" but i'm not able to see any wifi connection. This problem occurred right after the install, since before "during the try ubuntu and all the installation" i was able to see and connect w/out any problem.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If i go to All Settings -> Network i'm not able to turn on the wifi "it switch back to off as soon as i turn it on".[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Nothing also in Software and update -> more driver.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What should i do ? :C[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-10-20
Please post results for ```
lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by ozozuz on 2016-10-20
I was able to fix it by this metod here 
[http://askubuntu.com/questions/829863/wi-fi-drivers-for-laptop-xiaomi-air-13](http://askubuntu.com/questions/829863/wi-fi-drivers-for-laptop-xiaomi-air-13)

But now i can't find any programm/app on Ubuntu Software C. "like geany".
Is this problem somehow related to the fix that i just found ?

---

### Post by jeremy31 on 2016-10-20
For that issue, in terminal do ```
sudo apt-get update
``` and then see if you can find things in Software Center

---

### Post by fredericklowe63 on 2017-03-25
> **ozozuz said:**
> [COLOR=#111111][FONT=Ubuntu]i just installed ubuntu 16:10 on my Xiaomi Air 13 "uncommon device i know" but i'm not able to see any wifi connection. This problem occurred right after the install, since before "during the try ubuntu and all the installation" i was able to see and connect w/out any problem.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If i go to All Settings -> Network i'm not able to turn on the wifi "it switch back to off as soon as i turn it on".[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Nothing also in Software and update -> more driver.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What should i do ? :C[/FONT][/COLOR]

I had problems getting my wifi to work after installing ubuntu server 16.04 lts. There is no desktop only a command line. Anyway, I looked everywhere to get my wifi up I did a lot of reading on how to and nothing would turn on my wifi adapter. It read in iwconfig it was down. What really got me confused was while installing I was able to hook into my wifi and with success. When install was done I booted up. I was yes here we go. First I will update. WRONG!!!  Wifi was down. I said to myself wow. It was connected in install. So just for kicks I rebooted but this time when grub came up I went to the ubuntu advance option loaded the first line there booted up signed in and bang!! Had internet. So I did updates and upgrade. Rebooted and took the first grub ubuntu with the * by it. ( where I booted after install) still worked fine and is still going. What makes me rub my head in confusion, is the fact that it connected in install but not after install. Why it did not copy my connection to what ever conf file to keep it working. Well don't know if this helps desktop. Good luck.

---

