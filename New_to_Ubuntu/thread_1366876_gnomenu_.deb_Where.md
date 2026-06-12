---
title: "gnomenu .deb?? Where?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-12-28
Hi All, Okay, so I am hunting all over, and need some help getting and installing Gnomenu. I have seen a bunch of posts saying here you are, heres a link, but you go to them, and no .deb. it is all tars. And the links are all for the old 1.6, they are on what, 2.2.2 now.
I am using Lucid on a computer testing, and trying to learn more then just basics. This would be something i have been shying away from, so please, keep it simple.
Thanks

---

### Post by mapes12 on 2009-12-29
I'm not sure if this is what you're looking for but here it is anyway: [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by AndyP79 on 2009-12-29
> **mapes12 said:**
> I'm not sure if this is what you're looking for but here it is anyway: [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

Nope, this was some article on reseting a fubared desktop. On a side note, the commands are sneakily suspicious at being malicious. Anyone who reads this thread, BE CAREFUL if you run that command, I wouldn't run it just in case. Be sure you have nothing you would cry about if you lost it not backed up.

---

### Post by jimbauwens on 2009-12-29
To install GnoMenu in Ubuntu 9.10 or higher:
 ```
sudo add-apt-repository ppa:gnomenu-team
sudo apt-get update
sudo apt-get install gnomenu
```

Jim

---

### Post by AndyP79 on 2009-12-29
> **jimbauwens said:**
> To install GnoMenu in Ubuntu 9.10 or higher:
 ```
sudo add-apt-repository ppa:gnomenu-team
sudo apt-get update
sudo apt-get install gnomenu
```

Jim

Just tried this also, no luck. it tells me that the package does not exist. I got somehting similar to this when trying to add globalmenu also. So far, anything I have tried to add to Lucid has either broken the system or just plan won't load. So far it is nice and smooth, and adding updates is no problem. But I can't seem to get anything working:confused:
I am looking forward to getting the gnomenu, globalmenu and the RGBA transparency, along with the new AWN working in here, as I have it looking like a modern and attractive, slightly familiar interface. Oh well.... let's keep trucking

---

### Post by -kg- on 2009-12-29
[LIST]
[/LIST]

The process to add the repositories so you can install the program may be just a tad more complex than jimbauwens posted.

The page with the instructions (and, ostensibly, the repositories) is at [https://launchpad.net/~gnomenu-team/+archive/ppa]("https://launchpad.net/~gnomenu-team/+archive/ppa").  Try the instructions for installing the repositories from there and (hopefully) it should work.  Be sure to click on "(Read about installing)" down the page, then scroll up the page.  This will give you precise instructions on how to properly add the repositories and get the software.

---

### Post by 3rdalbum on 2009-12-29
> **AndyP79 said:**
> Nope, this was some article on reseting a fubared desktop. On a side note, the commands are sneakily suspicious at being malicious. Anyone who reads this thread, BE CAREFUL if you run that command, I wouldn't run it just in case. Be sure you have nothing you would cry about if you lost it not backed up.

It removes the per-user settings for Gnome and Gnome applications, nothing more. It's not malicious unless you are told to do it under the guise of it doing something different.

Original poster: You say you want to learn something more than the basics - so why not compile Gnomenu from source? This will teach you much more than just double-clicking on a Debian package.

---

### Post by mechro on 2009-12-29
There's .deb's here...

[https://launchpad.net/~gnomenu-team/+archive/ppa/+packages](https://launchpad.net/~gnomenu-team/+archive/ppa/+packages)

---

### Post by AndyP79 on 2009-12-29
> **3rdalbum said:**
> It removes the per-user settings for Gnome and Gnome applications, nothing more. It's not malicious unless you are told to do it under the guise of it doing something different.

Original poster: You say you want to learn something more than the basics - so why not compile Gnomenu from source? This will teach you much more than just double-clicking on a Debian package.

Hi, I did not mean to come off as saying that you were posting something bad. I just recognized the rm rf stuff and had always been told to stear clear. 
So Far as learning to compile from source, I don't even know what that actually means. And I am seeing that no mater what ppa's I put in, they aren't working in lucid?? I am actually starting a cheat sheet though with my testing adventure, so when I do figure something out and get it to work, I have a note of it so when I f*%@ it up, I can go back and put everything back.

---

### Post by AndyP79 on 2009-12-29
> **mechro said:**
> There's .deb's here...

[https://launchpad.net/~gnomenu-team/+archive/ppa/+packages](https://launchpad.net/~gnomenu-team/+archive/ppa/+packages)

this worked, click save install. 

just to add, as easy as this was, i have tried adding stuff from ppa's, and have just not been having any luck with them. thanks again

---

### Post by jimbauwens on 2009-12-30
> **AndyP79 said:**
> Just tried this also, no luck. it tells me that the package does not exist. I got somehting similar to this when trying to add globalmenu also. So far, anything I have tried to add to Lucid has either broken the system or just plan won't load. So far it is nice and smooth, and adding updates is no problem. But I can't seem to get anything working:confused:
I am looking forward to getting the gnomenu, globalmenu and the RGBA transparency, along with the new AWN working in here, as I have it looking like a modern and attractive, slightly familiar interface. Oh well.... let's keep trucking

Weird, I used this yesterday to install it on my Karmic computer.
Probably something is broken in your alpha build of Lucid.
Well, anyway you've got GnoMenu now on your computer.:)

Jim

---

### Post by rburkartjo on 2009-12-30
andy try this link i used it to install gnomenu it is a deb file. once you install right click your tool bar and add to panel and select gnomenu.

[http://www.getdeb.net/software/GnoMenu](http://www.getdeb.net/software/GnoMenu)

---

