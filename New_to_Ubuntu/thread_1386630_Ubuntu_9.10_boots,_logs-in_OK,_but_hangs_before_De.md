---
title: "Ubuntu 9.10 boots, logs-in OK, but hangs before Desktop"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Obob on 2010-01-20
Hi,  This is my first post, and as a rank amateur have some hope that this is a simple problem (but right now it is driving me crazy).  It seems similar to a problem [described here (and SOLVED) two weeks ago by cpedwards]("http://ubuntuforums.org/showthread.php?t=1370554&highlight=login+fails+after+Ubuntu+logo+before+Desktop"):

> I'm running 9.10 and recently updated to kernel 2.6.31-16-generic (using update manager). At first it was fine but yesterday it refused to boot (the logo appears, the splash screen starts (with the progress indicator moving across the screen), then just hangs there before the login screen (the hard disk light stays on) and it justs sits there like that until I force it off by holding the power button for a few seconds. I've retried several times with same result.That is an exact description of my problem (except that my kernel is 2.6.31-17*).  Other differences are that booting from earlier kernels (-15 & -14) give the same result, while cpedwards could get into his home directory by booting from an earlier release (i.e. -16 -- I didn't have -16 in my set of retained kernels).  Ultimately, he solved his problem by installing -17.  That kernel clearly isn't working for me.   I can see my (hopefully) intact home directory using a command line login (via Ctrl-Alt-F2) but want a GUI back.

I should say that I installed 9.10 over two months ago and it has been working very well until this problem came up.

A possible clue is that the GUI logon screen comes up with three boxes at the bottom of the screen: 

**Language** *unspecified*    **Keyboard** *USA*    **Sessions** *Failsafe GNOME*

If I click on the *unspecified* it reveals *other* and selecting that I get a selection window that I presume should contain many languages to chose from but it is empty. (??)

I would be extremely indebted to anyone who might suggestion ways out of this.  I'll keep reading, but I haven't a clue right now.  Thanks - Obob:(

---

### Post by cariboo on 2010-01-21
It sounds like you have a video card problem, what graphics card/chipset does your computer have?

---

### Post by Obob on 2010-01-21
Thanks for the speedy reply! 

> It sounds like you have a video card problem, what graphics card/chipset does your computer have?The video chipset is an onboard "VIA unichrome pro"  (on a Jetway mini-ITX with VIA C7 cpu -- about 16 mo old by now.)  

However, I don't believe the problem is with the video because, I have found since in my initial post that like [cpedwards]("http://ubuntuforums.org/showthread.php?t=1370554&highlight=login+fails+after+Ubuntu+logo+before+Desktop") I also have a second account that opens *more or less* as expected to a fine Ubuntu desktop with **Applications Places System** in the top bar.  I say "more or less" because it also opens with a window that says:

> [Somewhat paraphrased] Update folders to current language?  You have loged in in a new language. You can auto update the names of some folders in your home folder to match this language. The update would change the following folders ... /home/obob/Desktop  /home/obob/Downloads.I've resisted the urge to follow this advice because I fear that it might lead to the trashing of my obob login in the same way my **/home/first** (root accessible) login has been trashed.  I have no rational reason to think this but as it stands, the obob login provides a way to more easily rescue data from my **/home/first** account -- if push should come to shove.

It seems I have lost - or something traumatic has happened to - my language files.  Does it make sense that this is the cause of my **/home/first **login failure?  Or has some configuration file that specifies language as well as other settings been trashed?  I just don't know where to look.

Thanks again for your help,  Obob :confused:

---

### Post by Obob on 2010-01-21
Looking over my previous posts, I think I should restate the problem:

I'm running 9.10 and following a bad shutdown my computer refused to completely boot -- the logo appears, the splash screen starts with the progress indicator moving across the screen, and the login screen appears with two accounts: **first** & **obob**. When I attempt to login to the **first** account I am prompted for a password, the password is accepted, splash screen continues with the progress indicator moving across the screen, and then the progress indicator disappears leaving the splash screen (looks like a spotlight shining down on the ground.)  And there it sits, until I force the computer to shut off by holding the power button down for a few seconds. I've retried this several times with the same result.

If, however, I select the **obob** login the computer accepts the password and things proceed as described above *and* following the spotlight shining on the ground, the Desktop is displayed, at which time the following message opens in a window:

> [Somewhat paraphrased] Update folders to current language? You have loged in in a new language. You can auto update the names of some folders in your home folder to match this language. The update would change the following folders ... /home/obob/Desktop /home/obob/Downloads.  _Keep new language_  _Change language_I have always selected the keep new language button for the reasons stated in my last post. I haven't spent a lot of time in **obob**, but it appears to be "normal" except for the initial "language" message. (Can create files with names that are in English)

I have quite a bit of date in the **first** account, and, being first, it is also the account that can issue superuser commands and must be functional to maintain the machine.  Can anyone help me get it back?  I would really appreciate your suggestions.

Hope that I have stated my problem more clearly this time. -- Obob :???:

---

### Post by rogue_0111 on 2010-01-21
A note: my version of 9.10 at the time was an upgrade from 9.04.

I had a similar issue a few weeks ago. I tried booting to the Ubuntu CD and replacing the "xconf" file but no dice. 

Since I was unable to recover I copied my files to an external and did a fresh install of 9.10. No issues since then.

---

### Post by Obob on 2010-01-21
Thanks Rogue,  don't know anything about "xconf" but looking around I conclude it is for graphic config.  I should emphasize that my screen does not go black but freezes on the splash screen.  Also, I can login as a second user with fine graphics, so I don't think it is a video problem.  I realized that I didn't state the problem clearly in the first post, so restated it, it would seem, while you were writing your post.  Your final solution will work for me, I'm sure, but I'd like to avoid it if possible.  And I'd like to know what happened. -- Obob

---

### Post by rogue_0111 on 2010-01-23
> **Obob said:**
> Thanks Rogue...Your final solution will work for me, I'm sure, but I'd like to avoid it if possible.  And I'd like to know what happened. -- Obob

Sometimes the easy way is the best solution. It saves you some sanity:) and possibly a marriage or girlfriend/ boyfriend.

---

### Post by Miljet on 2010-01-23
Your reasoning seems sound, however it is the first time I have heard of languages getting changed. You might try to take a look at System -> Administration -> Language Support and see what language it shows. You can also try to change it from there if required. 

I think that I would make sure that all my data files were backed up before making any changes just in case it really goes sour.

---

### Post by Obob on 2010-01-24
Thanks Rogue & Miljet! 

Once I looked more closely at /home/**first** it was clear that the setup there had sustained major damage with about 40 unreadable "dot" files/directories. The reinstall seemed to fix them, but I'll have to spend some time to find out. 

Rogue, your advise was good -- double thanks!

I finally gathered my courage, spent most of a day backing-up my  more cherished files (about 200 GB) and then reinstalled 9.10.  All went smoothly, and though I haven't had enough time yet to say for certain, I looks as if everything important is still there.  I'll report later if my setup was recovered intact (I would doubt it), but if not, a good house-cleaning was long overdue, so, I'm philosophical about any lost configurations, etc. 

I'm really impressed with how Ubuntu handled this "recovery" (so far, anyway). -- Obob

---

