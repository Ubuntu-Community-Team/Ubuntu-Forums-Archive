---
title: "Need help modifying launchers and changing file paths"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by ColemanK on 2010-05-16
Okay, here goes.

I want to be able to right click something in Ubuntu menu, and instead of just being able to add the launcher to the panel or desktop, be able to actually MODIFY the launcher. I'd also like to be able to modify the different categories. 

Plus, I really hate how the path for many folders is just .wine/blah blah blah. Where is this located? How can I get to it? Why is it that when I uninstall Wine, the folder is still there, plus all of the programs I'd previously installed? \


That's all for now. I'll probably find some other stuff that I'm not so fond of and post here later. When I run into more problems. 

Thanks, Coleman

---

### Post by uRock on 2010-05-16
> **ColemanK said:**
> Okay, here goes.

I want to be able to right click something in Ubuntu menu, and instead of just being able to add the launcher to the panel or desktop, be able to actually MODIFY the launcher. I'd also like to be able to modify the different categories. 

Plus, I really hate how the path for many folders is just .wine/blah blah blah. Where is this located? How can I get to it? Why is it that when I uninstall Wine, the folder is still there, plus all of the programs I'd previously installed? \


That's all for now. I'll probably find some other stuff that I'm not so fond of and post here later. When I run into more problems. 

Thanks, Coleman
[s]Testimonial or asking for help? The thread title implies a rant.[/s] Thanks aysiu. 

OP, Like others have pointed out you can right click on the menu launcher. Or you can go to System> Preferences> Main Menu to make changes to items in the menu.

To find hidden files, they are usually in the /home folder, so you just need to go to your home folder(the one at the top of the list in Places) and hit Ctrl+H and all of the hidden files will become visible.

---

### Post by drs305 on 2010-05-16
To modify the Ubuntu menu, try this in a terminal (Applications, Accessories, Terminal):
```
alacarte
```

I know you say you want to be able to right click to modify; if it doesn't do that, this is *is* a way to modify the menu if that is one of your objectives

---

### Post by 4Orbs on 2010-05-16
Hint: Complaining to Linux is like complaining to the government. Takes you nowhere. Just ask for help, politely.

---

### Post by daimaru on 2010-05-16
if you want to right click just right click your application menu, choose edit menu and then edit the properties of the desired launcher... its the same thing as typing alacarte in terminal just without the typing and with your beloved right click :)

---

### Post by anewguy on 2010-05-16
Here's one hint - try opening "Places", go to your default folder, click "View" and click the option to show hidden files and folders.  See .wine now??  Your "C" drive to wine is within that folder.

Here's another hint, and please understand it is meant to help you, not make you mad.  As you can see from the other posts on this thread, titling a thread with "A bunch of complaints" is normally going to get you hammered by users here.  The better approach would be "New Ubuntu user, have some things I need help with", or even better "New Ubuntu user, Wine question and a misc question".  You see, things like that are polite, to the point, and will get you a lot of willing help.  Believe me, we've all been beginners, and even with the experience I have (I'm no expert!), we all have gotten frustrated, sometimes beyond believe.  The trick is to set that frustration aside and use constructive, detail requests for HELP.

Dave ;)

---

### Post by bowens44 on 2010-05-16
Instead of saying , I don't like this and I don't like that, take the time to learn to use linux. If you need help with something, be nice , ask politely, people will help.

---

### Post by kevinatkins on 2010-05-16
Okay...

To modify your application launchers on the main menus, right-click on 'Applications' and select 'Edit Menus' - you can then customise as you wish. 

You mention a .wine folder. File / folder names preceded by a dot in Linux are normally hidden from view. If you'd prefer to see such files / folders from within the standard Ubuntu file manager (Nautilus), press Ctrl-H to toggle hidden items...

Linux is different from Windows. It's probably a bit alien, and thereby frustrating, but spend a little time, use Google, ask questions, and you'll be rewarded by a great operating system.

---

### Post by 4Orbs on 2010-05-16
Hope we didn't run him off. Maybe it was Bill Gates in disguise.

---

### Post by SlappyPappy on 2010-05-16
Hardly a bunch of complaints.

I'm a happy Ubuntu user and I can do better than that.

2 funny.

:guitar::guitar::guitar:

---

### Post by sandyd on 2010-05-16
> **ColemanK said:**
> Okay, here goes.

