---
title: "update manager is lacking"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by degarb on 2010-02-27
there are several annoying and lacking behaviours of the update manager.

I have it set to check once a week, but it checks on every day reboot.

Then, I do not want a certain ff update,  I uncheck it, but each day it is rechecked.  The 15 updates I don't want must all be unchecked.  each day.

Then, I see update of 66 meg for open office.  I assume this will just replace old files so not much space loss.  But the updater never tells us if the update will save or cost disk space, and how much.   

the nag factor made me say the heck with it, just install the update, regardless of my shrinking disk space, and no easy way to install new and experimental aps on second drive in linux.

---

### Post by HermanAB on 2010-02-27
Hmm, doing auto-updates is the primary way to get your system screwed up...

You should only do updates when there is a serious need for it.  Look at it this way: If the system is working properly, then an update will either leave it the same, or worse - it cannot make it better...

---

### Post by DrMelon on 2010-02-27
> **HermanAB said:**
> Hmm, doing auto-updates is the primary way to get your system screwed up...

You should only do updates when there is a serious need for it.  Look at it this way: If the system is working properly, then an update will either leave it the same, or worse - it cannot make it better...

Disregard his post! Quite often, important security updates and bugfixes are in the updates.

---

### Post by mechro on 2010-02-27
In Synaptic Package Manager find any package you don't want updating and from Menu do **Package > Lock Version**.

---

### Post by gmargo on 2010-02-27
In general you should not be afraid of downloading updates.  They are almost exclusively minor bug fixes that will not significantly change the amount of consumed disk space. You complain about the lack of detailed information, but then you are using the dumbed-down interface.  If you want more info, go to the command line.

Here's the commands I use with short explanations.  I use more steps than many would because I like the control.  See the aptitude(1) man page for more info.

aptitude clean[INDENT]Remove all the downloaded package (.deb) files.  You don't need them after they've been installed. This may be the solution to your disk space compliant.
[/INDENT]aptitude update[INDENT]Update the package lists.
[/INDENT]aptitude -d -y -V -R full-upgrade[INDENT]Download all packages needing updates (-d: download only, -y: don't give prompt before downloading, -V: show version info, -R: don't install Recommended packages).  This step will tell you how much disk space consumption will change.
[/INDENT]aptitude -V -R full-upgrade[INDENT]Install all packages needing updates.  Downloads as needed if not already downloaded.
[/INDENT]

---

### Post by degarb on 2010-02-27
> **gmargo said:**
> In general you should not be afraid of downloading updates.  They are almost exclusively minor bug fixes that will not significantly change the amount of consumed disk space. You complain about the lack of detailed information, but then you are using the dumbed-down interface.  If you want more info, go to the command line.

Here's the commands I use with short explanations.  I use more steps than many would because I like the control.  See the aptitude(1) man page for more info.

aptitude clean[INDENT]Remove all the downloaded package (.deb) files.  You don't need them after they've been installed. This may be the solution to your disk space compliant.
[/INDENT]aptitude update[INDENT]Update the package lists.
[/INDENT]aptitude -d -y -V -R full-upgrade[INDENT]Download all packages needing updates (-d: download only, -y: don't give prompt before downloading, -V: show version info, -R: don't install Recommended packages).  This step will tell you how much disk space consumption will change.
[/INDENT]aptitude -V -R full-upgrade[INDENT]Install all packages needing updates.  Downloads as needed if not already downloaded.
[/INDENT]

I like the post on how to lock versions.

sudo aptitude clean  is this different than sudo apt-get clean?

And, do I just make a script file with lines 

sudo aptitude update
sudo aptitude -d -y -V -R full-upgrade
sudo aptitude clean

or do I need to add anything.

---

### Post by tom.swartz07 on 2010-02-27
> **HermanAB said:**
> Hmm, doing auto-updates is the primary way to get your system screwed up...

You should only do updates when there is a serious need for it.  Look at it this way: If the system is working properly, then an update will either leave it the same, or worse - it cannot make it better...
not to be a trifle, but ABSOLUTELY NOT! The exact reason that updates are pushed to users are to fix problems that have occurred with programs. Giving advice such as this is not only unwarranted, but it is on the same level as telling them to use the command line rm -rf function to completely erase their hard drive.

> **gmargo said:**
> In general you should not be afraid of downloading updates.  They are almost exclusively minor bug fixes that will not significantly change the amount of consumed disk space. You complain about the lack of detailed information, but then you are using the dumbed-down interface.  If you want more info, go to the command line.


I agree completely. 

Also, to the OP- you had mentioned that you dont want Firefox updates pushed to you; perhaps you have inadvertently enabled a newer repo for Firefox builds (sometimes to update from 2.5 to 3.0 for example) and it is simply this repo that is giving you the new packages. You could turn it off in the Software Sources tab- System>Admin>Software Sources, then additional software tab.

---

