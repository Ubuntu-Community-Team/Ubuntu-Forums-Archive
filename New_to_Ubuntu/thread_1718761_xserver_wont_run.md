---
title: "xserver wont run"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by niknafs on 2011-03-31
hey guys please don't laugh as this is really stupid,
well I am running a server so I decided to get rid of gdm at startup,anyway I did few changes(which I assume are the cause of my problem)  and I was successful.
now I just realized to I can't go back to gui anymore

if i run 
/etc/init.d/gdm start    
there is a message : unknown job gdm

if i try to run startx
"No protocol specified" message pops up soo many times

i have reinstall gdm,
tried to use
update-rc.d -f gdm start

update-rc.d -f gdm defaults

update-rc.d -f gdm enable


nothing that picked up from the form seems to work, that's y i posted it here.
I donno wat else to do :(

---

### Post by bodhi.zazen on 2011-03-31
Try ```
sudo apt-get install ubuntu-desktop
```

But honestly, on a server, X is of little benefit. If you need a graphical interface I would suggest any number of web tools such as webmin.

---

