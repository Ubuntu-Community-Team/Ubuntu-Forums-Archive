---
title: "What Automatix has wrought can someone (help me) rent asunder?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Langstracht on 2009-08-12
I am a bit vague about the chronology but it seems that when "Update Manager" tried to install libnspr4-dev, it broke adobe-flashplugin.  

The resulting error message being "E: /var/cache/apt/archives/libnspr4-dev_4.7.1 +1.9-0ubuntu0.8.04.5_i386.deb: trying to overwrite '/usr/share/aclocal/nspr.m4' which is also in package mozilla-dev"

I now find myself with two broken packages (adobe-flashplugin and libnss3-dev) and they have "unmet dependencies".

A further message suggested "You might want to run `apt-get -f install' to correct these.".  

So I ran apt-get -f install

and got:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
libnspr4-dev
The following NEW packages will be installed:
libnspr4-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/258kB of archives.
After this operation, 1430kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 169702 files and directories currently installed.)
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb (--unpack):
trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package mozilla-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So proceeded to sudo apt-get clean with no errors or anything ...

Then sudo apt-get check

which got me:

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
adobe-flashplugin: Depends: libnspr4-dev but it is not installed
libnss3-dev: Depends: libnspr4-dev but it is not installed
E: Unmet dependencies. Try using -f.

Which of course is where I started.

Can anyone help?  Please.

---

### Post by rajeev1204 on 2009-08-12
Did you try sudo dpkg --configure -a?

If that doesnt work try:

dpkg --remove --force-remove-reinstreq adobe-flashplugin

---

### Post by Langstracht on 2009-08-12
Thanks for you prompt response.

I did not try sudo dpkg --configure -a.  

The results are:

dpkg: dependency problems prevent configuration of libnss3-dev:
 libnss3-dev depends on libnspr4-dev; however:
  Package libnspr4-dev is not installed.
dpkg: error processing libnss3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libnspr4-dev; however:
  Package libnspr4-dev is not installed.
 adobe-flashplugin depends on libnss3-dev; however:
  Package libnss3-dev is not configured yet.
dpkg: error processing adobe-flashplugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnss3-dev
 adobe-flashplugin

So, as you suggested, I tried 

dpkg --remove --force-remove-reinstreq adobe-flashplugin.  

And indeed, it is now gone.

However, as might be expected I guess, libnss3-dev is not.

I assume you will want me to (re)install adobe.  Yes?  But I think libnss needs dealing with first ...???

---

### Post by ghostborg on 2009-08-12
I thought Automatix was discontinued and so I searched and found this in the
Wikipedia.

From Wikipedia

Automatix was discontinued in early 2008.[7]

A new project called Ultamatix, compatible with Ubuntu 8.04, was based on Automatix, however, it does not work on Ubuntu 9.04.

---

### Post by scorp123 on 2009-08-12
Automatix was ugly (from a sysadmin and scripting point of view ...) and unstable (in that it changed your system without even bothering to ask you ...) like hell.

**DON'T USE IT.**

