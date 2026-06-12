---
title: "Can't install Cairo dock in Karmic"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by bteotarigan on 2009-11-10
I've just recently upgrade to Karmic and find out that my AWN can't work on it. It's not a problem coz i'm thinking of switching to Cairo anyway. But i failed everytime installing Cairo. Is it just me? due to my system, i can't use compiz.

---

### Post by asuastrophysics on 2009-11-11
cairo-dock should work anyway, despite not having compiz installed. 
Does your graphics card support compiz?
try this:
```
compiz --replace
```
then this:
```
sudo apt-get install compizconfig-settings-manager
```

Also, it is common for Cairo-dock not to work quite right after installing it in Karmic. This is because Ubuntu forgets to install the cairo-dock plugins package. :P

so try this:
```
sudo apt-get install cairo-dock-plug-ins
```

Since you said you already have Cairo-Dock installed (it just won't run), I'm assuming you've already added it to your sources list. ;)

Did that help?

---

### Post by bteotarigan on 2009-11-11
i've tried the first command: compiz --replace.
The dock loaded at the first seconds! then the process took forever to completed. So i got no choice. I had to kill the process.
The second time i tried the command, the dock was not loaded anymore. And the same process still took forever to be completed. :(

---

### Post by asuastrophysics on 2009-11-11
ok obviously you can't run compiz.

run this: 
```
metacity --replace
```

and then execute that code I gave you earlier for installing cairo-dock and the plug-ins. 

cairo dock should launch without compiz, albight not looking as good. 

When you launch 
```
cairo-dock
```
in terminal, what output comes after it? does it give an error?

---

### Post by fabounet on 2009-11-12
how did you install the dock ?
the only reliable way is here :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
(because at the moment, the version on the Ubuntu repository does not integrate the latest bug fixes to make it work on Karmic)

Edit : you should completely deinstall it before you install the new version, just to avoid possible conflicts.

---

### Post by asuastrophysics on 2009-11-13
> **fabounet said:**
> how did you install the dock ?
the only reliable way is here :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
(because at the moment, the version on the Ubuntu repository does not integrate the latest bug fixes to make it work on Karmic)

Edit : you should completely deinstall it before you install the new version, just to avoid possible conflicts.

+1 I had forgotten that this is where I downloaded my copy.

---

### Post by bteotarigan on 2009-11-17
Hey thanx both of you. Finally, it works. Must be the way i installed the dock. i've made it works after i deinstall the old version and reinstall the new one. :)

---

