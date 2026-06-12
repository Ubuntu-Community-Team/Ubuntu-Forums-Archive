---
title: "Cleaning/Maintaining Ubuntu Linx??? How??"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by xXPetabyteXx on 2010-11-26
So yeah... you know how in Windows where you gotta keep everything clean and stuff? (CCleaner, Registry Cleaners, Utilities, ETC.) %Temp% Windows\TEMP. 
I'm kinda new to Ubuntu and I'm wondering if you need to do similar stuff. Does crap build up??? If so, please tell me how to delete them or like a program that does it.

If you guys can give me some tips on Ubuntu maintenance, that'd be great :D

---

### Post by xXPetabyteXx on 2010-11-26
o yeah... you know how in Windows where you gotta keep everything clean  and stuff? (CCleaner, Registry Cleaners, Utilities, ETC.) %Temp%  Windows\TEMP. 
I'm kinda new to Ubuntu and I'm wondering if you need to do similar  stuff. Does crap build up??? If so, please tell me how to delete them or  like a program that does it.

If you guys can give me some tips on Ubuntu maintenance, that'd be great :grin:

---

### Post by xXPetabyteXx on 2010-11-26
bump

---

### Post by xXPetabyteXx on 2010-11-26
bump:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by ivarn on 2010-11-26
install ubuntu tweak (from synaptic), when installed you will find ubuntu tweak under applications > system tools. now in ubuntu tweak go to ( i think it's called ) package cleaner, and you'll see all the useless packages and configs you can remove there.
These are basically removed packages, older kernels, cache and config settings from removed programs.
You should also use BleachBit (also in synaptic).
With bleachbit you can remove trash such as browser history, cache, empty files / folders and duplicated files. 

Two very useful tools.

---

### Post by karthick87 on 2010-11-26
**Linux!=Windows** See it's necessary here like you do in windows.In ubuntu all your temporary files will be stored under /tmp and automatically it will be deleted on reboot.

To clear the package cache,type the following in terminal
```

sudo apt-get clean
```You can also use bleachbit to clean up unwanted files
```
sudo apt-get install bleachbit
```

---

### Post by xXPetabyteXx on 2010-11-26
> **ivarn said:**
> install ubuntu tweak (from synaptic), when installed you will find ubuntu tweak under applications > system tools. now in ubuntu tweak go to ( i think it's called ) package cleaner, and you'll see all the useless packages and configs you can remove there.
These are basically removed packages, older kernels, cache and config settings from removed programs.
You should also use BleachBit (also in synaptic).
With bleachbit you can remove trash such as browser history, cache, empty files / folders and duplicated files. 

Two very useful tools.
Thanks for the help!!!!!

---

### Post by ronnielsen1 on 2010-11-26
That's all windows. The linux file system doesn't need defragged. You can relax a little more than you're used to

---

### Post by bioterror on 2010-11-26
First of all, you dont have to bump in 3 minutes if no one answers.
And no, Linux doesnt have samekind of registry as Windows does which "needs" cleaning.

All you need to do is run apt-get clean and apt-get autoremove.
/temp is cleaned after every boot (/var/temp/ not).

Just use your Linux system and stop worrying about Windows problems.

---

### Post by ivarn on 2010-11-26
> **ronnielsen1 said:**
> That's all windows. The linux file system doesn't need defragged. You can relax a little more than you're used to
He's talking about cleaning up useless files to free up space, not defragging, but yes you can relax a bit more. Even tho the system goes faster with less unnecessary files.

---

### Post by xXPetabyteXx on 2010-11-26
okai

---

### Post by xXPetabyteXx on 2010-11-26
BleachBit works good :D thanks guys, i can rest a bit easier now

---

### Post by madjr on 2010-11-26
> **xXPetabyteXx said:**
> okai

ubuntu tweak should give you everything you need

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

and no worry. even after years of use , you wont see errors and tons of reg problems like in windows after a few months.

spyware/malware wont build up either

---

### Post by WorMzy on 2010-11-26
Ubuntu is a bloated operating system by Linux standards, but having left over files shouldn't cause any significant degradation of performance. Obsolete files will take up space, but not much else. Defragmentation, as mentioned, is not an issue, and Ubuntu doesn't have a registry like Windows does (there is gconf, but that's for GNOME programs only, and doesn't work the same way as the the Windows registry).

In short, rejoice. Your need-to-clean days are over. ;D

Of course, you will experience degradation if your partition becomes too full, but this is true with almost any file system. Use a separate partition for data storage, and you should be fine.

---

### Post by howefield on 2010-11-26
Threads merged.

Please post once for each issue and wait about 24 hours before bumping.

---

### Post by Guitar John on 2010-11-26
Did anyone mention Computer Janitor?

System>Administration>Computer Janitor

---

### Post by WorMzy on 2010-11-26
> **Guitar John said:**
> Did anyone mention Computer Janitor?

System>Administration>Computer Janitor

sdasdasfadfsd

Don't use Computer Janitor. More often than not, it causes more problems than it solves. It has potential; but as it stands, it's a fairly useless tool.

---

### Post by Tamalin on 2010-11-26
Linux doesn't "snowball" the way Windows does over time.  You probably won't have much extraneous data buildup as you would on windows.  Perhaps the only thing I do is occasionally go through and look at extra packages installed in my system.  You can run ```
sudo apt-get autoclean
``` to get rid of these.  The only other thing that has ever really built on any linux system for me is cookies from my browser, which can be cleared easily enough.

Good Luck!

---

### Post by ronnielsen1 on 2010-11-27
> Did anyone mention Computer Janitor?
> Don't use Computer Janitor. More often than not, it causes more problems than it solves. It has potential; but as it stands, it's a fairly useless tool.

Agree. Seems like a dangerous program for newbies

---

### Post by karthick87 on 2010-11-27
I recommend **[COLOR=Red]bleachbit [/COLOR]**for newbies.

---

### Post by Norm24 on 2010-11-27
> **karthick87 said:**
> I recommend **[COLOR=Red]bleachbit [/COLOR]**for newbies.

I second that!

Bleachbit is much safer than Computer Janitor too.

---

### Post by Andrew.Z on 2010-11-27
> **karthick87 said:**
> In ubuntu all your temporary files will be stored under /tmp and automatically it will be deleted on reboot.

There are temporary files stored in all sorts of application-specific places.  Here are a few examples

1. Firefox and Google Chrome don't store cache under /tmp.  

2. Many people consider the rotated system logs in /var/log/ to be temporary junk: each log is deleted eventually and automatically, but the system keeps so many day's worth of logs in place.  

> **bioterror said:**
> And no, Linux doesnt have same kind of registry as Windows does which "needs" cleaning.

Windows registry benefits from defragmentation, which Linux doesn't have.  Linux doesn't have a central registry like the Windows hive (as a developer, that would often be convenient, by the way).  However, if you consider "registry" to mean place (or places) to store settings,  [both Linux and Windows have registries](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html) with things in common such as

1. When an application (such as Firefox) is removed, the settings usually remain

2. Applications contain errors which leave behind non-sense settings such as a personal GNOME shortcut to an application that doesn't exist

Usually these things do not cause problems.

> **WorMzy said:**
>  Defragmentation, as mentioned, is not an issue,

The Linux file system doesn't need defragmentation, but many Linux applications store data in SQLite databases which do fragment.  BleachBit vacuums SQLite databases in Firefox, Google Chrome, Thunderbird, Liferea, etc.  [Vacuuming may make Firefox faster](http://bleachbit.sourceforge.net/documentation/faq).

---

### Post by Guitar John on 2010-12-01
> **WorMzy said:**
> 

sdasdasfadfsd

:confused:

> **WorMzy said:**
> Don't use Computer Janitor. More often than not, it causes more problems than it solves. It has potential; but as it stands, it's a fairly useless tool.

Something I should know about?  I haven't had any problems with it.

---

### Post by TNT1 on 2010-12-01
> **Guitar John said:**
> :confused:



Something I should know about?  I haven't had any problems with it.


:confused:
Dunno... I've read some horror stories, but I've also not had any trouble using it, although lately I tend to clean up via apt or tweak.

---

### Post by WorMzy on 2010-12-01
If you never install applications from outside of repositories, then you'll probably be fine. If you *do* use non-repo apps, then Janitor will mark them for removal whether you're using them or not. If you're not paying attention, or trust the application to know best, then bam, you've just lost a bunch of applications that you use on a regular basis. It's not too difficult to reinstall them, but it's still an inconvenience.

---

### Post by Guitar John on 2010-12-02
> **WorMzy said:**
> If you never install applications from outside of repositories, then you'll probably be fine. If you *do* use non-repo apps, then Janitor will mark them for removal whether you're using them or not. If you're not paying attention, or trust the application to know best, then bam, you've just lost a bunch of applications that you use on a regular basis. It's not too difficult to reinstall them, but it's still an inconvenience.

Ok, that makes sense.

---