[http://www.psychocats.net/ubuntucat/why-i-dont-recommend-automatix-not-what-you-may-think-2/](http://www.psychocats.net/ubuntucat/why-i-dont-recommend-automatix-not-what-you-may-think-2/)

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

[http://forums.linuxmint.com/viewtopic.php?f=47&t=4386&start=0&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=47&t=4386&start=0&st=0&sk=t&sd=a)

---

### Post by Langstracht on 2009-08-12
I (now) realize that Automatix had issues and I will not use it again.  However I still need guidance with my problem:

1 - what to do with/about libnss3-dev 

2 - what to do about restoring adobe-flashplugin

...

---

### Post by scorp123 on 2009-08-12
> **Langstracht said:**
> 1 - what to do with/about libnss3-dev 

2 - what to do about restoring adobe-flashplugin
...

1. Check your sources.list and files underneath sources.list.d
==> All those entries should point to *.ubuntu.com servers
==> comment out (= place a "#" in front of it) any other strange entries ...
... or simply come here and ask. The goal here is to remove anything
that Automatix might have added.

2. Underneath /etc/apt/sources.list.d you might have *.list files. Take a look at those. Same as above: if anything they should point to *.ubuntu.com or *.ppa.launchpad.net servers ... Be super-duper suspicious of anything that points anywhere else. Stuff you know for 100% sure _you_ added is OK ... but please remove anything that Automatix might have added.

3. Once this is done:
```
sudo apt-get clean
sudo apt-get update

```

4. Resolving conflicting packages is ugly. I'd suggest to remove "mozilla-dev" (probably installed via Automatix?) because usually it's not so essential (I for example have tons of stuff but not that package ... so it can't be *that* important I guess? :D
```
sudo apt-get remove mozilla-dev
```

Once "mozilla-dev" is gone the package manager should resolve the remaining issues by itself.

If it doesn't  ... please give me the error messages you get after removing "mozilla-dev", OK?

---

### Post by ibuclaw on 2009-08-12
What version of Ubuntu do you use? 9.04?

> /var/cache/apt/archives/libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb
If you aren't running Ubuntu 8.04, be worried, as it looks like it is trying to force an installation of an 8.04 package (and it's possibly deprecated package dependancies) onto what I presume to be your 9.04 Ubuntu installation.

I suggest just to remove them, check your sources and ensure that nothing extraneous is in there, (this can be done by using "**System -> Administration -> Software Sources**" then install again.

Regards
Iain

---

### Post by Langstracht on 2009-08-12
Actually I AM running 8.04.  

So ... I should do what?

---

### Post by Langstracht on 2009-08-12
Sorry I missed a message there ... but in response to scorp123 removing got me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libnss3-dev: Depends: libnspr4-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

s-i-g-h-!-!-!

---

### Post by kansasnoob on 2009-08-12
Hello. Sorry to have left you hanging but I was basically out of gas on the whole thing. Thought I might reference the old thread so folks could get a better idea what you're up against.

[http://ubuntuforums.org/showthread.php?t=1229514&page=5](http://ubuntuforums.org/showthread.php?t=1229514&page=5)

I'm still thinking about generating a whole new sources list using a 8.04.3 live CD (of course selecting main server as source) and having you just replace the entire /etc/apt/sources.list.

But I can't guarantee anything.

If you want to go that way I can generate a new sources list for you. I'll just spin up my 8.04.3 live CD.

---

### Post by Langstracht on 2009-08-12
Hey no worries ... and thanks for all your help.

I may well take advantage of your offer ... but I think I need to get rid of (or maybe just deal with) this libnss3-dev thing.  Don't think the sources list is going to help with that.

---

### Post by RealG187 on 2009-08-12
Automatix?

I think I used the a long time ago.

I used it because a guide somewhere said to use it to get Ubuntu to play MP3, MP4, WMA, etc.

Now I just know to install "ubuntu-restricted-extras"

I heard automatix had problems or something and not to use it. There was another one too, I think it was called "Easy Ubuntu" or something like that...

---

### Post by scorp123 on 2009-08-12
> **Langstracht said:**
> libnss3-dev: Depends: libnspr4-dev but it is not going to be installed Well then ... remove "libnss3-dev" too for now. ```
sudo apt-get remove libnss3-dev
```

---

### Post by Langstracht on 2009-08-12
Golly, sure is simple.  When you know what you're doing.  Or aren't afraid to try.

O.K. so I think libnss3-dev and mozilla-dev and adobe-flashplugin and Automatix are all gone.

Now nothing else to do but to use update manager to (re)install adobe-flashplugin.  Right?

---

### Post by kansasnoob on 2009-08-13
But you still have no flash, eh?

Regardless, I had a thought .......... scary maybe, given I'm full of Percocet, but something I think should be considered.

In the process of trying to fix what Automatix trashed you may hose your Ubuntu so it would be good to know how much stuff you have to back up?

In other words, let's plan for the worst. Assuming you have only one hard drive it would be helpful to see a screenshot of Gparted. If it's already installed you'll find it at System > Administration > Partition Editor.

If it's not yet installed it's in Synaptic so it can be installed from there or from terminal with:

```
sudo apt-get install gparted
```

If you have more than one hard drive we should start with the output from terminal of:

```
sudo fdisk -l
```

We'll keep at this!

Hopefully some old-timey guru will see your dilemma and jump in with an easy fix.

---

### Post by scorp123 on 2009-08-13
> **Langstracht said:**
>  Now nothing else to do but to use update manager to (re)install adobe-flashplugin.  Right? Yes. Or "ubuntu-restricted-extras" so you get codecs and what not else too.

---

### Post by scorp123 on 2009-08-13
> **kansasnoob said:**
>  In the process of trying to fix what Automatix trashed you may hose your Ubuntu ...  Unlikely :D

Please don't spread panic, OK?

---

### Post by rajeev1204 on 2009-08-13
> **kansasnoob said:**
> But you still have no flash, eh?

Regardless, I had a thought .......... scary maybe, given I'm full of Percocet, but something I think should be considered.

In the process of trying to fix what Automatix trashed you may hose your Ubuntu so it would be good to know how much stuff you have to back up?

In other words, let's plan for the worst. Assuming you have only one hard drive it would be helpful to see a screenshot of Gparted. If it's already installed you'll find it at System > Administration > Partition Editor.

If it's not yet installed it's in Synaptic so it can be installed from there or from terminal with:

```
sudo apt-get install gparted
```

If you have more than one hard drive we should start with the output from terminal of:

```
sudo fdisk -l
```

We'll keep at this!

Hopefully some old-timey guru will see your dilemma and jump in with an easy fix.


kansas noob this reply is not needed at all.This kind of breakage is rare with automatix or anything else.

Langst....... just follow these for flash.

To install flash do the following:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Langstracht on 2009-08-13
O.k.  it looks like I'm good to go now.  

I think, thanks to the "restricted-extras" I've gotten a new font on (it seems) every web page ... and I don't like it too much.  But other than that, no broken links, no install refusals, no missing dependencies, no bad news at all.

As for partitioning.  I didn't have the brains to partition when I first installed ubuntu.  And when I finally figured out that I should have I had so much on the HD that I don't have enough room to make a partition.  Next time ... he said hopefully.

So thanks particularly to scorp123 for restoring my sanity.

---

### Post by scorp123 on 2009-08-13
> **Langstracht said:**
> So thanks particularly to scorp123 for restoring my sanity. You're welcome. :guitar:

---

