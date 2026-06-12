---
title: "laptop mouse pad not working with 9.10 update"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by jaceh14 on 2009-12-14
hello all, i have a gateway laptop, and i just updated my 9.04 to 9.10. my mouse was working fine with 9.04, but after the update, i have to use a USB mouse to do anything. i checked for driver updates in ubuntu, but it couldn't find any. anyone have any ideas? it's not that big of a deal to not have the mouse pad because of the extra mouse i have, but i'd like to be able to use it so i don't have always plug in my other one. thanks for the help

jace

---

### Post by cartisdm on 2009-12-14
I'm not sure which touchpad you have but trying installing gsynaptics

```
sudo apt-get install gsynaptic
```

---

### Post by dearingj on 2009-12-14
> **cartisdm said:**
> I'm not sure which touchpad you have but trying installing gsynaptics

```
sudo apt-get install gsynaptic**_s_**
```

Corrected a typo for you :)

---

### Post by jaceh14 on 2009-12-14
here is the error i get when i try to load gsynaptics:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

i tried to edit the xorg file, but SHMConfig wasn't anywhere in the file. i'll keep searching for a different xorg.conf file, but any ideas?

jace

---

### Post by cartisdm on 2009-12-14
you need to add

```

Option "SHMConfig" "1" 
```

in the xorg.conf file under the touchpad section.  Then restart X with Ctrl + Alt + Backspace


EDIT: in 9.10 I remember seeing a thread that it isn't Ctrl + Alt + Backspace anymore but I don't remember what the keystroke is.  If you don't know then just restart your computer to get the same effect

---

### Post by Quindos on 2009-12-15
The mousepad didn't work for me either.
I tested the 2.6.31-16 kernel instead of the -17, and Herueka, it works again.
// Have fun

---

