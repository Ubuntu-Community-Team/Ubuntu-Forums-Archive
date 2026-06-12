---
title: "Windows XP Theme"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by crisco552 on 2009-08-03
My parents use windows xp and I'm trying to convert them to Ubuntu so I installed an Aero theme that looks exactly like vista. Do you know what my dad said he said "I don't like Vista" so now I'm trying to find a XP theme including the login screen could someone help me? and if not could someone help me figure out how to make a theme?

---

### Post by coldReactive on 2009-08-03
```
sudo apt-get install emerald
```

[http://gnome-look.org/content/show.php/Luna+Element?content=108878](http://gnome-look.org/content/show.php/Luna+Element?content=108878)

```
emerald --replace
```

profit

---

### Post by realzippy on 2009-08-03
You installed ubuntu in Vista-look or XP in Vista-look?
Anyway,why do they not like ubuntu?

---

### Post by hessczoo on 2009-08-03
I haven't seen a theme that looks too much like XP. The nice thing about Ubuntu is it is something different. Maybe try letting your father pick out a style that is to his liking, he will find the layout of the bars is far better than that of XP.

---

### Post by SunnyRabbiera on 2009-08-03
Well there are a few good XP theme clones (the theme is called luna by the way)
Here a few Luna like themes:
[http://gnome-look.org/content/show.php/LUNA-EVO?content=109106](http://gnome-look.org/content/show.php/LUNA-EVO?content=109106)

[http://gnome-look.org/content/show.php/XPLuna2?content=84873](http://gnome-look.org/content/show.php/XPLuna2?content=84873)

[http://gnome-look.org/content/show.php/XP+2002?content=100380](http://gnome-look.org/content/show.php/XP+2002?content=100380)

Personally I like Lunacy:
[http://gnome-look.org/content/show.php/Lunacy?content=71170](http://gnome-look.org/content/show.php/Lunacy?content=71170)

For a XP like icon theme:
[http://gnome-look.org/content/show.php/GnomeXP?content=69587](http://gnome-look.org/content/show.php/GnomeXP?content=69587)

For a XP like start Button, that will be a little difficult.

---

### Post by RJ12 on 2009-08-03
Have you tried the XPDE Environment dont know if it has a login screen but its worth a try

---

### Post by lykwydchykyn on 2009-08-03
Google search turned this up:
[http://ubuntu.online02.com/node/14](http://ubuntu.online02.com/node/14)

It may be helpful.

It might be helpful to talk with your parents a little more about what they do/don't like about XP/Vista/Ubuntu.  A theme sometimes makes people more comfortable, but it doesn't magically transform Linux into XP.  In fact, sometimes it works against you, because it LOOKS like Windows but doesn't ACT like windows.

Sometimes simple things like turning off effects and putting the panel back on the bottom go a long way towards making people comfortable on a machine.

---

### Post by ubudog on 2009-08-03
> **crisco552 said:**
> My parents use windows xp and I'm trying to convert them to Ubuntu so I installed an Aero theme that looks exactly like vista. Do you know what my dad said he said "I don't like Vista" so now I'm trying to find a XP theme including the login screen could someone help me? and if not could someone help me figure out how to make a theme?

Look on [http://art.gnome.org/themes/search?text=xp](http://art.gnome.org/themes/search?text=xp) :) You'll probably like the eXperience one.

---

### Post by crisco552 on 2009-08-03
Wow thanks guys I will look at that stuff and figure out which one will work the reason he doesn't use linux is that the programs at his work require Windows but they probally can run on wine. His IT person is a linux fan as well but the lab only has a couple linux servers so... sorry I am confusing my self but he has just used Windows ever since XP came out before that we used Mac OS 7 so Linux hasn't bbeen used much in the family. I'm probaly the only person at my school that uses linux. But yeah I will look at all those themes and follow your suggestions including having him choose a custom theme. Thanks all.

---

### Post by egalvan on 2009-08-03
> **crisco552 said:**
> Wow thanks guys I will look at that stuff and figure out which one will work
**His IT person is a linux fan **as well but the lab only has a couple linux servers so...

Having the IT guy as a Linux fan will go a LONG way to helping your father. Now he has Linux in common with him.

---

### Post by crisco552 on 2009-08-03
Okay I have the theme installed including the emerald them but the problem is is that whenever I close Teminal the emerald theme goes away? anyway to fix this

---

### Post by coldReactive on 2009-08-03
> **crisco552 said:**
> Okay I have the theme installed including the emerald them but the problem is is that whenever I close Teminal the emerald theme goes away? anyway to fix this

System > Administration (or preferences, can't remember) > Startup Applications

add a new application/command and have the command text input say emerald --replace. Name it Emerald Theme Manager. Emerald effects such as wobbly windows, etc. are all controllable via ccsm. Log out and log back in.

Also, you can't use metacity themes while using emerald.

---

### Post by crisco552 on 2009-08-03
I can't find startup applications is it possible to launch it through terminal

EDIT: I found it, it is under sessions so now it works yeah!!!!

---

### Post by Mark Phelps on 2009-08-03
> **crisco552 said:**
> ... the reason he doesn't use linux is that the programs at his work require Windows but they probally can run on wine ...

Don't bet on it!!

Wine is very picky about which MS apps, and even moreso, which versions of MS Apps will work.

Before you "force Ubuntu" onto someone else, do some research by checking the CodeWeavers Application Compatibility site (link below) for the apps and versions used. IF you don't see any results, or if the ratings you get are not at least Gold or Platinum, you won't be able to use Wine for those apps:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Also, as one of the other poster pointed out, just because it looks like XP doesn't mean it will work like XP.  What's likely to be more confusing and frustrating: (1) something looks and behaves very different from what you're used to, or (2) something that looks like what you're used to but behaves differently?  Most will agree it's the second.

So, be prepared for lots of complaints about how "nothing works" in Ubuntu.

---

### Post by jacklinux on 2009-08-03
> **Mark Phelps said:**
> Don't bet on it!!

Wine is very picky about which MS apps, and even moreso, which versions of MS Apps will work.

Before you "force Ubuntu" onto someone else, do some research by checking the CodeWeavers Application Compatibility site (link below) for the apps and versions used. IF you don't see any results, or if the ratings you get are not at least Gold or Platinum, you won't be able to use Wine for those apps:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")
or not well.

---

### Post by Mark Phelps on 2009-08-03
> **jacklinux said:**
> or not well.

Yeah, you're technically correct -- you can get stuff that's rated Bronze or Silver to work, but that often comes at the cost of limited functionality.  You want to force something that only partly works in Wine on someone when they already have a functioning XP system? 

Not me.  

They won't understand that it's a "Wine problem"; they'll only get frustrated by things not working -- and they'll blame "Linux". 

Good way to ensure that we lose another potential Ubuntu convert.

---

### Post by jacklinux on 2009-08-03
> **Mark Phelps said:**
> Yeah, you're technically correct -- you can get stuff that's rated Bronze or Silver to work, but that often comes at the cost of limited functionality.  You want to force something that only partly works in Wine on someone when they already have a functioning XP system? 

Not me.  

They won't understand that it's a "Wine problem"; they'll only get frustrated by things not working -- and they'll blame "Linux". 

Good way to ensure that we lose another potential Ubuntu convert.
Yeah, i hear you. However i installed World of Warcraft and it was rated 'unussable' however it still worked fine. I guess more people just need to try things.

---

### Post by coldReactive on 2009-08-03
> **jacklinux said:**
> Yeah, i hear you. However i installed World of Warcraft and it was rated 'unussable' however it still worked fine. I guess more people just need to try things.

People aren't inclined to run unstable versions of Wine, nor the addons such as winetricks (in fact, I can't even recall HOW TO INSTALL the addons.)

---

