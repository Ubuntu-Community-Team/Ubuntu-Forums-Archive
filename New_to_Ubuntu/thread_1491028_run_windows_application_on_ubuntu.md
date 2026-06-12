---
title: "run windows application on ubuntu"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by neodjary on 2010-05-23
hai guys, i an completly newbie in linux, right now i'm using dual boot ubuntu 10.04 and windows xp. actually i want to throw away my  xp and all application in it and change with linux program, but i can not leave my embroidery  software (wilcom es designer), i have tried to using wine..., its work .but i can set the default measurement to metric unit (milimeter using regional and language setting in windows).anybody can help me? ireally need this software ..any solution? thanks before

---

### Post by SlidingHorn on 2010-05-23
Looking online I found a couple things that *might* work.

The first one had to do with checking the .reg files in your wine directory:

```
cd ~/.wine
gedit <filename>.reg
```

**Do NOT** change these files if you aren't absolutely sure you know what you're doing.

The other option I saw was to start wine under a specific language setting:

```
LANG=en_UK wine ...
```

I don't know if the lang settings will have any control over the measurement systems, but it might be worth a shot.  

Hope this helps

---

### Post by Silent Warrior on 2010-05-23
<Eh, scratch that.>

---

### Post by neodjary on 2010-05-29
its [SIZE=5]solved[/SIZE], thanks to SLIDINGHORN..its inpire me

i use [SIZE=5]regedit [/SIZE]from wine ,and then goto user local>>sontrol panel>>> international>>>change imeasure value from 1  to 0, and  ..........my windows application run on wine with default matric unit(milimeter)


thanks

---

