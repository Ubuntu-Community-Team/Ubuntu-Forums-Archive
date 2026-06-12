---
title: "xorg conf advance help"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-05-24
been using linux for years and it is amazing how i can still mess things up.
i have my computer hooked up to my tv so can watch movies. somehow i messed up x so i cant get the movies to play on the tv. if however i boot up my ubuntu 11.04 live cd x seems to be fine. how i change my x to be the same as on the live cd. that would fix the problem. any ideas. if you need more info i can supply. really dont want to reinstall 11.04 only as a last resort//tks

---

### Post by rburkartjo on 2011-05-24
should i be able to copy the default x conf from the live cd etc file and then paste in my etc file on my machine.

---

### Post by FormatSeize on 2011-05-24
> **rburkartjo said:**
> should i be able to copy the default x conf from the live cd etc file and then paste in my etc file on my machine.
That should work, so long as you were able to play movies through your television with no modifications to your Xorg conf file to get it to play movies in the first place. Also, if that is the case, I would back-up your old Xorg conf file (the one that currently won't let you play movies anymore, possibly call it Xorg conf_old), and then replace that one with the copied one. 
That is probably going to require sudo permissions, by the way.

---

### Post by Paqman on 2011-05-24
Ubuntu doesn't actually use an xorg.conf any more, although it will try to obey it if you create one. So to reset it to the default, just delete xorg.

---

### Post by rburkartjo on 2011-05-24
paq and what be the command to do that

---

### Post by Paqman on 2011-05-24
To delete it:
```
sudo rm /etc/X11/xorg.conf
```
Or, more conservatively, to rename it:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg_bak.conf
```

To do this graphically, hit ALT-F2, type:
```
gksudo nautilus
```
then navigate to /etc/X11 and delete or rename the file. That's a root file manager window, so make sure you close it after you're done.

---

### Post by bodhi.zazen on 2011-05-24
you should be able to set a resolution with xrandr

```
xrandr -q
```

now choose one of those

```
xrandr -s 1400x1050
```

see also man xrandr =)

---

### Post by rburkartjo on 2011-05-26
tks ya'll

---

### Post by bodhi.zazen on 2011-05-26
> **rburkartjo said:**
> tks ya'll

For the benefit of others, would you mind posting your  solution ?

---

