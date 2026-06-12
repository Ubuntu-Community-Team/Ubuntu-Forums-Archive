---
title: "I have a bunch of problems!"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by hmich176 on 2009-07-09
I had a problem with Ubuntu this morning.  I tried to open Firefox and it completely froze the system.  I had to manually reboot, and when I did, it took a rather long time just to get through the Ubuntu loading splash screen.  

Once I got to my standard desktop, whenever I try to open Firefox, it says it's opening but never does.  I tried uninstalling and reinstalling Firefox, but that didn't help anything.  

I tried to do a system update, but it couldn't complete the update.  

So, I'm not sure what to do from here.  I'm using an older version of Opera (which is an okay browser, I guess) since Firefox won't work.  The system also runs very sluggish.

---

### Post by tarps87 on 2009-07-09
Have you tried purging the install?
```
sudo apt-get purge firefox
```

What are the error messages when the update fails?

---

### Post by hmich176 on 2009-07-09
This is what happened when I tried to purge the install:
```
harry@harry-laptop:~$ sudo apt-get purge firefox
[sudo] password for harry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-9-generic libstrigiqtdbusclient0 python-twisted-names
  xfce4-mcs-plugins libarts1c2a libmono-posix1.0-cil libartsc0
  libmono-security1.0-cil libxfce4mcs-client3 liblzo1 python-psyco kanagram
  libksane0 amarok-engine-xine libparted1.8-9 nvidia-177-modaliases
  libmono-sharpzip0.84-cil ttf-sil-gentium linux-headers-2.6.27-9
  libmagick++10 sqlite linux-headers-2.6.28-11 libwxgtk2.6-0
  libmono-system-web1.0-cil python-twisted-runner libmagick10 libkipi-common
  libmono-data1.0-cil libdns43 libx11-xcb1 libsuitesparse-3.1.0
  python2.4-minimal libboost-date-time1.34.1 librasqal0 python2.4 libglide2
  libgnome-desktop-2-7 libx264-59 python-twisted-mail aumix
  linux-headers-2.6.28-11-generic xfce4-icon-theme libpulsecore5
  libwxbase2.6-0 python-pyme classpath-gtkpeer libmono-getoptions1.0-cil
  python-twisted-lore libpoppler3 libmono1.0-cil python-twisted-news
  python-twisted-words libmjpegtools0c2a libmono-data-tds1.0-cil
  python-twisted libtunepimp5 libifp4 libmono-system-data1.0-cil galeon-common
  libdvdread3 python-wxversion kdebase-workspace-data classpath-common
  gtk2-engines-xfce cacao xfce4-mcs-manager python-wxgtk2.6
  libxfce4mcs-manager3 classpath libisc44 sqlite3 libimlib2 libnova-0.12-2
  libnjb5 libggzdmod6 libpoppler-glib3 libntfs-3g28
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 315669 files and directories currently installed.)
Removing firefox ...
Purging configuration files for firefox ...
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tarps87 on 2009-07-09
It is possible that on of the packages has been corrupted, try
```
sudo dpkg --configure -a
```

If your computer freezes again try holding alt + print screen press R E I S U B with a short pause between each one

---

### Post by hmich176 on 2009-07-09
When I tried that, I got this: 
```
harry@harry-laptop:~$ sudo dpgk --configure -a
[sudo] password for harry: 
sudo: dpgk: command not found
harry@harry-laptop:~$ sudo dpgk --configure -a

```

---

### Post by tarps87 on 2009-07-09
Sorry typo dpkg, amend previous post

---

### Post by hmich176 on 2009-07-09
Okay.  I tried that and got this:
```
harry@harry-laptop:~$ sudo dpkg --configure -a
[sudo] password for harry: 
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-13-generic

```

---

### Post by tarps87 on 2009-07-09
It seems like that package is really broken, try
```
sudo apt-get autoclean
sudo apt-get install -f
```

And can you also post the output of
```
uname -a
```
we may need to remove the package

---

### Post by hmich176 on 2009-07-09
Here's the uname - a result:
```
harry@harry-laptop:~$ uname -a
Linux harry-laptop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

---

