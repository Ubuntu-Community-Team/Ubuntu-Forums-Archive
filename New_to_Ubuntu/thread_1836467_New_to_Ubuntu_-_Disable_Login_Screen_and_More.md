---
title: "New to Ubuntu - Disable Login Screen and More"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by gastoj on 2011-08-31
Hey people,

Ubuntu is pretty complicated. Firstly, the power icon in the top panel is now gone. How can i get it back? Secondly, I would like to know how to change the screen resolution at login, and also how to totally disable the login screen. I've tried all this myself, I have been sitting for a few hours now without being able to find a solution. I've tried opening GDM.. I've found it in the Software Center. Why isn't there an option to just click on it from there and run it? It shows that it is installed. How can I run GDM?

Also Why does it ask for authentication when I want to change something? Can I turn that off too? 

Thanks in advance

Kaspr

---

### Post by drpjkurian on 2011-08-31
Hi
May I know which version of Ubuntu are you using?

To get the shut down button-Right click on the top panel and select add to panel. Select shutdown button from there.

---

### Post by gastoj on 2011-08-31
Sorry, I am using 11.04 (Natty).. Ubuntu Classic (no effects)

---

### Post by drpjkurian on 2011-08-31
Ok 
So that means you are already running on GDM(GNOME Display Manager).
Well to disable the login screen-Please open 'login screen' and select login
as automatically.

To change the screen resolution select 'monitor' from preferences (i hope so)and change the resolution

Did these help you?

---

### Post by westie457 on 2011-08-31
Hi welcome to the Forums.

To answer some of your questions

> Firstly, the power icon in the top panel is now gone. How can i get it back?

If you mean the one for the battery, that can be set through Settings > Preferences > Power Management.

> Secondly, I would like to know how to change the screen resolution at startup, and also how to totally disable the login screen

No idea how to change the resolution at start up. Disable the Log in Screen through Settings > Administration > Login Screen. Your password will be needed.

> Also Why does it ask for authentication when I want to change something? Can I turn that off too?

System Security is asking you for permission to make changes to system files. Yes it can be turned off however I am not going to explain how because it is dangerous to your system to allow just about anything to install itself to your computer.

> How can I run GDM?

No idea because it is a default on my system and starts automatically

---

### Post by madjr on 2011-08-31
[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)

[http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html)
[http://www.youtube.com/watch?v=hZKNGXMSChE](http://www.youtube.com/watch?v=hZKNGXMSChE)

[https://help.ubuntu.com/community/Applets](https://help.ubuntu.com/community/Applets)
[http://www.youtube.com/watch?v=s655jL3_kuU](http://www.youtube.com/watch?v=s655jL3_kuU)


and passwords are there to protect your system from other people or malicious programs from modifying it.

If you dont like passwords you can always log in as root, but that is not recommended for a novice and you could break your system without knowing.

---

### Post by gastoj on 2011-08-31
Thanks for all the replies. It helped a a lot. I ment the screen resolution in the login screen though.. I saw something called Login Window in applications of other ubuntu version.. you could change the resolution there.. and now you only have login screen.  I have found the power icon, it was called somethng like indicator applet session, confusing.

---

### Post by madjr on 2011-08-31
> **gastoj said:**
> Thanks for all the replies. It helped a a lot. I ment the screen resolution in the login screen though.. I saw something called Login Window in applications of other ubuntu version.. you could change the resolution there.. and now you only have login screen.  I have found the power icon, it was called somethng like indicator applet session, confusing.

well you're using classic, which is not going to be supported any more and yes, the learning curve is higher since is very flexible...

But the new default interface in ubuntu is now "**unity**" (or just ubuntu) and is far easier since it has built in search and you wont lose your power icon again, since is locked in the panel :)

i recommend (if your computer supports it to switch from classic to ubuntu/unity) by login out.

and this should help you learn your way around, very quickly:

video:
[http://www.youtube.com/watch?v=KDIGOtInoKY](http://www.youtube.com/watch?v=KDIGOtInoKY)

pdf:
[http://iloveubuntu.net/meet-unity-simplify-your-life-free-pdf-book-about-ubuntus-unity](http://iloveubuntu.net/meet-unity-simplify-your-life-free-pdf-book-about-ubuntus-unity)

---

### Post by gastoj on 2011-08-31
unity is too heavy for my system.. it slows down things. I have a big problem now : (.. when i rebooted my pc only a black screen with ubuntu login and password appeared.... this is after i did something like sudo nano /etc/grpoup/ and changed the file contents.. (it said its a bugfix for soundcard problems..) omg...coz my sc doesnt work lol.. im so  tired of this

---

### Post by madjr on 2011-08-31
> **gastoj said:**
> unity is too heavy for my system.. it slows down things. I have a big problem now : (.. when i rebooted my pc only a black screen with ubuntu login and password appeared.... this is after i did something like sudo nano /etc/grpoup/ and changed the file contents.. (it said its a bugfix for soundcard problems..) omg...coz my sc doesnt work lol.. im so  tired of this

ok, unity 2d will be available soon and should work on all systems. It behaves exactly as unity 3d, but without the performance hit on older hardware. So for now is ok if you stay with classic.

As for the bug, can you post the link where you got your instructions? not sure exactly what you did :p

---

### Post by gastoj on 2011-08-31
[http://ubuntuforums.org/showthread.php?t=1836562](http://ubuntuforums.org/showthread.php?t=1836562)


ive started a new thread for this.. somebody who is helping me there said i might be in major trouble :s

---

### Post by madjr on 2011-08-31
hehe, i get in major trouble on daily basis, i purposely break my system just to try new stuff :D

in fact am using the alphas/betas for next ubuntu release to make it better and help report/fix the bugs i can.

and glad to see you got it restored!

you are becoming a pro!

---

### Post by gastoj on 2011-08-31
thank you madjr :)

---

