---
title: "Help getting a wireless Belkin F5D7050 working?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by PillowFightin on 2007-10-21
I just did a clean install of Gutsy on my old Sony Vaio PCG-540 and am having trouble getting the wireless working. (Before I go any further I should state that I am a TOTAL newbie to Ubuntu and Linux in general). I can use the wired okay, but can't get the Belkin USB wireless adapter working...a F5D7050, version 3. I specifically chose it because I had read somewhere that it works out of the box and I wouldn't have to use ndiswrapper (which I have no clue whatsoever how to implement). Router is a Linksys WRT54G using WEP.

I have tried to investigate...some threads suggested fooling around in Network Manager, but this option is not even present under System, only Network Proxy. Maybe it exists using the Terminal but I don't know how to get to it.

Help?

---

### Post by PillowFightin on 2007-10-22
Ok, hopefully I am getting somewhere...I have followed the directions found [here]("http://ubuntuforums.org/showthread.php?t=404763&page=2") (by ffxr), but I am stuck at the step

```
gedit rt73sta.dat
```

There is an SSID entry in that file but no ESSID entry (same thing?) and it won't let me save changes.

 I am so close...help, please?

(P.S. For the life of me I do not see a Network Manager anywhere...does anyone know how to get to this? It's not under System.)

---

### Post by PillowFightin on 2007-10-23
*bump*    Anyone...?

---

### Post by farmer26 on 2007-12-01
You need to use sudo in order to change that file, so do ```
sudo gedit rt73sta.dat
``` and then enter your password. After you have made your changes you should be able to save it fine.

---