### Post by hmich176 on 2009-07-09
Then I ran the autoclean and isntall -f and here's the result: 
```
harry@harry-laptop:~$ sudo apt-get autoclean
[sudo] password for harry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del cupsys-client 1.3.9-17ubuntu3.1 [60.2kB]
Del libhal1 0.5.12~rc1+git20090403-0ubuntu3 [93.5kB]
Del linux-image-2.6.28-13-generic 2.6.28-13.44 [24.6MB]
Del cupsys 1.3.9-17ubuntu3.1 [60.2kB]
Del cups-common 1.3.9-17ubuntu3.1 [1165kB]
Del cups 1.3.9-17ubuntu3.1 [2135kB]
Del linux-headers-2.6.28-13-generic 2.6.28-13.44 [668kB]
Del linux-libc-dev 2.6.28-13.44 [760kB]
Del libcupsys2 1.3.9-17ubuntu3.1 [60.2kB]
Del libhal-storage1 0.5.12~rc1+git20090403-0ubuntu3 [22.7kB]
Del hal 0.5.12~rc1+git20090403-0ubuntu3 [395kB]
Del cups-client 1.3.9-17ubuntu3.1 [115kB]
Del libcupsimage2 1.3.9-17ubuntu3.1 [51.5kB]
Del pidgin-data 1:2.5.5-1ubuntu8.1 [1151kB]
Del cupsys-bsd 1.3.9-17ubuntu3.1 [60.2kB]
Del cups-bsd 1.3.9-17ubuntu3.1 [36.2kB]
Del libpurple0 1:2.5.5-1ubuntu8.1 [1587kB]
Del linux-headers-2.6.28-13 2.6.28-13.44 [8693kB]
Del pidgin 1:2.5.5-1ubuntu8.1 [519kB]
Del libcups2 1.3.9-17ubuntu3.1 [174kB]
Del cupsys-common 1.3.9-17ubuntu3.1 [4520B]
harry@harry-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-9-generic libstrigiqtdbusclient0 python-twisted-names
  xfce4-mcs-plugins libarts1c2a libmono-posix1.0-cil libartsc0
  libmono-security1.0-cil libxfce4mcs-client3 liblzo1 python-psyco kanagram
  libksane0 amarok-engine-xine libparted1.8-9 nvidia-177-modaliases
  libmono-sharpzip0.84-cil ttf-sil-gentium linux-headers-2.6.27-9
  libmagick++10 sqlite linux-headers-2.6.28-11 libwxgtk2.6-0
  libmono-system-web1.0-cil python-twisted-runner libmagick10 libkipi-common
  libmono-data1.0-cil libdns43 libx11-xcb1 libsuitesparse-3.1.0
  python2.4-minimal libboost-date-time1.34.1 librasqal0 python2.4 libglide2
  libgnome-desktop-2-7 libx264-59 python-twisted-mail aumix
  linux-headers-2.6.28-11-generic xfce4-icon-theme libpulsecore5
  libwxbase2.6-0 python-pyme classpath-gtkpeer libmono-getoptions1.0-cil
  python-twisted-lore libpoppler3 libmono1.0-cil python-twisted-news
  python-twisted-words libmjpegtools0c2a libmono-data-tds1.0-cil
  python-twisted libtunepimp5 libifp4 libmono-system-data1.0-cil galeon-common
  libdvdread3 python-wxversion kdebase-workspace-data classpath-common
  gtk2-engines-xfce cacao xfce4-mcs-manager python-wxgtk2.6
  libxfce4mcs-manager3 classpath libisc44 sqlite3 libimlib2 libnova-0.12-2
  libnjb5 libggzdmod6 libpoppler-glib3 libntfs-3g28
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tarps87 on 2009-07-09
> **hmich176 said:**
> Here's the uname - a result:
```
harry@harry-laptop:~$ uname -a
Linux harry-laptop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

Right, do you have any previous kernels installed? When the boot menu loads are there several entries?

---

### Post by hmich176 on 2009-07-09
> **tarps87 said:**
> Right, do you have any previous kernels installed? When the boot menu loads are there several entries?

