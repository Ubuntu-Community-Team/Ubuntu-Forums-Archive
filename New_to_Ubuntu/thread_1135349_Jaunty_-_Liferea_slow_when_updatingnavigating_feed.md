---
title: "Jaunty - Liferea slow when updating/navigating feeds"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-24
I've been a heavy user of liferea for a year or so. Its been a great program for RSS!

Unfortunately after upgrading to Jaunty (and ext4), liferea (1.4.26) is PAINFULLY slow, hanging all the time (window greys out). Is this a known issue?

---

### Post by billgoldberg on 2009-04-24
> **abhiroopb said:**
> I've been a heavy user of liferea for a year or so. Its been a great program for RSS!

Unfortunately after upgrading to Jaunty (and ext4), liferea (1.4.26) is PAINFULLY slow, hanging all the time (window greys out). Is this a known issue?

No idea.

Start it from the terminal and look if it gives any error messages.

If it gives error messages, create a launchpad bug report or something.

You could always manually install an older version if it's bothering you that much, or use another rss feed reader.

---

### Post by abhiroopb on 2009-04-24
I noticed that the bug has been reported...

[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/290666](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/290666)
[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/335471](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/335471)

Any suggestions for other RSS readers?

---

### Post by iamnotthemessiah on 2009-04-24
same issue here. tried all the rrs readers on gnomefiles but none comes close to liferea. 'straw' perhaps is the one ill migrate to cos liferea cant be used as it is now

---

### Post by abhiroopb on 2009-04-24
straw doesn't seem to support folders very well. I tried akregator and apart from it being a big install it seemed to re-update my feeds every time it started, downloading things I'd already read. Shame that liferea is broken :(

---

### Post by borislevalle on 2009-04-24
I love almost everything about Ubuntu, but somehow readers are a week point. I had the same problem with Akregator as abhiroopb. Liferea is better, but getting slower. I hope we'll get something like RSSOwl for Linux one day.

---

### Post by abhiroopb on 2009-04-24
RSSOwl seems to work in linux (as it is a java app). Still not as clean as liferea, but it definitely a good replacement for the moment.

---

### Post by abhiroopb on 2009-04-27
This is a temporary fix:

enter the following in a terminal:
```

cd /usr/src
mkdir libfsync
sudo gedit libfsync.c

```

Enter the following into the text file:
```

int fsync (int fd) {
 return 0;
}

```

Again in the terminal:
```

sudo gcc -Wall libfsync.c -o libfsync.so -shared -fPIC -Wl,-soname,libfsync.so
sudo gedit /usr/bin/liferea 

```


Enter the following into the SECOND LINE of the text file:
```

export LD_PRELOAD=/usr/src/libfsync/libfsync.so

```

No idea what it does, but it was suggested in the launchpud page and it worked for me ([https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/333718](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/333718)).

---

### Post by natrium on 2009-04-29
worked for me! thanx! :KS

---

### Post by nischg on 2009-04-29
Things with Liferea 1.5.15 seem to be a little different. I can't edit the /usr/bin/liferea file. 

Does anyone know what file has to be edited in this version? :)

---

### Post by abhiroopb on 2009-04-29
should be the same, what error are you getting? (remember to use sudo)

---

### Post by nischg on 2009-04-29
Gedit refuses to open the file saying something about character localization. If I try to edit it using Vi I only see a bunch of strange characters so I'm guessing it's not the file I should be messing around with since it's not a config file for Liferea.

---

### Post by abhiroopb on 2009-04-29
The file is not a config file, its the file that launches the actual liferea program. If there is something wrong with the file, then there may be something wrong with your liferea. I suggest doing a complete re-install (ensuring you do rm /usr/bin/liferea) to make sure that you delete your corrupt file. And then install. Then try running the commands.

---

### Post by nischg on 2009-04-29
Thank you for your help. I'll try your suggestion and edit this post with the results.

---

### Post by abhiroopb on 2009-04-29
No problem. 

I'd also like to add that I did not come up with the solution and only found it on the launchpad page, so unfortunately I can't really help if there is a problem with the solution itself.

Good Luck!

---

### Post by nischg on 2009-04-30
Well, this fix works with Liferea 1.4. I had no success with 1.5.15 from the Liferea PPA. The file that has to be edited in this version isn't the same as in 1.4, so I'm sticking with it.

---

### Post by druellan on 2009-05-07
Same problem here. I read in the bug report that perhaps is related to Liferea + ext4. Are you guys all using ext4?

BTW, for a very good reader I can recommend [BRIEF]("https://addons.mozilla.org/en-US/firefox/addon/4578") Firefox add-on.

---

### Post by fshapps on 2009-05-08
> **druellan said:**
> Same problem here. I read in the bug report that perhaps is related to Liferea + ext4. Are you guys all using ext4?

BTW, for a very good reader I can recommend [BRIEF]("https://addons.mozilla.org/en-US/firefox/addon/4578") Firefox add-on.

Nope. Just plain old ext3.

---

### Post by rdjse on 2009-05-13
> **druellan said:**
> Same problem here. I read in the bug report that perhaps is related to Liferea + ext4. Are you guys all using ext4?

BTW, for a very good reader I can recommend [BRIEF]("https://addons.mozilla.org/en-US/firefox/addon/4578") Firefox add-on.

I have the same (or similar problem). Liferea is trashing my disk whenever I try to read a feed entry. I'm not using EXT4 but EXT2 cause I run Ubuntu on my Netbook. 
Everything worked fine in 8.10 but after upgrading to 9.04 Liferea is unusable due to heavy disk access.

I hope it gets fixed soon tho!

---

### Post by abhiroopb on 2009-05-13
I tried my fix on 1.5 and above and it does not work. For now, if you are using 9.04 (whether ext2, ext3 or ext4) I suggest using the fix I have outlined with liferea 1.4