I want to be able to right click something in Ubuntu menu, and instead of just being able to add the launcher to the panel or desktop, be able to actually MODIFY the launcher. I'd also like to be able to modify the different categories. 
**see above posts**
Plus, I really hate how the path for many folders is just .wine/blah blah blah. Where is this located? How can I get to it? Why is it that when I uninstall Wine, the folder is still there, plus all of the programs I'd previously installed? \

[B]Go to your home folder.
Click on "view" and select "show hidden folders"

Now do you see the .wine folder?

alternatively, run this in the terminal.
This will create a folder called "wine" in your home folder, this is the squivilent of .wine
```

ln -s ~/.wine ~/wine
```[/B] 
That's all for now. I'll probably find some other stuff that I'm not so fond of and post here later. When I run into more problems. 

Thanks, Coleman

> **4Orbs said:**
> Hint: Complaining to Linux is like complaining to the government. Takes you nowhere. Just ask for help, politely.

> **uRock said:**
> Testimonial or asking for help? The thread title implies a rant.

> **anewguy said:**
> Here's one hint - try opening "Places", go to your default folder, click "View" and click the option to show hidden files and folders.  See .wine now??  Your "C" drive to wine is within that folder.

Here's another hint, and please understand it is meant to help you, not make you mad.  As you can see from the other posts on this thread, titling a thread with "A bunch of complaints" is normally going to get you hammered by users here.  The better approach would be "New Ubuntu user, have some things I need help with", or even better "New Ubuntu user, Wine question and a misc question".  You see, things like that are polite, to the point, and will get you a lot of willing help.  Believe me, we've all been beginners, and even with the experience I have (I'm no expert!), we all have gotten frustrated, sometimes beyond believe.  The trick is to set that frustration aside and use constructive, detail requests for HELP.

Dave ;)

> **bowens44 said:**
> Instead of saying , I don't like this and I don't like that, take the time to learn to use linux. If you need help with something, be nice , ask politely, people will help.

> **4Orbs said:**
> Hope we didn't run him off. Maybe it was Bill Gates in disguise.
offhand, i say we sent him running. :(

be nice to newbies guys.

---

### Post by 4Orbs on 2010-05-16
But Carlee, the guy was obviously twisted by years of Windo## propaganda. We were just trying to help him by first getting his feet back on solid ground. Jeez.... I feel so ashamed now.

---

### Post by QIII on 2010-05-16
A bit of advice from a crusty old Army Officer.  And my apologies to the moderators for my suggestive acronym.

It's easy to make fun of the FNG.

Hard as h*ll to train him properly.

You can probably guess which course of action I respect.  One is weak.  The other tough.

To get respect, you have to earn it.  You have to give it to get it.

Every new user we laugh out of the room is another person to spread the stereotype that we are a bunch of snobby techno-geeks.

Good job, guys.

---

### Post by anewguy on 2010-05-16
And I didn't even know from the title it was going to be complaints about Ubuntu.  I thought they were a new Ubuntu user and had complaints like "the water is dripping in my kitchen faucet" - you know, things like that. ;) ;)

I also thought that some of us treated this user with respect, or at least the respect they had earned.

Dave ;)

---

### Post by aysiu on 2010-05-16
> **uRock said:**
> Testimonial or asking for help? The thread title implies a rant. I'm giving the benefit of the doubt, so I changed the thread title.

---

### Post by 4Orbs on 2010-05-16
> Plus, I really hate how the path for many folders is just .wine/blah blah blah. Where is this located? How can I get to it? Why is it that when I uninstall Wine, the folder is still there, plus all of the programs I'd previously installed?

When you install Wine, the first thing you gotta do is configure it by opening the Configure Wine link in the menu. Then assign your preferred audio and click apply and save. This automatically creates the .wine hidden folder in your personal home folder.

If you uninstall Wine and want to remove the folder from your home folder, just open the Nautilus file browser, and in the View menu at the top of Nautilus, select "Show Hidden Files". Then you can scroll down and delete the .wine folder. Next time you log out or reboot, all the Wine entries should have disappeared from your apps menu.

To avoid wasting time by trying to install something in Wine that won't work, first visit the [Wine HQ Database]("http://appdb.winehq.org/") to see if that program is listed as working or non-working in Wine. And to uninstall any programs you've installed in Wine, use the specific Wine uninstall programs utility.

---

