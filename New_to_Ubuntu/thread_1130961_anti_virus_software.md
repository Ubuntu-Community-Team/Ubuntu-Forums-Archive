---
title: "anti virus software"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by lane1075 on 2009-04-20
hi absolute beginner at ubuntu is there any anti-virus software already installed?  also need to download software updates but keeps on asking for password everything i have tried doesnt work how can i re-set a password?

---

### Post by aeiah on 2009-04-20
very few people bother with antivirus software for ubuntu. linux is inherantly more secure than windows, and also has hardly any viruses. i would say no viruses at all, but then some smart-*** will chirp in with some case study that found one or something. basically you may want to use antivirus if you deal with windows computers so you dont accidentally send on an email containing a windows virus, but this virus won't affect you its self. if you want to use antivirus, then have a look at clam-av

your other problem seems more worrying though. your root password should be the same as your initial user password. the user you set up initially when installing ubuntu. do the usual check of making sure capslock is off etc

---

### Post by muteXe on 2009-04-20
It's the password you chose when you installed Ubuntu.
Search for clam av in the repo's for antivirus.  I think avg do a linux version of their software as well.

---

### Post by Hyper Tails on 2009-04-20
I recommend clamtk or avast.

choose which one you'll like
I have Clamtk

---

### Post by MysticGold04 on 2009-04-20
I use Avast Anti-Virus on my Ubuntu machines only because I have a network with Windows machines attached.  Generally no need, but I like to be on the safe side.

---

### Post by Hospadar on 2009-04-20
As above, clamav would be the software to use.  That said, viruses for linux are very rare, on top of things being relatively secure in general (although that's not to say linux is invincible, **all** software has holes in it, and you should still use smart computing practices)

If you want to use clamav, there are some graphical frontends for it, although in all honesty I think it's more straightforward to run it from a command line.

I run a clam av scan on my internet-exposed server once a week and have yet to detect a single virus (it's been running since the fall), so I think you're probably pretty safe.  Certainly a once-weekly scan is probably plenty.

Also note, clam av (even the linux version) will detect and inform you of known viruses for *all* OS's.  So if you by chance download a windows virus, although it won't do anything on linux, it's always nice to know and delete these sorts of things.  (this is because a lot of people run clam av or similar stuff on mail and web servers which may serve content to windows/osx machines)

---

### Post by john stiles on 2009-04-20
Do not forget pass words are case sensitive in Linux.
Avast is a good anti virus for windows converts as it shares the same interface.

---

### Post by lane1075 on 2009-04-20
thanks for the anti virus info well helpful, ok next problem a bit trickier then what if i cant find out what my password is?

---

### Post by john stiles on 2009-04-20
It sounds as if you have just installed for the first time. You gave a user name and password, but no longer have it. Why not simply install again, obviously taking greater care at the username and password screen this time.

---

### Post by marco123 on 2009-04-20
> **lane1075 said:**
> thanks for the anti virus info well helpful, ok next problem a bit trickier then what if i cant find out what my password is?

It's the password you logged in with.:)

Cheers, Marco.

---

### Post by john stiles on 2009-04-20
Backup any data you added quickly, before logging off.

---

### Post by atomizer on 2009-04-20
you can change your password in recovery mode (option when you boot)


look at this [howto]("http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/")

---

### Post by XubuRoxMySox on 2009-04-20
I installed clamav, I *think*, but it isn't listed under Applications. So I ran the install again through Symantic Pkg Mgr. Still nothing shows up. How do I know if I even *have* Clamav? - And if I do, how do I run it?

Sorry, total n00b, but loving my Ubuntu!!

-Robin

---

### Post by Celauran on 2009-04-20
> **dixiedancer said:**
> How do I know if I even *have* Clamav?

```
ps aux | grep clam
```

> **dixiedancer said:**
> And if I do, how do I run it?
Either run clamscan manually, or set it up as a cron job. 'man clamscan' for options.

---

### Post by Paqman on 2009-04-20
> **dixiedancer said:**
> I installed clamav, I *think*, but it isn't listed under Applications.

You've been led slightly up the garden path on that one. They should have told you to install clamtk, which is clamav plus the GUI interface to use it with. If you install clamtk now it'll show up.

A good way to avoid this problem is to use Add/Remove instead of Synaptic. Add/Remove doesn't show all the command-line only apps that are in Synaptic.

---

### Post by XubuRoxMySox on 2009-04-20
Here's the output I got back afterwards:

```
clamav    4578  0.0  0.2   3268  1348 ?        Ss   05:56   0:00 /usr/bin/freshclam -d --quiet
robin     7023  0.0  0.1   3240   804 pts/0    S+   12:29   0:00 grep clam
```

Um, does that mean I have it? Does it mean I have to go to /usr/bin/freshclam to use it?

I'll get it sooner or later, LOL

-Robin

---

### Post by Celauran on 2009-04-20
Freshclam is what keeps the virus definitions up to date. The -d indicates that it's running as a daemon.

---

### Post by XubuRoxMySox on 2009-04-20
> **Celauran said:**
> Freshclam is what keeps the virus definitions up to date. The -d indicates that it's running as a daemon.

Sorry to be so totally ignorant, but it sounds like my computer needs an **exorcism** or something! What's a daemon? Nothing like a demon, I hope.

I hope it means it's running "in the background" just doing it's little thing and doesn't need any manual input from me. If that's what a daemon is, then wow, cool, call off the exorcism!

-Robin

---

### Post by Celauran on 2009-04-20
Yes, it means it's running in the background.

---

### Post by XubuRoxMySox on 2009-04-20
Oh, how very cool! Got it, thanks. So I guess the daemon is doing the updates (because I'm not "root" ordinarily and don't want to be!) automatically. It would tell me if it's out of date, wouldn't it? 

Oh, LOL, I'm pro'lly making all this harder than it needs to be. It's just that I share the network here with abuncha Windows machines and want to be nice to them...

I guess it's all working fine now. Thanks!

By the way - **AVAST** was much easier to install, update, and run, but I like the idea that Clamav detects viruses for *all* operating systems, not just Windows

-Robin

---

### Post by MrWES on 2009-04-20
> **dixiedancer said:**
> Sorry to be so totally ignorant, but it sounds like my computer needs an **exorcism** or something! What's a daemon? Nothing like a demon, I hope.

I hope it means it's running "in the background" just doing it's little thing and doesn't need any manual input from me. If that's what a daemon is, then wow, cool, call off the exorcism!

-Robin

A Linux daemon is a kin to a Windows service. It generally loads at boot time. FYI, freshclam, by default, checks for updates once per hour = 24 times a day.

Bill

---

### Post by XubuRoxMySox on 2009-04-20
> **MrWES said:**
> A Linux daemon is a kin to a Windows service. It generally loads at boot time. FYI, freshclam, by default, checks for updates once per hour = 24 times a day.

Bill

Thanks, Bill! Hope my ignorance is amusing instead of irritating! I don't mind being laughed at a little... I expected it when I started something totally new to me. 

Daemons are good little guys to have around! Thank you very much.

-Robin

---

