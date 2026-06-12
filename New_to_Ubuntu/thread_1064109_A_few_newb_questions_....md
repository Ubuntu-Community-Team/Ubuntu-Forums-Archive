---
title: "A few newb questions ..."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by xlns on 2009-02-08
Hello, people!

Yesterday, I finally made the Step : I installed Ubuntu 8.10 executing my decision not to have any illegal software on my PC. I am not proud of hosting such software, but that's the way it was. Now, as a new linux user, I ask for help from anyone who knows how to solve any of my problems.

I had some experience with linux before, but not much : I tried a Slackware distribution ... like a 10 years ago. I know how to cp an entire directory around and was able to write a small chat daemon, but that's about it. I'm telling you about it so you may know how newb really am I. Be gentle. =)

Ah, the problems ... well, most of them I think I could solve easy if there wasn't of one unfortunate circumstance ... bla, bla, bla, I don't have my DSL ( or any other Internet access for that matter ) and it ain't going to be around quick enough. Now, I'm running on somewhat slower network: I take my memory stick and go to a public PC =)

First of all ... err ... I kinda didn't care to make a swap partition while installing OS . What is default root password for ubuntu 8.10 ? I already tried love, secret, sex and god =) I menaged partitioning with sudo, but I fear that some default root password may compromise my security online.

Is there a way to enable use of Alt+(ASCII Number) under linux? I have a keyboard without greater/less(60/62) symbols and it's driving me mad when I need to make a for loop :-/ Is there a way to hack around this or ... ?

I am bit concerned about GUI speed. For example, in Gnu chess figures movement animation are irregular and slow. I installed cq3 ( open sourced client for cpma/quake3 ) and it runs at 1 fps , although I believe it to be a round-off error. It feels like 1/3 fps =) True, I have a slow PC (AMD Athlon XP @ 1,1GHz, GF 5500 FX and 0,5 GB RAM ), but cq3 is running at solid 120 fps under win32. I will install non-free drivers tonight, but is there anything else I should look at? Off the top of your head? 

I noted in Help/Advanced topics/C and C++ that there are two "popular development platforms" for graphical development. What exactly does this mean? If I write an application for GNOME, how much work is to cast it to run under KDE or any other desktop environment?

Many thanks in advance!

---

### Post by halitech on 2009-02-08
by default the root account is actually disabled so everything is done with sudo which you are a member of by default as the first user.

Some will claim you have an "old and slow system" and you should consider puppy linux or DSL as they are better suited for "old" systems. Personally, unless you need a rescue system or are travelling and using anothers computer, I wouldn't touch either. You may want to consider Debian with XFCE instead of even Xubuntu. I've run Debian+XFCE for awhile now and was even able to get it running on an old P266 with 96meg of ram. 

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by howlingmadhowie on 2009-02-08
> **xlns said:**
> 
First of all ... err ... I kinda didn't care to make a swap partition while installing OS . What is default root password for ubuntu 8.10 ? I already tried love, secret, sex and god =) I menaged partitioning with sudo, but I fear that some default root password may compromise my security online.

The default root password is some complicated random string. but it's not important because ubuntu uses a command called sudo. by default, your first user is allowed to use sudo. you use it like this:

```
sudo <command>
```
and then it will ask for your password. then the command will be carried out as if root issued it. you can also get a root shell by typing:
```
sudo -i
```
and entering your password.

> 
Is there a way to enable use of Alt+(ASCII Number) under linux? I have a keyboard without greater/less(60/62) symbols and it's driving me mad when I need to make a for loop :-/ Is there a way to hack around this or ... ?

under gnome you can enter unicode characters by entering ctrl-shift-U and a number, for example 
```
ctrl-shift-U 0 0 3 c
``` or just
```
ctrl-shift-U 3 c
``` will give <

> 
I am bit concerned about GUI speed. For example, in Gnu chess figures movement animation are irregular and slow. I installed cq3 ( open sourced client for cpma/quake3 ) and it runs at 1 fps , although I believe it to be a round-off error. It feels like 1/3 fps =) True, I have a slow PC (AMD Athlon XP @ 1,1GHz, GF 5500 FX and 0,5 GB RAM ), but cq3 is running at solid 120 fps under win32. I will install non-free drivers tonight, but is there anything else I should look at? Off the top of your head? 

that's almost certainly the drivers. ubuntu has a driver installer for non-free drivers, but you need an internet connection for that. i think you can still install the latest nvidia drivers manually, but best to search through the forum a bit for advice.

> 
I noted in Help/Advanced topics/C and C++ that there are two "popular development platforms" for graphical development. What exactly does this mean? If I write an application for GNOME, how much work is to cast it to run under KDE or any other desktop environment?


you'd have to rewrite the GUI code, however almost everybody has libraries for gtk (gnome) and qt (KDE) installed, so that shouldn't be necessary. qt (in particular the newest version---qt4) is also pretty cross-platform.


lots of fun! i'm sure you'll do fine :)

you may want to search around for a quick beginner's tutorial for ubuntu, just so you can learn about some of the basic differences between ubuntu and other gnu/linux distributions.

---

### Post by Mud.Knee.Havoc on 2009-02-08
Forget everything that you remember about linux from 10 years ago.  It's light years ahead of where it was back then. :)

It should be quite easy to get your DSL up and running with linux.  I've got a router that handles my PPPOE settings, so it's set up automatically for me.  Even if you don't have a router (which you really should have, even for the added security), it's not a big deal.

You'll get used to not having a root account with Ubuntu.  At first, I couldn't get my head around it - now I definitely prefer it.  Just use sudo (gksudo in some cases, if you're running something graphical) and you're good.

---

