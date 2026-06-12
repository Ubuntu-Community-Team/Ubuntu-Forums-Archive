---
title: "Ubuntu 14.04 Wifi is timing out frequently [continued..]"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by essxiv on 2015-04-30
[http://ubuntuforums.org/showthread.php?t=2268066](http://ubuntuforums.org/showthread.php?t=2268066)


In my previous post, a couple weeks ago, I thought I had a decent way around my WiFi timing out every 30 minutes or so..

I think because i've been updating these updates for Ubuntu, something changed in my system because these timing outs have been A LOT more frequent, and sometimes the fixes that once worked, do NOT work anymore..

*sigh*, could someone try and diagnose this for me please.. It's really effecting my work (12 hours on the computer daily).

Thanks much

---

### Post by jeremy31 on 2015-04-30
Lets try a slightly different fix that may work
```
[COLOR=#545454][FONT=arial]echo "[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**options rtl8723be**[/FONT][/COLOR][COLOR=#545454][FONT=arial] fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.[/FONT][/COLOR][COLOR=#545454][FONT=arial]conf [/FONT][/COLOR]
```

Reboot

---

### Post by essxiv on 2015-05-04
> **jeremy31 said:**
> Lets try a slightly different fix that may work
```
[COLOR=#545454][FONT=arial]echo "[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**options rtl8723be**[/FONT][/COLOR][COLOR=#545454][FONT=arial] fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.[/FONT][/COLOR][COLOR=#545454][FONT=arial]conf [/FONT][/COLOR]
```

Reboot

Hey Jeremy31,

It seems to have worked for the most part! I have had none-to-1 time-outs in the past 3 days!!!!!

Can you tell me exactly what this echo block of code does exactly?
Thank You!
^_^
Cheers!

---

### Post by jeremy31 on 2015-05-04
It turns off some power management on the wifi card, with all the issues being fixed with this it should be the default values

---

