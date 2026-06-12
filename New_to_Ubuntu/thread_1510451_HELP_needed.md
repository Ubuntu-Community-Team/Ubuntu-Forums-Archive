---
title: "HELP needed"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Bukarts on 2010-06-15
I finaly installed Ubuntu on my main PC at home, and all what I get is black screen  shoving OUT OF range,  I reseted that thing to default, Pluged in Diferent Monitor OLD CTX one :P,  Set lower resolution, pluged in My original monitor,everything fine so far, and After restart all I have is the same Out of range, no matter what resolution I leave before restart.   NOTICE  before restart just with replugin monitors main monitor works great with all available resolutions.  Please help me if anyone has SOLVED such problem . Thanx in advice.

---

### Post by Bukarts on 2010-06-15
Anyone ?

---

### Post by cap10Ibraim on 2010-06-15
what's your video card ? 
and are you using dual monitors or one at a time ?

---

### Post by Bukarts on 2010-06-15
I am using one monitor at a time,  My video card is ATI Radeon X800, Monitor is LG Flatron L1919S

Now I Use DUAL ones if that might help :)

---

### Post by ajgreeny on 2010-06-15
See if you have a /etc/X11/xorg.conf file and if so try renaming it as a backup with ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```  Now try a restart, or a logout and in again to restart x.  You may find that a lack of xorg.conf will allow the system to re-detect all hardware and get you a GUI.  If it makes no difference, you can reverse the whole proceedure with ```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

If that does not help, I will have to leave things to others who are better than I am.

---

### Post by Bukarts on 2010-06-15
Nope, Still the same.  The worst thing is while I keep running both monitors everything works fine, when I plug out 2nd one main one again shows out of range.
also reversed procedure doesnt work.

---

### Post by cap10Ibraim on 2010-06-15
> **Bukarts said:**
> Nope, Still the same.  The worst thing is while I keep running both monitors everything works fine, when I plug out 2nd one main one again shows out of range

while they are both plugged in go to system > prefernce > monitors and choose a monitor and turn off one monitor from there don't unplug it see what happens ?

---

### Post by Bukarts on 2010-06-15
How I can choose them, All I have available is to check Cloned monitors or not.  And in window I see Cloned or unknown. So Now I managed to turn off first one and Leave Main one running. But I am afraid to restart now, since most probably I will get the same place where I was before.

---

### Post by Bukarts on 2010-06-15
Ok! Restarting now ! :P
:lolflag:
Yup Still the same! Out of range once again

---

