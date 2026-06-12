---
title: "Playing DVD's on 9.04 64 bit"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-24
I tried playing a DVD from blockbuster and i keep getting this error
"An error occurred
Could not read from resource"
this is after about 1 or 2 minutes of movie player being black aka frozen?
any suggestions?

---

### Post by oldos2er on 2009-05-24
Have you installed libdvdcss2? Get it from Medibuntu: [http://medibuntu.org](http://medibuntu.org)

---

### Post by rlj399 on 2009-05-24
I tried installing what you said and this is what i get in the terminal:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I'm guessing that means something went wrong?

---

### Post by rlj399 on 2009-05-24
i went to synaptic package manager and installed libdvdcss2 but it had no effect :-\

edit: ok after like 1 minute of it being black, it played about 10 seconds of the film and got black again and gave the error message :-\

---

### Post by Duskao on 2009-05-24
Well, I think probably the easiest way to enable the ability to play DVD's is to go to add/remove then look for ubuntu restricted extras. Gives you everything you need (and a whole lot more). If you are new to linux or ubuntu then it makes it really nice to help settle in with ubuntu, cause it gives you a lot of the "necessities" that widows users are used to like flash, java, ability to play DVD's and MP3s. If it doesn't work for ya, just uninstall it the same way you installed it.

---

### Post by oldos2er on 2009-05-24
w32codecs is available via Medibuntu, same as libdvdcss2.

---

### Post by gandaran on 2009-05-25
> **rlj399 said:**
> i went to synaptic package manager and installed libdvdcss2 but it had no effect :-\

edit: ok after like 1 minute of it being black, it played about 10 seconds of the film and got black again and gave the error message :-\
which player did you use? Totem?
totem-gstreamer doesn't play dvd's with menus, for dvd's with menus install another player either totem-xine, mplayer, vlc and gxine.

---

### Post by Kevbert on 2009-05-25
Use totem-xine and install ubuntu-restricted-extras. They can be found in Synaptic.

---

### Post by rlj399 on 2009-05-25
I was trying the one that comes with Ubuntu, apparently it's just called movie player 0_o
well to solve my problem i just installed VLC, thanks anyways though guys

---

### Post by XCan on 2009-05-25
> **rlj399 said:**
> I was trying the one that comes with Ubuntu, apparently it's just called movie player 0_o
well to solve my problem i just installed VLC, thanks anyways though guys

Just for future reference. The player that comes with Ubuntu is Totem. My personal opinion is that its functionalities are lacking.

---

### Post by balloooza on 2009-05-25
BTW, being a strong open software advocate, I prefer to use all open, or all legal.

Technicaly, playing dvd' on ubuntu is semi- legaly unstable (depending on where you live, and where you bought the dvds.

The best dvd playback is recieved from getting:
[http://shop.canonical.com/product_info.php?products_id=243&osCsid=163e2f43bd862d1562994f181b675109](http://shop.canonical.com/product_info.php?products_id=243&osCsid=163e2f43bd862d1562994f181b675109)
although the website says it only works with 8.10 and 8.04 LTS

---

