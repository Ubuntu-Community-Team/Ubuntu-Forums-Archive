---
title: "Changing fonts"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by lizandeen on 2009-01-07
I'm having problems with my 8.10 upgrade and I think my problems may arise from the fact that it is trying to boot with a customized font that it no longer recognizes. Is there any way I can change the font to a generic one using the command line (I cannot access the terminal)? Thanks.p.s.the simpler the explanation the better!

---

### Post by RobsterUK on 2009-01-08
What error message is it giving you when you run the upgrade?

---

### Post by jskandhari on 2009-01-08
Please BE more specific.. as the error and other details.. provide the symptoms not only the problem.

---

### Post by lizandeen on 2009-01-08
After boot a (I presume) warning/error box comes up but is unreadable because it consists of small rectangle boxes with a warning sign in the top left corner. Then using [startx] (the only way I can reach the Intrepid Desktop) instead of letters or numbers all that can be seen is small upright rectangles. Also the mouse cursor is frozen so I cannot "guess" my way to changing the font from here. Hope this is a bit clearer. Thanks

---

### Post by albinootje on 2009-01-08
> **lizandeen said:**
> I'm having problems with my 8.10 upgrade and I think my problems may arise from the fact that it is trying to boot with a customized font that it no longer recognizes. Is there any way I can change the font to a generic one using the command line (I cannot access the terminal)? Thanks.p.s.the simpler the explanation the better!

Did you finish the upgrade completely ?

Please boot in "recovery mode" and choose "drop to root shell prompt", and run the following :
```

df -h
dhclient
apt-get update
dpkg --configure -a
apt-get -f install
apt-get dist-upgrade

```
Please post any errors.

---

### Post by lizandeen on 2009-01-14
No luck with that,I'm afraid.

---

### Post by albinootje on 2009-01-14
> **lizandeen said:**
> No luck with that,I'm afraid.

Perhaps the best and easiest for you is to boot from an Ubuntu installation cdrom, make proper backups from your /home to some usb-disk, and then do a fresh install of 8.10.

---

### Post by lizandeen on 2009-01-15
Thanks, I think that's my only option if I want to carry on with 8.10 (though in the meantime I'll stick with my old 8.04!)

---

