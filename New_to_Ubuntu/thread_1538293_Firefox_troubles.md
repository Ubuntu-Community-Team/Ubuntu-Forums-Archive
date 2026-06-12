---
title: "Firefox troubles"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Azatos on 2010-07-24
I just did a fresh install of 10.04 after getting rid of win 7.  Now I have a problem when I go to start firefox it will show the little bar saying firefox is loading or something and then it will just go away and firefox will never open.  The system manager thing doesnt have firefox as running and on the ubuntu software thing it is not listed as being installed.

What do?

---

### Post by lovinglinux on 2010-07-24
Open a Terminal (Applications > Accessories > Terminal) then run the following command to re-install firefox:

```
sudo apt-get install --reinstall firefox
```

If that doesn't help, then perhaps you have a problematic extension or a corrupted profile. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial. Do the tests suggested there, then report back with the results.

---

### Post by d3v1150m471c on 2010-07-24
that will keep the configuration files, lovinglinux. he'll need to do a purge if a corrupt configuration is causing the problem. 
```

sudo apt-get purge firefox
sudo apt-get install firefox

```

---

### Post by lovinglinux on 2010-07-24
> **d3v1150m471c said:**
> that will keep the configuration files, lovinglinux. he'll need to do a purge if a corrupt configuration is causing the problem. 
```

sudo apt-get purge firefox
sudo apt-get install firefox

```

Purging Firefox does not remove corrupted profiles and configuration files. The purge command removes system configuration files, not the user configuration files from the user profile, which are usually the source of Firefox problems and reside under ~/.mozilla/firefox/.

---

### Post by walt.smith1960 on 2010-07-25
I just had something very similar to the O P's problem--Firefox looks like it's going to start but didn't.  This occurred after an  update on a 64 bit Karmic install.  This was SWMBO's machine-- "YOU BROKE IT!!!" :-&.  Tried the usual fix first -- reboot-- nope,  didn't fix it.  Then tried powering all the way down and restart.  Success!  So you might try powering down and restarting before reinstalling.

---

