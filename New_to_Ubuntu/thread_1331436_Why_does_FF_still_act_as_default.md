---
title: "Why does FF still act as default?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-11-19
I got google Chrome Unstable for Linux about a week ago.  I liked it so much that I have made it my default web browser and that is how it shows up in System -> Preferences -> Preferred Applications  However, whenever I click on a link anywhere, firefox still asserts itself as if it is the default.  How to make FF stop acting like it is the default web browser when it isn't?

-Yos

---

### Post by viralmeme on 2009-11-19
> **YosefKaro said:**
> How to make FF stop acting like it is the default web browser when it isn't
$sudo update-alternatives --config x-www-browser

---

### Post by YosefKaro on 2009-11-19
So is x-www-browser a variable that I am supposed to add a value to in its stead?

-Yos

---

### Post by wojox on 2009-11-19
Just copy and paste it into the terminal.

---

### Post by YosefKaro on 2009-11-19
Well, I tried that and changed the default to google Chrome in the terminal, however, FF is still popping up as the default browser... You guys have any other ideas?

-Yos


Ok, now I see that I am only having the problem with one application: ShareFire

---

### Post by gradinaruvasile on 2009-11-19
There are applications that have the browser defined in their config rather that take it from the system defaults.
What do you have in System->Preferences->Preferred Applications?

---

### Post by YosefKaro on 2009-11-19
In System->Preferences->Preferred Applications I have google Chrome selected...where can I locate a programs config folder?  If I can find it, I want to change this.

-Yos

---

### Post by gradinaruvasile on 2009-11-19
I dont have that prog installed so i cant tell you but does it have a preferences or similar menu?

---

### Post by YosefKaro on 2009-11-19
I tried that...it only has a 'settings' option but nothing in there no where near what I am looking for.  Looks like I have to try to find out the 'what and where' of the config file.  Thank you for your help.  :D

---

### Post by mocoloco on 2009-11-19
Some apps are dumb and hard-code for only one browser.  I used and app that would only use "mozilla" for links, so I had to create a symlink for mozilla -> firefox.

---

### Post by wojox on 2009-11-19
Is preferred app set to this:

custom

/usr/bin/chrome %s

---

### Post by YosefKaro on 2009-11-19
It's actually an excellent app that I found here (an RSS reader plus a whole lot more).  It just has this dumb feature for whatever reason.

-Yos

---

### Post by gradinaruvasile on 2009-11-19
It is that adobe air based thing?
There is a folder .adobe in my home folder (it seems it is used by adobe reader and the flash plugin), check yourself, maybe you will have something interesting in it.

---

### Post by YosefKaro on 2009-11-19
Yes, 'It is that adobe air based thing' ;)  and thanks for sharing that with me...I will have a look.

-Yos


Laughing Out Loud, it appears to be folder after folder leading to hot air at the end...is that the 'air' that adobe air is referring to.

---

