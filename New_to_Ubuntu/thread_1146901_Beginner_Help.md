---
title: "Beginner Help"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Coatze on 2009-05-03
Hello All,
Well I am new to Linux... well that is, new once again after a brief flirtation which ended when I realized I needed to have a functional computer (or at least one that was functional for me).  

Anyway, trying to get back at it and I am having three problems I just can't wrap my head around:

Just a slight irritation right now, but discourages me from setting anything up: Everything resets whenever I log back in.  That is, my backround changes don't keep, monitor selection (using second monitor w/ twin view) and my effects preferences reset.  How do I stop this from happening?

The next problem is basically the same thing happening in firefox.  Every time I open firefox, my bookmarks disappear, preference changes don't stick etc.

What's worse is firefox doesn't seem to want to do a few basic things.  Whenever I tried to download the user guide, it would tell me there was not enough space on the disk (however, I could download packages from the add/remove app...so that's obviously a lie).  The next problem is that it will not recognize login/search buttons.  I can click them, admire them, but they never lead me to the promised lands of my email account/this forum registration/search etc etc. 

Sooo any tips?

Sorry for being so long winded, and I hope I won't be inundated with links to other posts and invitations to use the search command(though if I deserve it, I deserve it).  Tried skimming through the guide, but didn't even seem to broach the topic, so i assumed if it was a common issue, it would be addressed pretty obviously.

Thanks,
Coatze

---

### Post by nandemonai on 2009-05-03
Sounds to me like you're running off a live CD. If that's the case changes are not saved as everything is saved to RAM.

You'll need to actually install if you want to be able to make changes...

---

### Post by Coatze on 2009-05-03
Oh come on now, do I really sound that hopeless? 

Heh, no, it is installed.

---

### Post by nandemonai on 2009-05-03
Didn't mean to sound condescending, that's just a rather odd issue and sounds exactly like a live session.

Could be space related, open up terminal (Applications -> Accessories -> Terminal) and enter this:

```
df -h
```

Post the output. That will list all mounted file systems and their size / space.

Other than that I'm not too sure, maybe a permissions issue on home?

```
ls -l /home/
```

Should show your user owns it like so..

```
drwx------ 75 nandemonai nandemonai 20480 2009-05-03 10:47 nandemonai
```

Good place to start.

---

### Post by nhasian on 2009-05-03
from your description of the problem is sounds like you dont have write permissions in your home directory.  open up a terminal and type:

```
cd /home
```

then to see the permissions for your home directory type:

```
ls -l
```

mine look like this:

> drwxr-xr-x 110 nasser nasser 4096 2009-05-02 19:06 nasser


also i took a screenshot of the permissions of my home directory if it helps you its attached.

---

### Post by Johnneylee on 2009-05-03
Maybe you set up your home directory some place other than the filesystem you installed Ubuntu on?

I guess nandemonai is asking the more pertinent question. Do you have the permissions set right?

---

### Post by Coatze on 2009-05-03
Now i'm wondering if I botched the install.  Due to firefox's quirks, I can't log in on the computer in question and I can't get into my email to copy it to myself.  But it df -h yields something along the lines of:
/dev/sda7 2.3g used 2.2g avail O mounted on /

There are others in the list, all fairly large and unused mounted to /lib/init/rw, /var/run, /var/lock, /dev, /dev/shm and an overflow which is the biggest by far, also largely unused...

But I'm thinking the first one might be my issued since it is mounted to the root it is defaulting to that for mozilla downloads.  and since my preferences aren't keeping, it won't let me change my save directory.  But why do I have room for package downloads (which kept, by the way)

Is it possible i somehow botched the install? Used the standard tool to do a side by side with windows, but according to the grub loader screen, I have multiple windows, both an XP home and a 95/nt/xp... is it possible it found it's way onto the wrong partition?

Oh and home is all mine.

And no worries.  You didn't sound condescending.  It just reminded me of something I'd say to mother when doing family tech support,  and she is hopeless.

---

### Post by Coatze on 2009-05-03
Crap, I am hopeless.   Realized I botched the install in the way suggested (if not other ways).  Doing a reinstall, hoping that somehow magically fixes everything else.

Thank you for all the help!!
Coatze

---

### Post by zvacet on 2009-05-03
Your root partition is to small.If you can make it ~10 GB you will not have problems.Also separate home will save your settings.If you didn´t make it that do it now following [this.]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

---

