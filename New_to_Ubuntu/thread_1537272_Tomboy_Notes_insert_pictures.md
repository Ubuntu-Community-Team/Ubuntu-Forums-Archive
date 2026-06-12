---
title: "Tomboy Notes insert pictures?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by justincase_2008 on 2010-07-23
I saw this for tomboy [http://gitorious.org/tomboy-image](http://gitorious.org/tomboy-image) It is suppose to add the ability to add images to tomboy. I was hoping it would add the image itself not a link to the file. Has anyone been about to do this? I dropped the files in the config/tomboy//addins like it said but tomboy doesnt see the new add-ins. Im running 10.04 with Tomboy 1.2.1. Im trying to do this for my Girlfriends netbook so i can get vista off of it. Trying to find a replacement for Windows One Note that will work for her.

---

### Post by LowSky on 2010-07-23
have you tried BasKet Note Pads?
[IMG]http://basket.kde.org/screenshots/basket-note-pads.png[/IMG]

---

### Post by justincase_2008 on 2010-07-23
Will install and give it a try thanks.

---

### Post by sharm on 2010-07-23
> **justincase_2008 said:**
> I saw this for tomboy [http://gitorious.org/tomboy-image](http://gitorious.org/tomboy-image) It is suppose to add the ability to add images to tomboy. I was hoping it would add the image itself not a link to the file. Has anyone been about to do this? I dropped the files in the config/tomboy//addins like it said but tomboy doesnt see the new add-ins. Im running 10.04 with Tomboy 1.2.1. Im trying to do this for my Girlfriends netbook so i can get vista off of it. Trying to find a replacement for Windows One Note that will work for her.

Did you compile the tomboy-image add-in?  The only file you should need to drop in ~/.config/tomboy/addins is the .dll file produced when you build tomboy-image.  Just open TomboyImage.sln in MonoDevelop and build it (if you have a new enough version of Mono you can also build from the command line by running `xbuild TomboyImage.sln`).

This add-in does work, but it doesn't support note sync if you were using that.

---

### Post by A_M_S on 2010-07-23
A good substitute of tomboy is keepnote

[http://rasm.ods.org/keepnote/](http://rasm.ods.org/keepnote/)

---

### Post by justincase_2008 on 2010-07-26
I tried BasKet and it works great only thing is spell check...

---

### Post by hottarod on 2011-03-12
Most current location for the DLL is /usr/lib/tomboy/addins.  That is where all the other DLL's are stored.  It does not work there either.  Tomboy does not find the DLL or it can't activate it.  I have notes with embedded images that I can no longer access and they are kind of important to me.

---

### Post by grekpg on 2012-11-24
anyone have tomboy-image file - InsertImage.dll 
limk is broken, please put somwere or send to my in anyone have it...

---

### Post by overdrank on 2012-11-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

