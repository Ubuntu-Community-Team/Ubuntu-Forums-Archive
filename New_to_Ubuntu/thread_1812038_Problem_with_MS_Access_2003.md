---
title: "Problem with MS Access 2003"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by JacquesPotter on 2011-07-25
Ahaa I finally figured out how to post a new thread. Yippee for me!!!!

Ok, now seriously. I have recently reinstalled Ubuntu to give it another try and I have been having some serious problems trying to work with MS Office 2003. I have been able to load in onto the computer but, Ill stick with Access on this thread. When I go to open my existing database from when I was working in the MS XP OS, or try to save a new db while in Ubuntu, I get an error that states "Microsoft Office Access has encountered a problem and needs to close. We are sorry for the inconvenience." I have added all the service packs up to service pack 3. What else can I do. I need these db's for work and I only have a couple of days before I MUST have access to them again.

---

### Post by IHeequ5i on 2011-07-25
My first suggestion is to head over to WineHQ and see what they've run into as far as gotchas and workarounds.  I'm guessing that you're going to need winetricks and some special config to get Access to play nice on Ubuntu.

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

How did you do the install? Did you get any errors?

Best of luck!

---

### Post by JacquesPotter on 2011-07-25
Thanks, Ill give that a try.

---

### Post by IHeequ5i on 2011-07-25
Apologies - should've checked this before making my first post:

Assuming you have installation media for Office 2K3... download PlayOnLinux (from [www.playonlinux.com](www.playonlinux.com)) and use their script to reinstall Office. Of course, you should uninstall everything you've already got first.

I don't guarantee that PoL will work, but I've had decent luck with them on a variety of applications.

---

### Post by oldfred on 2011-07-25
Someone posted this, I have not tried it. But have just converted Access data using MDBtools.

Microsoft Access in Wine - some success
[http://ubuntuforums.org/showthread.php?t=1113065](http://ubuntuforums.org/showthread.php?t=1113065)

---

### Post by JacquesPotter on 2011-07-25
Oh and to answer how I did the install. I used my discs and ran the setup.exe with Wine. That was pretty easy and I didn't run into any problems. I since then tried Crossover, but that only seemed to give me a partial install so I went back and reinstalled it with Wine. Does this help?

---

### Post by Mark Phelps on 2011-07-25
If you use the link provided to search the WineHQ site for info on Access, you'll see that 2003 is rated Bronze -- the lower rating anything can get an still work.

Also, if you look at the testing results, you'll see that no one tested it with Ubuntu 11.04.

So, you're likely to be the first.

---

### Post by JacquesPotter on 2011-07-25
Thanks everyone. Ill give them all a try and let you know if any of them work. I won't be able to try anything for a few hours, so don't hold your breath too long... dont want anyone passing out and all...:)

---

### Post by Wim Sturkenboom on 2011-07-25
If everything fails, you can try (and buy) codeweavers' crossover office and run it in there.

PS it seems to be called 'crossover impersonator' nowadays

---

### Post by Gone fishing on 2011-07-26
I know you can run Access by using Crossover from Codeweavers. I've never had much luck simply using Wine, I guess that it must be possible after all Crossover is built on Wine however, Codeweavers must do a lot of tweaking.

Download and install the trial version of Crossover it will work

---

### Post by amjjawad on 2011-07-26
My personal opinion about that was, still and will always be that it's much better to run/install each program/application on its native environment.

Having that said, I will not bother to install something for Microsoft on Linux and vice versa but again, that's only me :)

---

### Post by JacquesPotter on 2011-08-15
OK, sorry everyone for my absence the last week. I've been busy with many other things that take up more of my time then I can deal with because I don't have my calendering/emailing system and my db. I think we've tried all the ways to get me working. So, even though we have not solved the problem I will mark this thread as solved and move onto the next set of problems in life. 

I do want to sincerely thank everyone for your help. It truly is appreciated!!! I've learned a lot about Ubuntu over the past few weeks that will help me through the times ahead. Thanks again!!

---

### Post by drdos2006 on 2011-08-15
Well, if you really need to use an Access database, install Virtualbox from Oracle, run your Windows version under virtualbox and install Access from your virtualised Windows program.

regards

---

