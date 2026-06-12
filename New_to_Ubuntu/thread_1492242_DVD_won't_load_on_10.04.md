---
title: "DVD won't load on 10.04"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by archie311 on 2010-05-24
Recently installed 10.04. But can not play DVD or Cd commercial or otherwise. gstreamer ugly etc installed, gxine, vlc. libdvdcss2, libdvdread4. everything I can think of. Dvd was working before I installed 10.04. . reconnected the sata lead to the dvd.
When I load a dvd/cd the system freezers, and I can't do anything except remove dvd, wait a few seconds and all seems ok....Never been stumped like this before.. and otherwise like what I have seen of 10.04 so far

---

### Post by c-lou on 2010-05-24
Hi Archie311,

I had the same problem. I solved it using the instructions at 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I needed to restart after running the command  
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Hope it works for you.

c-lou

---

### Post by archie311 on 2010-05-24
Have tried that,,, no harm trying again...Thanks

---

### Post by BigMeanMikeRich on 2010-07-19
Did c-lou's solution solve your problem?  You could try removing 
libdvdread and libdvdcss, then reinstalling.  You could copy and paste 
the following two commands into a terminal (at your own risk!)

```
sudo apt-get remove libdvdread4 libdvdnav4 libdvdcss2

sudo apt-get install ubuntu-restricted-extras libdvdread4 libdvdnav4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

There is some overlap in the install commands (ubuntu-restricted-extras
should automatically install dvdread and dvdnav) but this will make 
absolutely sure* that the proper libraries are installed.

Forgive me if I'm loading you down with obvious advice, but you could 
also try multiple media players if one is giving you trouble.  I prefer 
VLC myself, but MPlayer and Kaffeine are both good choices as well.

If your problems have been solved by any of the advice in this thread, or 
by some other means entirely, please mark it 'SOLVED' so that others know 
to find a solution.  Good luck!

---

