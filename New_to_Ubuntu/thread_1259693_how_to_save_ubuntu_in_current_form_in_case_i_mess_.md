---
title: "how to save ubuntu in current form in case i mess it up"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by nh5y on 2009-09-06
i've already had to reinstall  ubuntu twice because i was playing around with ccsm and it distorted my screen (it was distorted even after rebooting a couple times).

i was wondering if there's a way to save ubuntu in its current form on my external so that i can play around with ubuntu without having to reinstall if i mess something up again.

step-by-step instructions would be ideal!!  thanks!

natasha

ps- i have a vaio vgn-txn17p in case you have any general advice about ubuntu on my particular computer

---

### Post by Lukica18 on 2009-09-06
I think this is what you need.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by mgranet on 2009-09-06
If you have an large enough external drive, you can use something like [CloneZilla]("http://clonezilla.org/") to essentially ghost your OS to a compressed folder on your external. I've used this with great results many times. Backing up and restoring using this method only requires you to answer a few basic questions. If you read everything it tells you, it's difficult to make a mistake. Note: Don't mess with keymaps ;)

---

### Post by nh5y on 2009-09-06
thanks for the replies!

on another note, i'd like to add some apps to my startup programs, so i know that the way to do that is to go to system --> preferences --> sessions... but i don't have "sessions"  is there a different way to get to it?  i know i had it with ubuntu 8.04, but now i'm using 9.04 and i just can't find it.

---

### Post by fela on 2009-09-06
About the compiz problem - that would never require a reinstall. Just login to a text terminal, and run:

```
DISPLAY=:0 metacity --replace&
```

Then you can fix your ccsm settings by going back to the GUI.

---

### Post by nh5y on 2009-09-06
found it!  my question was hasty. it was under system --. preferences --> startup applications

---

### Post by zipperback on 2009-09-06
> **nh5y said:**
>  so i know that the way to do that is to go to system --> preferences --> sessions... but i don't have "sessions"  is there a different way to get to it? 

System -> Preferences -> Startup Applications

- zipperback
:popcorn:

---

