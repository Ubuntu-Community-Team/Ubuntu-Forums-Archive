---
title: "Reinstalling Lucid"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by jnmjr on 2010-05-14
Hey guys, I'm at the end of my rope, I've been trying to fix my sound for 2 days since I lost it, since nothing works I'm thinking of a clean reinstall of Lucid, my question, is it possible to install fresh in another partition and then copy my Home folder to the new install so I can keep my configuration files and I don't have to reconfigure the whole thing? THX

---

### Post by mike555 on 2010-05-14
Yes, but easier to copy contents of old home into new ...not the folder itself..

---

### Post by jnmjr on 2010-05-14
> **mike555 said:**
> Yes, but easier to copy contents of old home into new ...not the folder itself..

Can that be done during the install or would it be necessary to copy folders and files one at a time afterwards? THX

---

### Post by Zintha on 2010-05-14
> **jnmjr said:**
> Hey guys, I'm at the end of my rope, I've been trying to fix my sound for 2 days since I lost it, since nothing works I'm thinking of a clean reinstall of Lucid, my question, is it possible to install fresh in another partition and then copy my Home folder to the new install so I can keep my configuration files and I don't have to reconfigure the whole thing? THX
Your 19 hour old topic isn't exactly a 2 day effort. Its half a day with only 1-2 fixes posted so far.

If the end of your rope on a non-urgent issue is 19 hours after seeking help then you might run into issues later down the line.

That said, you tried clicking the Sound icon at the bottom and checking output. Also checked you've not put headphones in?

To answer your question I don't think a clean reinstall will solve your problem at all. This isn't windows. Unless you went from Beta to Release it won't solve anything more than likely.

---

### Post by jnmjr on 2010-05-14
> **Zintha said:**
> Your 19 hour old topic isn't exactly a 2 day effort. Its half a day with only 1-2 fixes posted so far.

If the end of your rope on a non-urgent issue is 19 hours after seeking help then you might run into issues later down the line.

That said, you tried clicking the Sound icon at the bottom and checking output. Also checked you've not put headphones in?

To answer your question I don't think a clean reinstall will solve your problem at all. This isn't windows. Unless you went from Beta to Release it won't solve anything more than likely.

Thank you for your opinion, I do realize this is not Windows, further you've got no clue how much research I've done in these 19 hours, how many different things I've tried, how many uninstalls reinstalls I've done, I've spent the better part of 2 working days trying to resolve this matter, if having no sound is non urgent to you Great!!! to me is absolutely urgent and necessary...Furthermore please refrain from posting...this thread is not about sound....if you don't have anything concrete to add to a possible solution, your patronizing attitude is not appreciated.

---