No, it directly boots into this version of Ubuntu. On my PC, I have both Windows and Linux (I'm still running 7.10 on that one, believe it or not!) which has several entries on the boot menu.

---

### Post by Maheriano on 2009-07-09
Discussed and solved many many many many many many times already. Search for the solution.

---

### Post by hmich176 on 2009-07-09
I don't know what's wrong.  So how can I search for a solution?

---

### Post by Knacker_Ned on 2009-07-09
> **Maheriano said:**
> Discussed and solved many many many many many many times already. Search for the solution.

Maheriano, a link to that solution would be nice. Thanks in advance...

---

### Post by hmich176 on 2009-07-09
> **Knacker_Ned said:**
> Maheriano, a link to that solution would be nice. Thanks in advance...

Yeah.  It would be appreciated instead of you coming in here telling me to search.  I post on enough boards to know when to search.  But when I don't know what terms to use to search, I make a thread.  It's just easier.  If a mod wants to close the thread or merge the thread because there are so many, then that's their perogative.

---

### Post by LewRockwell on 2009-07-09
> **hmich176 said:**
> Yeah.  It would be appreciated instead of you coming in here telling me to search.  I post on enough boards to know when to search.  But when I don't know what terms to use to search, I make a thread.  It's just easier.  If a mod wants to close the thread or merge the thread because there are so many, then that's their perogative.

well, it's kind of a tit for tat deal

for many here, attempting to assist others(not unlike yourself), it's a big pet peeve to get poor titles and non-existent/non-specific information with respect to the trouble-call

hopefully this makes sense

Edit: also, it is quite simple to change the title of a thread by editing the title area in the thread creator's first post

.

---

### Post by hmich176 on 2009-07-09
> **LewRockwell said:**
> well, it's kind of a tit for tat deal

for many here, attempting to assist others(not unlike yourself), it's a big pet peeve to get poor titles and non-existent/non-specific information with respect to the trouble-call

hopefully this makes sense

Edit: also, it is quite simple to change the title of a thread by editing the title area in the thread creator's first post

.

Fair enough, I can change the title to help with that. 
But being told to search when I don't know what the problem is doesn't help either.  

What should the title be?  I can't open Firefox, Ubuntu takes much longer to load, Ubuntu runs rather sluggish, and the update runs into an error. Plus, everything I've tried to do so far, based on the suggestions in this thread, end in an error of some kind.

---

### Post by Jazzy_Jeff on 2009-07-09
> **LewRockwell said:**
> well, it's kind of a tit for tat deal

for many here, attempting to assist others(not unlike yourself), it's a big pet peeve to get poor titles and non-existent/non-specific information with respect to the trouble-call

hopefully this makes sense

Edit: also, it is quite simple to change the title of a thread by editing the title area in the thread creator's first post

.

Shouldn't be a pet peeve, either you want to help or you don't. Simple as that. No one is forcing you to help.

---

### Post by cptr13 on 2009-07-09
You have got to be kidding...., search the forums isn't an acceptable answer as far as I'm concerned.  First of all, these are the Ubuntu forums, not any other distro.  I've been using linux for a few years now, and while we should encourage everyone to learn to search out thier own solutions first, I've found that the general attitude in the Ubuntu forums is far better about that then most other distros.  Secondly....this is a NEWBIE area.  No offense to any posters, but when we respond to posts here, we should respond as if they're.....wait for it.....newbies.

Crazy huh.

Tell him to search, and include the link next time.  It's crap like that that will chase folks away who are trying it out for the first time.

---

### Post by LewRockwell on 2009-07-09
> **Jazzy_Jeff said:**
> Shouldn't be a pet peeve, either you want to help or you don't. Simple as that. No one is forcing you to help.

no one forced ANY of us to post here...

but that didn't stop ANY of us either...

.

---

### Post by LewRockwell on 2009-07-09
how's that for a new title?

.

---

### Post by hmich176 on 2009-07-09
Well, that's the best title I could come up with.  

But seriously, I really could use the help.

---

### Post by LewRockwell on 2009-07-09
let's try this:

do a cold boot(just for the sake of saying we did it)

go to System > Administration > Update Manager

It should automatically check but if it doesn't you can do it manually

then, when you're done there...

go to System > Administration > Synaptic Package Manager

You'll be asked for the administrator's password

in the package manager you'll use the quick search box to enter "firefox"

there should be a green box indicating that "firefox" is installed

when you left-click on the green box you should get a menu and you should select "Mark for Complete Removal"(note that configuration settings/files will be deleted so don't do the complete removal if you can't live without your previous settings and such)

after you've made your selections then you'll apply them and you might get an additional screen confirming the deletion of dependencies(which is fine)

once the package removal is complete you should reboot, go back to the package manager, use the reload function, mark firefox for installation and follow the normal procedures to apply that installation

then, the next time you have a chance(after your next reboot) go back to package manager and choose "Reload", then "Mark All Upgrades", then "Apply" and here again you'll get message(s) regarding dependencies which is normal

it should also be noted that the directions you were given by others, using the command line are also fine, but the package manager is there kind of like a multiple-choice question(complete with hints) instead of just an essay question...lol.

keep us posted!

.

---

### Post by LewRockwell on 2009-07-09
> **hmich176 said:**
> Well, that's the best title I could come up with.  

But seriously, I really could use the help.

to change it for the thread as a whole you'll need to edit your first post in this thread with the new title

(just sayin'...)

.

---

### Post by hmich176 on 2009-07-09
I actually did that before, with no luck.

When I run depmod, I get this error
```
E: linux-image-2.6.28-13-generic: subprocess post-installation script returned error exit status 1
```

---

### Post by LewRockwell on 2009-07-09
> **hmich176 said:**
> I actually did that before, with no luck.

I saw that, sorry...my mistake...and here all this time...lol...go figure...

.

---

### Post by LewRockwell on 2009-07-09
> **cptr13 said:**
> You have got to be kidding...., search the forums isn't an acceptable answer as far as I'm concerned.  First of all, these are the Ubuntu forums, not any other distro.  I've been using linux for a few years now, and while we should encourage everyone to learn to search out thier own solutions first, I've found that the general attitude in the Ubuntu forums is far better about that then most other distros.  Secondly....this is a NEWBIE area.  No offense to any posters, but when we respond to posts here, we should respond as if they're.....wait for it.....newbies.

Crazy huh.

Tell him to search, and include the link next time.  It's crap like that that will chase folks away who are trying it out for the first time.

some have thicker skin than others...

definitely...

.

---

### Post by LewRockwell on 2009-07-09
> **hmich176 said:**
> I actually did that before, with no luck.

When I run depmod, I get this error
```
E: linux-image-2.6.28-13-generic: subprocess post-installation script returned error exit status 1
```

this is an older thread but it might be good reading anyway

food for thought(s):

[http://ubuntuforums.org/showthread.php?t=253415](http://ubuntuforums.org/showthread.php?t=253415)

and another one geared more on the technical side:

[http://plosquare.blogspot.com/2009/01/subprocess-post-installation-script.html](http://plosquare.blogspot.com/2009/01/subprocess-post-installation-script.html)

---

### Post by hmich176 on 2009-07-09
Well, I'm not sure how to fix the problem.  For whatever reason depmod just fails to run.

---

### Post by LewRockwell on 2009-07-09
> **hmich176 said:**
> Well, I'm not sure how to fix the problem.  For whatever reason depmod just fails to run.

It may be easier to reinstall than to continue fighting an unknown

I know it's frustrating from your side, but it's also frustrating for those of us who continually encourage others to do back-ups/clones and to off-load valuable static data/files/images/etc. to optical media for long-term secure storage

Not too long ago a gal had spent literally YEARS putting photos in her computer and doing genealogy research and data entry...

Guess what...yep, no back-up...AB-SO-LUTELY...NOTHING...

Somebody broke in and stole her computer...

Now, there's nothing to be done about that except to hope that the thieves get caught and the computer is recovered intact, but the odds of that happening are slim to none...

.

---

### Post by Maheriano on 2009-07-09
Took me 6 seconds.

[http://ubuntuforums.org/showthread.php?t=1158471](http://ubuntuforums.org/showthread.php?t=1158471)

---

### Post by Jazzy_Jeff on 2009-07-09
> **Maheriano said:**
> Took me 6 seconds.

I feel sorry for your girlfriend.  :lolflag:

---

### Post by hmich176 on 2009-07-09
> **Maheriano said:**
> Took me 6 seconds.

[http://ubuntuforums.org/showthread.php?t=1158471](http://ubuntuforums.org/showthread.php?t=1158471)

Did you read my post?  I have bigger problems than Firefox not working.  

When I tried to run Firefox in safe mode it gave me this:
```
harry@harry-laptop:~$ firefox -safe-mode
Bus error

```

---

### Post by Maheriano on 2009-07-10
> **hmich176 said:**
> Did you read my post?  I have bigger problems than Firefox not working.[/code]
Yes, I did. Enlighten me, oh great one, where you mention anything besides your whining about Firefox.
> **hmich176 said:**
> I had a problem with Ubuntu this morning.  I tried to open Firefox and it completely froze the system.  I had to manually reboot, and when I did, it took a rather long time just to get through the Ubuntu loading splash screen.  

Once I got to my standard desktop, whenever I try to open Firefox, it says it's opening but never does.  I tried uninstalling and reinstalling Firefox, but that didn't help anything.  

I tried to do a system update, but it couldn't complete the update.  

So, I'm not sure what to do from here.  I'm using an older version of Opera (which is an okay browser, I guess) since Firefox won't work.  The system also runs very sluggish.

You mention other issues like the system taking longer to start up and the updates not working but when your troubleshooting and descriptions are that vague, who's going to take their time to help you?
> ** hmich176 said:**
> I tried to do a system update, but it couldn't complete the update.  
Well, that makes sense. By providing us zero troubleshooting and not even remotely describing what your problem is, garbage like this gets ignored. Thus bringing us to the only useful pieces of information you posted being about your Firefox problem. So again, point out to me where you mentioned your other troubles.

---

### Post by Don1500 on 2009-07-10
I think a reinstall may be your best bet. But do it by the book this time, don't try anything fancy. Do it from a verified Live Disk. If you don't have a live CD, downlown the ISO, check it for errors, and make one using the slowest speed your burner allows.

---

### Post by hmich176 on 2009-07-11
> **Don1500 said:**
> I think a reinstall may be your best bet. **But do it by the book this time**, don't try anything fancy. Do it from a verified Live Disk. If you don't have a live CD, downlown the ISO, check it for errors, and make one using the slowest speed your burner allows.

What do you mean by that?  I've been running 9.04 since it was released.

---

### Post by Don1500 on 2009-07-11
OK, maybe I was a little presumtive. I have know of people that try to update using their own methods, I have no reason to assume you did anything wrong. I just ment that a complete install with a known good live CD is usually the best method.

---

### Post by hmich176 on 2009-07-11
> **Don1500 said:**
> OK, maybe I was a little presumtive. I have know of people that try to update using their own methods, I have no reason to assume you did anything wrong. I just ment that a complete install with a known good live CD is usually the best method.

Okay.  I'll have to give that a shot.

---

### Post by tarps87 on 2009-07-13
Sorry for not posting back sooner been busy. As you only have the one kernel installed fixing the problem may prove risky, I think your safest bet is to back up your data and reinstall. I believe the update problem was cause by the improper power down. If you do need to force a shutdown try the key combination I posted at the start. That said it is still rare for it to kill the system.
If you have any problems with Firefox after the install or you need suggestions with backing up your data just post back

> **Maheriano said:**
> Yes, I did. Enlighten me, oh great one, where you mention anything besides your whining about Firefox.

You mention other issues like the system taking longer to start up and the updates not working but when your troubleshooting and descriptions are that vague, who's going to take their time to help you?

Well, that makes sense. By providing us zero troubleshooting and not even remotely describing what your problem is, garbage like this gets ignored. Thus bringing us to the only useful pieces of information you posted being about your Firefox problem. So again, point out to me where you mentioned your other troubles.

The original problem was related to Firefox but in trying to solve this problem a bigger problem was unearthed.

If you look at the link you posted the problem is that Firefox closes, this problem is it has frozen the system and this has cause other problems. Please read what is written before assaulting people and please remember that not everyone know what information is valid and what is not.

---

