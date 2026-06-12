---
title: "Background does not apply"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by karthick87 on 2011-05-05
I have changed my background. But it does not take effect. I guess it seems to be permission issue. I checked the value in gconf-editor it says "The key is not writable". Look at the screen shot pls.

---

### Post by karthick87 on 2011-05-10
Bump..

---

### Post by plucky on 2011-05-10
What are the permissions on the file? ```
ls -l /usr/share/backgrounds/
``` and post

---

### Post by karthick87 on 2011-05-10
```
karthick@karthick:~$ ls -l /usr/share/backgrounds/
total 3772
-rw-r--r-- 1 root root 289945 2010-09-13 21:37 Aeg_by_Tauno_Erik.jpg
-rw-r--r-- 1 root root 116263 2010-09-13 21:37 Blue_box_number_2_by_orb9220.jpg
-rw-r--r-- 1 root root 184981 2010-09-13 21:37 Blue_by_ElSlunko.jpg
-rw-r--r-- 1 root root 191920 2010-09-13 21:37 Bubbles_by_JanneM.jpg
drwxr-xr-x 2 root root   4096 2010-10-07 21:39 contest
drwxr-xr-x 2 root root   4096 2010-10-07 21:36 cosmos
-rw-r--r-- 1 root root  73530 2010-09-13 21:37 Crocosmia_by_sirpecangum.jpg
-rw-r--r-- 1 root root 123677 2010-09-13 21:37 Feather_by_quinn.anya.jpg
-rw-r--r-- 1 root root 170908 2010-09-13 21:37 Fern_by_aalex04.jpg
-rw-r--r-- 1 root root 360889 2010-09-13 21:37 Life_by_Paco_Espinoza.jpg
-rw-r--r-- 1 root root 197864 2010-09-13 21:37 Liquid_glass_by_matthileo.jpg
-rw-r--r-- 1 root root 158893 2010-09-13 21:37 Mirada_Perduda_by_Marxicoli.jpg
-rw-r--r-- 1 root root 117257 2010-09-13 21:37 Morning_II_by_Tadas_N.jpg
-rw-r--r-- 1 root root  80352 2010-09-13 21:37 Primer_Amanecer_2010_by_letoloke.jpg
-rw-r--r-- 1 root root  95876 2010-09-13 21:37 Ropey_Photo_by_Bob_Farrell.jpg
-rw-r--r-- 1 root root 142344 2010-09-13 21:37 Serenity_Enchanted_by_sirpecangum.jpg
-rw-r--r-- 1 root root 107146 2010-09-13 21:37 Smile_by_quinn.anya.jpg
-rw-r--r-- 1 root root  75689 2006-05-18 07:23 space-01.jpg
-rw-r--r-- 1 root root  83842 2006-05-18 07:23 space-02.jpg
-rw-r--r-- 1 root root  31661 2006-05-18 07:23 space-03.jpg
-rw-r--r-- 1 root root  78323 2006-05-18 07:23 space-04.jpg
-rw-r--r-- 1 root root  14620 2006-05-18 07:23 space-05.jpg
-rw-r--r-- 1 root root 118342 2010-09-13 21:37 Spiral_by_firas.jpg
-rw-r--r-- 1 root root 911546 2010-09-14 23:38 warty-final-ubuntu.png
-rw-r--r-- 1 root root  85517 2010-09-13 21:37 Waterchain_by_Poje_Mario.jpg
karthick@karthick:~$ 

```

---

### Post by mcduck on 2011-05-10
If the gconf key is not writable, that definitely isn't because of the *picture's* permissions.

Either the gconf file itself has wrong permissions (make sure you own everything in ~/.gconf directory) or the current key value has been set as mandatory (which would require running gconf-editor as root, so it's unlikely that would happen by accident. I'd look at the gconf file permissions first).

---

### Post by karthick87 on 2011-05-10
Yes the key has been set to mandatory. How to revert it back ?

---

### Post by mcduck on 2011-05-10
Run gconf-editor as root ("gksudo gconf-editor"), then select File->New Mandatory Window and that should give you access to mandatory keys & allow you to unset them.

---

### Post by karthick87 on 2011-05-10
Thanks a ton :) it solved my problem. But is there a way to unset the key via terminal ?

---

### Post by mcduck on 2011-05-10
> **karthick87 said:**
> Thanks a ton :) it solved my problem. But is there a way to unset the key via terminal ?

gconftool should allow you to do that, but I've never used it with mandatory/default settings so I can't say more about how exactly that would work.

---

### Post by karthick87 on 2011-05-10
Any how thanks a  lot :)

---

