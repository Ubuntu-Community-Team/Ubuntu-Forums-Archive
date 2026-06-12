---
title: "Networking between Ubuntu and Vista"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by dikos on 2009-07-07
Good Morning..

I've spent the last 4 hours trying to figure this out.. 

I have 1 ubuntu and one Vista pc connected wirelessly on my home network.. 

i would like to set the network so that ubuntu can view vista when i click on places >> network.. but not for vista to see ubuntu..

in other words, i would want to hide ubuntu from the network map.. i'm pretty sure the answer lies somewhere in smb.conf

would inserting "browseable = no" under global settings do the trick?

i'll be forever grateful if anyone can help me out..

thanks!

---

### Post by superprash2003 on 2009-07-08
you could try blocking port 137-139 in firestarter or ufw , that should block access

the browseable = no , would only make 1 share hidden

---

### Post by nhasian on 2009-07-08
well if you dont share any folders the vista computer will not be able to access anything.  as far as sharing folders on vista and trying to access them remotely... good luck with that.  Vista really sucks with networking.  i am Microsoft Certified and it only works part of the time for me even when its set up properly.  Maybe we'll have better luck with Windows7 :lolflag:

---

### Post by dikos on 2009-07-08
> **nhasian said:**
> well if you dont share any folders the vista computer will not be able to access anything.  as far as sharing folders on vista and trying to access them remotely... good luck with that.  Vista really sucks with networking.  i am Microsoft Certified and it only works part of the time for me even when its set up properly.  Maybe we'll have better luck with Windows7 :lolflag:
well, i've been using vista before jumping into this warm cup of ubuntu :D

and i've certainly had an easier time hiding the vista computer from the network.. 

will uninstalling samba do the trick? or will i lose my internet connectivity as well? going through smb.conf certainly doesn't mention anything about internet connection per se..

help? ](*,)

---

### Post by nhasian on 2009-07-09
well sure you could uninstall samba with

```
sudo apt-get remove samba
```

this will stop your computer from being able to view windows shares on the network, as well as stop sharing any folders you have on your computer.  it will not affect your internet connection.

---

