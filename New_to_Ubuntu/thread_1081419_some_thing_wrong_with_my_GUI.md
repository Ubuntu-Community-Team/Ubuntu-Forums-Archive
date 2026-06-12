---
title: "some thing wrong with my GUI"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-26
hi i have installed Ubuntu 8.04(Wubi)
my system hanged (not even keyboard or mouse worked)
so i pressed restart button at that time update manager was installing some thing 
after restart my system GUI changed i checked the Appearance it shows the same properties as before 
1)Taskbar is not visible for anything
2)Theme has become grey color
3)All icons have changed
help me i am new to ubuntu

---

### Post by kansasnoob on 2009-02-26
I don't know Wubi well at all, I tried it once when 8.04 came out, but generally if an update is interrupted you'd need to run in terminal:

```
sudo dpkg --configure -a
```

But Wubi is rather a beast all it's own. 

Sadly the Wubi Forum seems to be down so I can only send you here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by avtolle on 2009-02-26
Another thing to think about: since you hit the power button to shut off your computer, you should run chkdsk -r (I think that's the correct command) from Windows; the Wubi Guide will give you some information about that, too.

---

### Post by kansasnoob on 2009-02-26
Ah, it helps to read, "feel free to ask for help on the Ubuntu Forums in the Installations & Upgrades section - don't forget to let them know that you're using Wubi"

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

I know they had a Wubi forum at one time.

---

### Post by kansasnoob on 2009-02-26
> **avtolle said:**
> another thing to think about: Since you hit the power button to shut off your computer, you should run chkdsk -r (i think that's the correct command) from windows; the wubi guide will give you some information about that, too.

+1

---

