---
title: "Menu Problem In Yahoo Messenger"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by jelsa on 2009-06-12
I did Succeeded to install YM in Ubuntu Jaunty Jackalope, but I can't click nor see menu in YM program.

Tell me to solve this issue and please don't suggest me to use Pidgin, GyachE, etc.

---

### Post by gradinaruvasile on 2009-06-12
You can install it under wine allright, but (at least to me) it is kinda useless afterwards. Its too much Windows stuff involved i think ...

---

### Post by nandemonai on 2009-06-12
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=29](http://appdb.winehq.org/objectManager.php?sClass=application&iId=29)

---

### Post by jelsa on 2009-06-12
[nandemonai]("http://ubuntuforums.org/member.php?u=73922")

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=29](http://appdb.winehq.org/objectManager.php?sClass=application&iId=29)

I cannot see any screenshots for Yahoo Messenger 8.x
Does it run well in Ubuntu especially for the menu?

---

### Post by nandemonai on 2009-06-12
> **jelsa said:**
> [nandemonai]("http://ubuntuforums.org/member.php?u=73922")

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=29](http://appdb.winehq.org/objectManager.php?sClass=application&iId=29)

I cannot see any screenshots for Yahoo Messenger 8.x
Does it run well in Ubuntu especially for the menu?

I use pidgin myself so I can't comment personally. Though winedb has this to say:

> What works
After working on the yahoo messenger for about a week I got it to sign in perfectly, I can IM people with all the effects and everything, audibles work fine, I can read what people send and all. I had to do quite alot of installing with stuff with winetricks and copying some dlls over from ies4linux installation and walla.


What does not

I know that for a fact audio/vid doesn't work, it says that the audio isn't accessible because it's in use but I haven't found out the cause of that yet. Other then that, the UI doesn't like the linux very much you just have to tell wine not to decorate the window and the UI seems to level it self out.

Alright there is quite a few dll overrides I needed to do so I"ll list what I have, I know for a fact riched20 and jscript dll you need atleast to fix the not being able to see anyone type issue. But anyways here is the list I have, noting that some of these dlls that I did not have were taken from ies4linux wine.


What was not tested
Chatrooms, and I haven't really tested much else. 

Looks like there is a bit of work needed to get it functioning ok. I wonder if a virtual install of XP under virtual box might be more useful to you?

Wine is very much hit and miss in my experience.

---

### Post by jelsa on 2009-06-18
After several googling and chating finnaly I know it's just a bug of wine.
I checked site " [http://appdb.winehq.org/](http://appdb.winehq.org/) and see the sreenshot, it also has no Menu.
anybody wants to suggest me?

---

### Post by ~sHyLoCk~ on 2009-06-18
> **jelsa said:**
> After several googling and chating finnaly I know it's just a bug of wine.
I checked site " [http://appdb.winehq.org/](http://appdb.winehq.org/) and see the sreenshot, it also has no Menu.
anybody wants to suggest me?

The only thing I can suggest you is that, use Pidgin. It is a multi-protocol supported IM engine. It has Yahoo, MSN, Gtalk,IRC,etc. Give it a try I'm sure you will love it. ;)

---

### Post by nandemonai on 2009-06-18
[Gyachi]("http://gyachi.sourceforge.net/") is another alternative if you simply must have video / audio support for yahoo messenger.

Still, if it were me I'd use pidgin and stick to something like Skype / Ekiga for audio / video support.

(I know you don't want to hear this but it's pretty much your only option if wine wont run it and you're not prepared to run YM in a virtual machine).

---

