---
title: "Can't change resolution higher than 800x600 under VirtualBox"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by wrathofmobius on 2011-01-22
I know this question's already been asked, but none of the solutions provided work for me. Also, I am a complete Linux n00b, so any advice that doesn't require any knowledge that I can't Google would be appreciated.

Just yesterday, I got Ubuntu (10.10) working under VirtualBox (3.2.12), and got everything set up so that I can do pretty much whatever I need under Linux. Unfortunately, I can't get the screen resolution higher than 800x600 px. I did do a lot of Googling about this problem, so this is the list of things I did and why they failed:

-Trying to set it through Ubuntu (duh!): 800x600 px is the best option.
-Giving it more virtual RAM: Did nothing.
-Installing guest additions: Did nothing.
-Editing xorg.conf: It's empty. (Yes, I did use sudo gedit instead of just opening it up the normal way.)
-Installing the virtualbox-ose-guest-x11 package: Did nothing.

I'm pretty sure that's all I found, so I'm a bit lost on how to do this as, again, I'm a complete n00b.

---

### Post by stmiller on 2011-01-22
Use virtualbox 4.x?

---

### Post by wrathofmobius on 2011-01-23
Wow, I checked the date on when 4.x was released, and apparently, I got 3.x the day or two before 4.x was released.

Anyway, that fixed it!

---