### Post by mike555 on 2010-05-14
after you install and startup , mount your old home folder , select all, copy, (don't close window) ,go to your new home and paste , it will ask about replacing things as it copies ...... easy (I just did it yesterday , because my hard drive failed )

---

### Post by jnmjr on 2010-05-14
> **mike555 said:**
> after you install and startup , mount your old home folder , select all, copy, (don't close window) ,go to your new home and paste , it will ask about replacing things as it copies ...... easy (I just did it yesterday , because my hard drive failed )

Thanks, that sure sounds easy enough, just another ? Did you run into anything in particular that you needed to reconfigure after you copied the files, or did all look like your old set-up after you rebooted?

---

### Post by 2hot6ft2 on 2010-05-14
I don't know about the other thread but if it has to do with no sound thru headphones perhaps a little more reading would be in order. If not before then after you re-install depending on what all you've changed.

It's a known bug.
[http://forumubuntusoftware.info/viewtopic.php?f=68&t=4589&start=30](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4589&start=30)
:guitar:

---

### Post by Tholley on 2010-05-14
Ok.. I don't mean to hijack this thread, but I think I know what you are trying to achieve, and would like to re-configure the question, since I would be interested in it too.

So like in my case to be specific, if I copy all the contents from my home folder, upgrade from 9.04 to 10.04, re-copy all the contents into the new home folder, then I would not have to re-do all my visual effects and appearances that I spent allot of time with Emerald Theme Manager, Compiz, etc.?

Is that kinda what you are getting at too?

---

### Post by mike555 on 2010-05-14
You would need to make sure you have all the themes and programs installed that you had before , otherwise the hidden settings in the home folder for them wouldn't do any good ........ I noticed that when I reinstalled , I had to reinstall themes , and a few other things ....


 good idea to export bookmarks and contacts and such and put on a thumbdrive ,just in case ...

---

### Post by 2hot6ft2 on 2010-05-14
> **Tholley said:**
> Ok.. I don't mean to hijack this thread, but I think I know what you are trying to achieve, and would like to re-configure the question, since I would be interested in it too.

So like in my case to be specific, if I copy all the contents from my home folder, upgrade from 9.04 to 10.04, re-copy all the contents into the new home folder, then I would not have to re-do all my visual effects and appearances that I spent allot of time with Emerald Theme Manager, Compiz, etc.?

Is that kinda what you are getting at too?
That would be backing up home and restoring it. I did it on 2 machines and 1 works perfectly while the other has browser plugin issues and I had to delete the firefox profile and create another.
I'll be re-installing in a few days when UE 2.7 is released anyway so I don't really care.
:popcorn:
It's all the hidden files and folders in home that have all your settings.

---

### Post by Tholley on 2010-05-14
> It's all the hidden files and folders in home that have all your  settings.

Cool! I'll be trying that out pretty soon then. Right now I am backing up both all my Jaunty files I wanted to keep as well as all my Windows that are on the other dual boot partition, just in case something goes wrong like I have read in some other peoples horror stories trying to upgrade to 10.04.

I know in Windows you have to select "show hidden files and folders" in order to copy them, is there something similar like that in Ubuntu, or will just "selecting all" catch all the hidden files too?

---

### Post by 2hot6ft2 on 2010-05-14
> **Tholley said:**
> Cool! I'll be trying that out pretty soon then. Right now I am backing up both all my Jaunty files I wanted to keep as well as all my Windows that are on the other dual boot partition, just in case something goes wrong like I have read in some other peoples horror stories trying to upgrade to 10.04.

I know in Windows you have to select "show hidden files and folders" in order to copy them, is there something similar like that in Ubuntu, or will just "selecting all" catch all the hidden files too?
Ctrl+h or View > Show Hidden Files
will show the hidden files and folders.
You're better off using an app. to backup and restore (because of permissions that wont allow a normal user to save some root owned files). I use QuickStart and have for years.
[http://www.quickstart.freeforums.org](http://www.quickstart.freeforums.org)

just save a copy of it to the usb and install it as the very first thing on a fresh install do not do anything else before restoring home.
:popcorn:

---

### Post by Tholley on 2010-05-14
> You would need to make sure you have all the themes and programs  installed that you had before , otherwise the hidden settings in the  home folder for them wouldn't do any good ........ I noticed that when I  reinstalled , I had to reinstall themes , and a few other things ....

> just save a copy of it to the usb and install it as the very first thing  on a fresh install do not do anything else before restoring home.


Like I said before, I didn't mean to hijack this thread, so I hope this is what jnmjr was getting at too.

anyway...  so I should re-copy home folder as the very first thing, and then install Emerald, Compiz, etc.? 

Oh... and **I** am planning on doing an upgrade, unlike jnmjr who is planning to to a fresh install. If the upgrade were to go thru without any hitches, will all my setting be there still anyway? I didn't have any success upgrading from 9.04 to 9.10, ended up doing a fresh install back then, so not sure about what gets saved in an upgrade.

Sorry again for the hijack... :)

---

### Post by 2hot6ft2 on 2010-05-14
> **Tholley said:**
> Like I said before, I didn't mean to hijack this thread, so I hope this is what jnmjr was getting at too.

anyway...  so I should re-copy home folder as the very first thing, and then install Emerald, Compiz, etc.? 

Oh... and **I** am planning on doing an upgrade, unlike jnmjr who is planning to to a fresh install. If the upgrade were to go thru without any hitches, will all my setting be there still anyway? I didn't have any success upgrading from 9.04 to 9.10, ended up doing a fresh install back then, so not sure about what gets saved in an upgrade.

Sorry again for the hijack... :)
There have been MANY changes in 10.04 some of the themes wont even work that used to work. 10.04 is a LTS and should be done as a fresh install then you can do upgrades until the next LTS which will most likely have more drastic changes. It just doesn't play well as far as backwards compatibility on a lot of things.

As far as compiz and emerald goes I use [UE]("http://forumubuntusoftware.info/index.php") so it comes with it. I don't have to install it. 2.6 is here and 2.7 will be in a few days. 2.6 is gnome only 2.7 will be gnome, kde, xfce and lxde all rolled into 1. I choose my desktop environment when I login.

Normally an upgrade should keep all your settings and stuff but things tend to break especially if you have apps. installed that were not installed thru the repos.
:mad:All my hard work getting things just how I wanted them.
Oh well.

---

### Post by Tholley on 2010-05-14
> **2hot6ft2 said:**
> There have been MANY changes in 10.04 some of the themes wont even work that used to work. 10.04 is a LTS and should be done as a fresh install then you can do upgrades until the next LTS which will most likely have more drastic changes. It just doesn't play well as far as backwards compatibility on a lot of things.

As far as compiz and emerald goes I use [UE]("http://forumubuntusoftware.info/index.php") so it comes with it. I don't have to install it. 2.6 is here and 2.7 will be in a few days. 2.6 is gnome only 2.7 will be gnome, kde, xfce and lxde all rolled into 1. I choose my desktop environment when I login.

Normally an upgrade should keep all your settings and stuff but things tend to break especially if you have apps. installed that were not installed thru the repos.
:mad:All my hard work getting things just how I wanted them.
Oh well.

Ok.. I can do a fresh install, and save my home folder setting like we discussed earlier.
Hopefully some stuff will still work the same.

don't know anything about UE... I clicked on your link an will check it out farther. Is it something that I can use to make the windows eye candy like in Emerald?

---

### Post by 2hot6ft2 on 2010-05-14
> **Tholley said:**
> Is it something that I can use to make the windows eye candy like in Emerald?
It's an operating system that uses ubuntu as it's base but adds many things ubuntu doesn't offer, has it's own repos. and has been tweaked, so it doesn't qualify to be called a remix.
:guitar:

---

