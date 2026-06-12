---
title: "Fios Connection To Laptop Using Lubuntu?"
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by tomsubt on 2015-10-04
Hello Everyone,  i have a laptop with Lubuntu on it and when i had dsl it had no problem connecting to the internet. but i just got fios and the laptop will connect hard wired perfectly but it will not connect to the internet using just wifi.
verizon is trying to tell me it is because of Lubuntu os but how can that be if it is hard wired it has no problem connecting to the internet but as soon as i try to go to the internet using the correct username and password it will not connect to the internet. does anyone have a solution for this? Thanks

---

### Post by tgalati4 on 2015-10-04
Open a terminal and post the output of:

```
iwconfig
```

While connected with an ethernet cable, log into your FIOS modem using a webpage (probably [http://192.168.0.1](http://192.168.0.1)) and examine the settings for wireless.  There are a lot of settings that need to be tweaked to get wireless to work correctly.

---

### Post by Hadaka on 2015-10-04
Hi, please open a terminal ctrl/alt/t and do..
```
cat /etc/network/interfaces
lspci -n | awk '/0280/ {print $3}'
```
post the output
thanks

---

### Post by tomsubt on 2015-10-04
ok, guys, it working now, i dont know exactly how but i put the 
Code:

iwconfig
in and some writing came up and on the bottom of that it said wireless network not started or something like that
so all i did was re enter the username and password and it worked right away. i did restart the modem before i did this though. so i am not sure what made it work, i had verizon techs at the house and on the internet and they could not get it to work either. dont have know what happened but Thanks its working now.

---

### Post by tgalati4 on 2015-10-04
What are your connection speeds?  [http://speedtest.net](http://speedtest.net)

---

### Post by tomsubt on 2015-10-04
download 25mb and 26 upload, new fios installation.

---

### Post by tgalati4 on 2015-10-04
Nice.  I only get 3 to 6 Mbits/sec with ATT's crappy DSL and 60-year-old, untwisted copper wire.  My neighbor was promised 45 Mbits/sec with ATT's U-Verse.  Nope, he only got 6-12 Mbits/sec.  (I think U-Verse simply uses 2 DSL lines).  The technician said the lines were too old to support higher speeds.  No kidding.

---

### Post by tomsubt on 2015-10-05
yeah i just got rid dsl with the copper wiring, the fios is more expensive though, hope i can keep up with it, i did not win the lottery yet but still trying!!!!lol!!!

---