---

### Post by rdjse on 2009-05-14
> **abhiroopb said:**
> I tried my fix on 1.5 and above and it does not work. For now, if you are using 9.04 (whether ext2, ext3 or ext4) I suggest using the fix I have outlined with liferea 1.4

I got impatient and tried the fix suggested in this thread and it worked for me! :popcorn:

---

### Post by z0mbie on 2009-05-31
I seem to have the issue after a fresh install with ext4. I was on ext3 before and there was no problem. For now I'm using [Sage]("https://addons.mozilla.org/en-US/firefox/addon/77") Firefox extension for RSS. I'll wait until the bug is patched.

---

### Post by linux_mafia on 2009-06-01
I am on Jaunty with ext3, so glad I saw this thread, was having the exact behaviour others reported, lockups, disk thrashing etc.

I can confirm the the fix mentioned by abhiroopb at [https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/333718](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/333718) works for me.

Although the fix won't cause any problems, I would read the launchpad thread before blindly doing it, just so you get the jist of what you are doing.

---

### Post by abhiroopb on 2009-06-01
could you perhaps explain what it does? I still don't fully understand it!

---

### Post by z0mbie on 2009-06-01
> **abhiroopb said:**
> could you perhaps explain what it does? I still don't fully understand it!

There's a high CPU usage.

The current version in Jaunty repos is version 1.4.**26**, it seems like the next stable version 1.4.**28** has the fix according to [Liferea's change log]("http://liferea.svn.sourceforge.net/viewvc/liferea/branches/liferea-1_4/liferea/ChangeLog"): 

> 2009-04-12  Lars Lindner  <lars.lindner@gmail.com>

	Version 1.4.28 (Stable)

	* Adds a possible fix for the 100% CPU issues by settings
	  places.frecency.updateIdleTime to 0.
	  (suggested by Axel Beckert)

I guess we have to wait for the next version in the repos or you can compile it on your own.

---

### Post by Mornedhel on 2009-06-01
> **abhiroopb said:**
> could you perhaps explain what it does? I still don't fully understand it!

It replaces the unistd (standard) fsync function with one that does nothing but return successfully. fsync (2) is normally used to ensure that modifications to a file are completed and written to disk before proceeding. Apparently Liferea has an issue with fsync somewhere (didn't read the bug report, may contain more details).

Basically this sacrifices safe input/output for the sake of having Liferea work, but it should be safe since the fix from abhiroopb's post affects only Liferea and no other application. Although it will cause a few issues in the case of a system crash (power loss, whatever) while Liferea is running.

I should note that Liferea works perfectly on my system out of the box.

---

### Post by z0mbie on 2009-06-02
Everyone try this Liferea PPA repository. It has the version 1.6.0-rc3 of Liferea and is running very smoothly on Jaunty:

> [https://launchpad.net/~liferea/+archive/ppa](https://launchpad.net/~liferea/+archive/ppa)

*Also requires this Webkit PPA:

> [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by abhiroopb on 2009-06-02
> **z0mbie said:**
> Everyone try this Liferea PPA repository. It has the version 1.6.0-rc3 of Liferea and is running very smoothly on Jaunty:



*Also requires this Webkit PPA:

Its certainly better than 1.4, but its still a little laggy. Since the fix works fine (without any major problems). I am content to use the fix for now.

---

### Post by DMS86 on 2009-06-20
> **abhiroopb said:**
> This is a temporary fix:

[...]

I'm with Jaunty and ext4, Liferea 1.4.26 and it works. Thank you!

---

### Post by okubax on 2009-06-26
> **abhiroopb said:**
> This is a temporary fix:


the fix works thanks. now i can continue to use liferea with ext4 on jaunty

---

### Post by WorLord on 2009-06-29
Thank you, z0mbie!  Liferea 1.6 works *great*, and without the need to disable a very basic feature like fsync.  Kudos!

---

### Post by abhiroopb on 2009-06-29
I;m not sure. 1.6 still seems slower than just switching fsync off!

---

### Post by lemonade on 2009-08-18
> **abhiroopb said:**
> I;m not sure. 1.6 still seems slower than just switching fsync off!

I noticed that my ext4 partition had barrier-bit enabled. After setting mount option barrier=0 liferea and all other sqlite-software got huge boost and aren't slow anymore. Perhaps it could be your issue too?

---

### Post by pwc on 2009-08-20
How do you set mount option barrier=0. I can't find it.

Thanks

---

### Post by abhiroopb on 2009-08-29
Yes I would like to try and change "mount option barrier=0" but I'm not sure how I am supposed to do that.

---

### Post by abhiroopb on 2009-08-29
There is a good guide here on how to change it:

[http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/)

But it still seems slower for me. If I have a feed with 50 unread items and I do "mark all as read" it takes a few seconds (upto 30-40) before it completes the action.

---

### Post by quisnox on 2010-11-07
It's filesystem problem... And any "fixes" can really do something BAD, I think:roll:
.
Dude in this forum used fix, that 'overrides' 'file system sync' 

The best solution is wait for new Liferea release (who knows - this fixed in trunk builds, maybe?)

---

### Post by docomo on 2011-01-24
This made liferea faster for me:

[http://liferea.blogspot.com/2008/08/how-to-run-vacuum.html](http://liferea.blogspot.com/2008/08/how-to-run-vacuum.html)

> Situations when you might want to VACUUM

    * When the DB file (~/.liferea_1.4/liferea.db) is very large (e.g. >50MB)
    * When you have only a few feeds with a low cache setting (e.g. 30 feeds and 100 items) and believe Liferea to be unreasonably slow.
    * When you have run Liferea for ages.

My liferea.db was 80MB.

---

