---
title: "flash player and firefox 3"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by dodian on 2009-02-25
hi
can some one help me i cant play anything on u tube it keeps coming up with xulrunner-1.9 gnome-supor -user/bin/dpkg error (1) i think it goes a lot deeper than that i cant load firefox 3 neither i can web brows but i had to put on firefox 2 i have been in package manager but keeps coming up with errors ???? this is since i had downloaded updates (i haven't a clue please help dodian :mad:

---

### Post by billgoldberg on 2009-02-25
Hmm strange.

I guess you could try to remove xulrunner and firefox 3, then reinstall them and see if that fixes anything.

```
sudo apt-get autoremove firefox xulrunner flashplugin-nonfree --purge
```

and then

```
sudo apt-get install xulrunner firefox flashplugin-nonfree
```

See if that fixes it.

--

If the package manager gives errors, post the exact error message it give here.

---

### Post by dodian on 2009-02-25
it keeps coming up with xulrunener 1.9 gnome suport
firefox 3 E: sub process user/bin/dpkg error (1) 

thanks for your help

---

