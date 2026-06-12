---
title: "Program that logs changes I make in config files?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-20
Hey everyone,

Is there a program out there for ubuntu that will log any changes I make to config files?

When tweaking around with Ubuntu, we all sometimes end up making an undesirable change to a config file, then we forget which file we changed (well, I do, anyway!)

If there's a program out there for this, it would reduce the need to reinstall the entire OS if I end up making a bad change to the wrong file. 

Thanks!

---

### Post by badger_fruit on 2009-10-20
I **ALWAYS** make a .BACKUP copy of ANY config file I change
cp foobar.config foobar.config.backup

Then, if anything goes bang, restore the .backup
rm foobar.config
cp foobar.config.backup foobar.config

I don't think there's an app that manages things like that though; after all, there's so many of the damned things and they're all over the file-system it would be a nightmare to track.  Plus, if you trash your PC, how are you going to run the app to see what it was you changed and when, that trashed it?

;)

---

### Post by asuastrophysics on 2009-10-20
well, if the app stored the recent changes to config files in a log file, you could access the log file from the shell in recovery console. 

the log file would be stored in the /home/user/ folder and it would say something like this:

10-20-2009 3:00PM: Change in file /etc/init.d/rc
Line 43 Characters 13-26
Before change: "start gdm=1"
After change: "start gdm=0"

^ eh, something like that! :P 
That way, you could just sudo nano /etc/init.d/rc from the shell and correct the bad change. 

Of course, I'm probably just dreaming. :rolleyes:
maybe such program doesnt exist for novice unix users like me. 

couldn't help but wonder though.

---

### Post by cmcanulty on 2009-10-20
I think Ubuntu really needs a system restore like program. Last week I made a minor change and caused a big mess.

---

### Post by asuastrophysics on 2009-10-20
I'm not trying to say to everyone out there not to backup your config files. You **can** and you **should**! 8)

My point is, sometimes when more than one config file is changed, I'll forget where each config file is located. So even though I did make a backup of each config file changed, I don't remember the names of all of them or where each one is on the file system. 

Sorry, just thought I'd clarify. :) Sometimes making backups isn't enough for people like me.

---

### Post by falconindy on 2009-10-20
Gedit will always save a backup as filename~. Wanna revert your changes? `mv filename~ filename`. I'm sure plenty of other text editors have similar features.

To parrot the above: backups, backups, and more backups.

> **asuastrophysics said:**
> My point is, sometimes when more than one change is made, I'll forget where each config file is located.
Remember the name of the file? Use 'locate' to find it. Don't remember the name exactly? Your text editor likely has a history.

Hmmmm, I suppose a versioning system like git could be used here. Create a local only repository somewhere in your home directory, let's say its $HOME/git/sysfiles. Then make a script like so:
```
#!/bin/bash
GITREPO=$HOME/git/sysfiles
gedit $1 #or whatever other editor you want
#make your changes, save the file... when the exit your editor, the next lines execute...
cp $1 $GITREPO
git add $1
git commit -a -m "Changes to $1"
```
Call the script something like sysedit.sh and use it to edit a file that you're interested in tracking. It would need some more fleshing out (error checking and whatnot), which I could probably do if there's interest...

With this, you can use 'git log' to see changes that have been made with a date and timestamp, and you'll be able to roll back to each commit if you need to grab an old config.

---

### Post by asuastrophysics on 2009-10-20
> **falconindy said:**
> Gedit will always save a backup as filename~. Wanna revert your changes? `mv filename~ filename`. I'm sure plenty of other text editors have similar features.

To parrot the above: backups, backups, and more backups.


Remember the name of the file? Use 'locate' to find it. Don't remember the name exactly? Your text editor likely has a history.

That is a very good point, I didn't think to look in the recent documents section. :popcorn:

---

### Post by issih on 2009-10-20
I think this is an excellent thought..

Whilst it is true that various editors provide automated backups of the last change made, that really is not enough when messing with config files, a properly audited change log is a much better idea. More importantly the onus should be on the OS to protect its configuration rather than individual editing applications. Secondarily having an OS that automatically protects the user against common errors (like not backing up config files) is progress, because even the most advanced user will eventually hack something in an ill-advised rush and bork it, I know I have.

It really shouldn't be too hard to create a little monitoring system that would do this, in fact I may look into it. Doing it properly in a scalable and efficient manner may be a lot harder, but to my mind it is a really really good idea, especially if reverting changes is made simple and foolproof.

For example if the sources file is bust you can just offer to revert the last change until it works again.

---

### Post by asuastrophysics on 2009-10-20
Haha, if we end up implementing this, developing time for the upcoming releases of Ubuntu could be shortened, as developers could just rollback changes if the ones they made didn't work as well. 

Playing around with the OS could become a whole lot friendlier.

---

### Post by issih on 2009-10-20
I don't know about that...source code management is a smidge more involved especially in a multi developer environment, and there are several (very complex) applications that do that job already.

This would be a quite basic little tool, with admittedly similar goals.

I'm thinking of throwing something crude together using fsniper, diff and patch, but I really should be doing other things, so it may well not get done for a while.

In better circumstances a simple cli app should only take a few days to throw together, although honing it into something actually useful would obviously take a fair bit longer.

I'm considering storing the current version of a file and successive patch files which can be applied sequentially to revert back to previous versions. Doing it this way, more recent changes will be faster to access than old ones, which seems better.

Initially I'll probably just store the files in a directory, but really they ought to be in a database or at least a compressed archive. For a first pass though the config files and diff files (being plain text) are probably small enough to just store as they are.

One advantage of a simple directory structure is that "find" could be used along with the modification time to form a rudimentary system restore feature very easily.

I'm in fact envisioning that a lot of this could just be shell scripts.

anyway as I say, won't happen for some time, but its definitely achievable.

---

### Post by asuastrophysics on 2009-10-20
This forum now has an idea at Ubuntu Ideas URL:

[http://brainstorm.ubuntu.com/contributor/asuastrophysics/ideas/](http://brainstorm.ubuntu.com/contributor/asuastrophysics/ideas/)

issih, I used a couple of your thoughts in writing out my idea, so some of the credit goes to you ;-)

If this simple shell script gets developed properly, I think every Ubuntu user out there should benefit from it. This would help make Ubuntu unique among other distros. (what other flavor of linux do you know that can rollback changes to system .conf files?)

Anyway, I'll try to help out any way I can, but I only know basic shell script. 

Thanks! :)

---

### Post by HermanAB on 2009-10-21
I use RCS.  It is the simplest solution by far:
[http://aeronetworks.ca/rcs-howto.html](http://aeronetworks.ca/rcs-howto.html)

---

