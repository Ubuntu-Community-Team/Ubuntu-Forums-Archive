---
title: "I Am A Newbie, Please Help"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Master_Z on 2007-06-15
My wireless card is the Realtek 8185. I am currently on the wired LAN on this laptop, since the wireless isnt detected by Feisty Fawn. Is there some way to fix this?

Also, my sound isnt working. It is of the SIGMATEL HIGH DEFINITION AUDIO CODEC. The exact model is STAC 9200. I went into alsamixer, but none of them are muted. On music files, it will show the file streaming, but the sound wont play. How can I fix this?

---

### Post by xthaparian on 2007-06-15
Try this site for Wireless issues

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Also try this Post for Sound issues..

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

enjoy

---

### Post by jfinkels on 2007-06-15
> **Master_Z said:**
> My wireless card is the Realtek 8185. I am currently on the wired LAN on this laptop, since the wireless isnt detected by Feisty Fawn. Is there some way to fix this?


Do one question per thread, please :D

Take a look here for the drivers for RTL818X series wireless cards. I have had success with them in the past. [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

Come back and let us know if you need help compiling them. As a start, do the following:

Type the following in the terminal to install essential programs for compiling:```
sudo aptitude install build-essential
```

Then, download the drivers from the website I gave you and follow the directions there for compiling and installing.

---

