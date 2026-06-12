---
title: "syntax error aireplay-ng"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by fractalman on 2011-05-21
Anybody know how to fix this? i assume i have to edit some text in a file but can someone tell me which file to edit and what text i should change?



sudo aireplay -1 0 -e DELTA.661>256>A7T -a xx:xx:xx:xx:xx:xx: -h xx:xx:xx:xx:xx:xx
bash: syntax error near unexpected token `256



This is MY wifi network,  i'm trying to learn how people crack wifi so i can secure my network properly, i'll understand it a whole lot better when i see the whole process in action so any help would be much appreciated,

Thanks

---

### Post by TeoBigusGeekus on 2011-05-21
WEP can crack in 8min.
Use wpa2 and you have nothing to worry about.

---

### Post by fractalman on 2011-05-21
Yeah, i don't usually have my wifi on at all, it's usually on wpa2 if i ever put it on,  i just wanted to learn how to crack wep and see it in action, but i cant do that till i sort out this syntax error problem.

---

### Post by fractalman on 2011-05-21
Ok sorted it out now :-)   have to put the symbol '\' in front of the symbols in the ESSID

so  DELTA.661>256>A7T becomes

 DELTA.661\>256\>A7T

---

