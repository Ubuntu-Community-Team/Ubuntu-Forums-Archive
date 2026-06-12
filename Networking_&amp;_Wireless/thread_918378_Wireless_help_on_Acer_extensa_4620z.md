---
title: "Wireless help on Acer extensa 4620z"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by GibsonSGKing on 2008-09-12
Ok, heres the problem. i just installed ubuntu, and it will not let me use my wireless card. a quick google search came up with this [http://ubuntuforums.org/showthread.php?t=715187](http://ubuntuforums.org/showthread.php?t=715187) . BUT, at this part, unzip xp32-6.0.3.85.zip
sudo ndiswrapper -i net5416.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo loadndisdriver
sudo modprobe ndiswrapper

i get stuckat the sudo ndiswrapper -i net5416 command. it says that the command is unrecognized. im very new to ubuntu, so plz keep this in mind when posting. im sorta stumped so anyhelp is appreciated. and if you can recomend some good anti virus software, that would be great also. thx!!

---

### Post by IndyGunFreak on 2008-09-12
You have an atheros wireless chipset, you would probably be better off looking into madwifi...

[http://madwifi.org/](http://madwifi.org/)

IGF

---

### Post by GibsonSGKing on 2008-09-13
ok, can you help me install it??? because i have absolutely no clue..........:confused::confused::confused::confused:

---

