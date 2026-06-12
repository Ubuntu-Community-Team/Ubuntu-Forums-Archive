---
title: "Remastersys: Create LiveCd inc docs and settings, without log in password"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by CharlotteThe57th on 2010-05-17
Does anyone know how to create a LiveCd for friends, using remastersys, that can retain my documents and settings and not require the LiveCd user to enter my password to use. 

I have tried the remastersys backup option to create a LiveCd to give to friends, but this requires the entering of my user password to run. 

I want to make a LiveCd, from a fresh Ubuntu install, that wthe newly installed Fire Fox extensions,  apps and Desktop items, as my friends don't have the ability to do these things every time they runa LiveCd that does not have these new Fire Fox extensions,  apps and Desktop items

Any ideas or suggestions welcome.

I think many people would like to do this sort of LiveCd creation.

---

### Post by Phrea on 2010-05-17
Why would you want to have your own documents on that live cd?
I think the Dist option will keep all the settings and programs, but will not include your personal information, passwords and files.

---

### Post by CharlotteThe57th on 2010-05-17
> **Phrea said:**
> Why would you want to have your own documents on that live cd?
I think the Dist option will keep all the settings and programs, but will not include your personal information, passwords and files.

I wish to have **my** documents on the Desktop, in exactly the same way that happens when a LiveCd is being used, as the Desktop always displays a folder with documents called "Examples". See attached screen shot folder.png

When remastersys is used to create a Dist just for friends it removes, by default, all of my new settings and documents, which means all the newly installed Fire Fox add ons and Desktop items simply vanish from the custom Dist LiveCd.

If I do a fresh install of Ubuntu, then just add new Folders with content and Documents to the Desktop and install Fire Fox add-ons, when I create a Dist via remastersys, all of these Desktop items and Fire Fox add-on vanish and it is these very extras that I want to give friends access to from a LiveCd Dist.

---

### Post by Phrea on 2010-05-17
Ok.
I have never tried it, but I think you need to setup Ubuntu so that it doesn't need a password, at all.
I'm not sure how to do that, but there's gotta be information out there to do just that.

---

### Post by CharlotteThe57th on 2010-05-18
> **Phrea said:**
> Why would you want to have your own documents on that live cd?
I think the Dist option will keep all the settings and programs, but will not include your personal information, passwords and files.

For my own use I have had to resort to using a LiveUSB and when using windows placing the folders and files in the root (cdrom) section of the usb stick. This also allows me to use the stick on windows and via root access to access the files I have been using on windows, which are considered as being within the read only section of the root cdrom folder. 

A frustrating compromise, till I can work out a more appropriate way of doing things.

---

### Post by Sublime Porte on 2010-05-18
[quote=Charlotte]I want to make a LiveCd, from a fresh Ubuntu install, that wthe newly  installed Fire Fox extensions,  apps and Desktop items, as my friends  don't have the ability to do these things every time they runa LiveCd  that does not have these new Fire Fox extensions,  apps and Desktop  items[/quote]

You need to do something like put the stuff you want to appear in the default user account into the /etc/skel directory. Not sure if that's the proper way to be doing it in gnome, there's probably a place in /usr/share/gnome or something, but basically you just need to find out where the default user profile gets setup from, and put your customisations in there, so the users get them when they load your custom livecd.

You want to be doing the dist option, not the backup option.

---

### Post by CharlotteThe57th on 2010-05-19
> **Sublime Porte said:**
> You need to do something like put the stuff you want to appear in the default user account into the /etc/skel directory. Not sure if that's the proper way to be doing it in gnome, there's probably a place in /usr/share/gnome or something, but basically you just need to find out where the default user profile gets setup from, and put your customisations in there, so the users get them when they load your custom livecd.

You want to be doing the dist option, not the backup option.

 Thanks, I have been giving this and others /etc/skel suggestions a go, not much luck thus far. But this url [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) seems to give a brief screen shot guide to doing similar things, so hopefully I can now work things out. Though the screen shots that cover transferring username folders to skel are a bit vague (copies attached: see below) If I want to keep all my Fire Fox settings, do I just place my Mozilla folder in skel and nothings else? I am unsure how just copying a folder into skel will ensure that all my Fire Fox settings will be transferred into a custom LiveCd/USB Dist.:confused:

---

### Post by robert shearer on 2010-05-19
This may be too easy but.... why not just make the remaster _with your password_ and then change **your password** on your own  install. ??

Or create an install on another partition using a generic password, modify it as you want it, remaster it and then delete that install.

---

### Post by CharlotteThe57th on 2010-05-19
> **robert shearer said:**
> This may be too easy but.... why not just make the remaster _with your password_ and then change **your password** on your own  install. ??

Or create an install on another partition using a generic password, modify it as you want it, remaster it and then delete that install.

I thought I could create the LiveCd/USB so it had a username:

 log on password = password or

password is password

a bit of a cheat. I would like to create a LiveCd/USB with my settings and docs that does not need a password, so I can give a copy of the iso to friends and they would be free to give a copy to anyone else, having to use a password to log on to a LiveCd/USB seems to defeat a general principle of creating a Dist.

---

### Post by robert shearer on 2010-05-19
> **CharlotteThe57th said:**
>  having to use a password to log on to a LiveCd/USB seems to defeat a general principle of creating a Dist.

Training should start early and often. :)

Good habits (esp. security) will improve their Linux experience.

---

### Post by CharlotteThe57th on 2010-05-20
I have managed to create live cd/usb that retains all the settings and   desktop items, my placing things in the skel folder. 

My earlier errors seem to stem from not accessing my username folder   under root as well as with root access to the skel folder.

Thanks to all who helped me learn this solution to what I hope will be a   powerful tool in sharing my custom iso's with others.

The guide on [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) was   particularly helpful and all those who gave tips on this forum:

[http://ubuntuforums.org/showthread.php?t=1487500](http://ubuntuforums.org/showthread.php?t=1487500)
[http://ubuntuforums.org/showthread.php?t=1479155](http://ubuntuforums.org/showthread.php?t=1479155)

Of course one has to thank the developer of Remastersys for creating   something that newbies like me can work with.

---

