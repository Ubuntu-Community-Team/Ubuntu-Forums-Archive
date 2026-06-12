---
title: "Trimming the proverbial processes fat"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Green Growbot on 2011-07-19
I have been a user of Ubuntu for roughly a year now and, just to try something new, installed Xubuntu. I had noticed that Ubuntu had run very few processes which was great because for the moment I have a old computer with only 512MB of RAM. Never had any problems with memory when using Ubuntu but now that I installed this new OS it says I am running 119 processes on what is basically a new install.  Any simple tricks or a link on how I can "trim the fat" would be very much appreciated. Thank You

GG
  (Hardcore Ubuntu Loyalist)


P.S. cpu is a 1.7 GHZ intel--running at 16-25% currently.

---

### Post by MG&amp;TL on 2011-07-19
Err...does it tell you what said processes are? And what Ubuntu WERE you running? Older versions have less jobs...

Try:

```
top
``` in a terminal.

This will give you what's using what. :D

---

### Post by bodhi.zazen on 2011-07-19
> **Green Growbot said:**
> I have been a user of Ubuntu for roughly a year now and, just to try something new, installed Xubuntu. I had noticed that Ubuntu had run very few processes which was great because for the moment I have a old computer with only 512MB of RAM. Never had any problems with memory when using Ubuntu but now that I installed this new OS it says I am running 119 processes on what is basically a new install.  Any simple tricks or a link on how I can "trim the fat" would be very much appreciated. Thank You

GG
  (Hardcore Ubuntu Loyalist)


P.S. cpu is a 1.7 GHZ intel--running at 16-25% currently.

IMO, the easiest method by far is to do a minimal install and add only the applications you want / need.

---

### Post by MG&amp;TL on 2011-07-19
You could always try lubuntu...very light (MUCH lighter than Xu-), but a little lacking in terms of hardware compatibility, plug-and-play-ness, and general tools like a full office suite (I know it has gnumeric and AbiWord, but that IS really the bare minimum.)

Oh, and check "startup applications."

Ubuntu minimal install is good, but a SERIOUS learning curve (I'm working on it bodhi!) Unless you are terminal competent, have serious partitioning skills, and don't mind a couple of hours' work, it's probably not for you. And having wired internet is an advantage.

Have fun!

---

### Post by Green Growbot on 2011-07-19
op - 13:11:36 up  1:26,  2 users,  load average: 0.12, 0.15, 0.14
Tasks: 122 total,   3 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.3%us,  7.6%sy,  0.0%ni, 84.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    442020k total,   305392k used,   136628k free,    10456k buffers
Swap:   455676k total,     6176k used,   449500k free,   113736k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                
 1669 green     20   0  103m  11m 8236 R  7.3  2.8   5:20.82 xfce4-taskmanag                                                                                                        
 1056 root      20   0 43012  18m 7108 S  5.0  4.2   1:26.18 Xorg                                                                                                                   
 3203 green     20   0  117m  19m  10m S  3.3  4.5   0:04.24 xfce4-terminal                                                                                                         
 1218 root      20   0 16824 3136 2280 S  0.7  0.7   0:02.40 upowerd                                                                                                                
 1471 green     20   0  7016 1976 1348 S  0.7  0.4   0:04.64 xscreensaver                                                                                                           
 2784 green     20   0  357m  70m  29m S  0.7 16.4   0:31.89 firefox-bin                                                                                                            
  479 messageb  20   0  3380 1392  748 S  0.3  0.3   0:01.94 dbus-daemon                                                                                                            
 1496 green     20   0  100m 9636 6584 S  0.3  2.2   0:02.87 xfce4-power-man                                                                                                        
 2334 root      20   0     0    0    0 S  0.3  0.0   0:00.89 kworker/0:0                                                                                                            
    1 root      20   0  2920 1492 1092 S  0.0  0.3   0:01.43 init                                                                                                                   
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                               
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.97 ksoftirqd/0                                                                                                            
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.42 kworker/u:0                                                                                                            
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                            
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                                                                                 
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                                                
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                                                                                                                  
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.01 sync_supers                                                                                                            
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                                                                                            
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd                                                                                                            
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd                                                                                                                
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                                                 
   15 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify               


[B]

Im not sure if thats good enough or not. Damn thing keeps updating and un-highlighting the thing before I can copy it. If it needs straightened out for you Ill have to work a little gedit magic on it.[/B]
[B][I]
   As far as the version goes, unfortunately have no idea. I stupidly forgot to write the v. number on the disc.  Dapper Drake sounds right but I could very well be mistaken. Like I said though, it was about 1 year ago. I can tell you that runing idle there were 25 processes running on it so you might be right about it being an older version.[/I][/B]

---

### Post by Green Growbot on 2011-07-19
Of course im not able to use Compiz 3d or anything like that on here and I am semi-competent with the terminal I do enjoy doing some customizing so bare minimum probably isnt going to work for me.  Right quick though, how is it that you do a minimum install? (If you have the time, I dont mean to get to far off topic)

---

### Post by MG&amp;TL on 2011-07-19
WELL...bodhi can probably answer better than me...but I imagine he's very busy, he posts EVERYWHERE.

Anyway:

1. Burn 'minimal' cd.

2. Boot it.

3. Go through the 'pseudo graphical' installer. It asks all the usual questions. But is considerably harder to deal with, especially if you have wireless internet.

4. It will boot to a DOS-type prompt. You will then have to install things via 'apt-get'  I would suggest installing the desktop of your choice (i.e Unity, GNOME, LXDE, XFCE, KDE, GNOME 3...the list goes on. Your choice really.) Unless you WANT a command line, that is...

5. You then have Ubuntu...without anything installed. Install the stuff you want. If you've installed a compiz-friendly desktop, compiz settings should work out of the box. I've never actually got this far, but the theory is that you get a completely customised Ubuntu desktop. But it's HARD.

Go [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) HERE for minimal .iso

and [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) HERE for installation instructions. I imagine it's very easy if you take up the entire disk, and use wired internet.

I don't do either, so as you can imagine, it's difficult.

Have (LOTS!!) of fun with that. :P

---

### Post by Green Growbot on 2011-07-19
well what about the processes? Do you see anything there that can be removed or made inactive MG?

---

### Post by MG&amp;TL on 2011-07-19
Anything marked 'green' is you, I'm guessing. So any of that can go, but by the looks of things, that is literally just basic things like a web browser. Try chromium, that's a LITTLE lighter.

Ummm...I have to say, I've never liked Xubuntu after an infinite login>back to login screen loop problem. You could always try *up*grading to Ubuntu11.04. I have run it on the spec below, and it worked relatively fast. You could...try a re-install and hope that solves it, although tbh it looks like standard stuff there. Or (very carefully) see what happens if you remove some of the less-vital looking ones... :D.** although be warned, it may very easily break something or everything. A reboot may/may not solve it. It depends what you have to lose. Personally, I like breaking things to see how to fix them...but if you have documents...:(**

You can 'kill' a process by:

```
kill PID


```The PID is  the first coloumn in 'top' Just make sure you get the right one. _***And you have been warned about this. You may have to be sudo to do this. Not recommended if it's marked root.***_

---

### Post by Green Growbot on 2011-07-19
ok, illl take that all under advisement. If I go with ubuntu v 11.04 is there anything new that you can do or anything more accessible or fun to play around with or is it still that plain magenta background when it first starts and all the same stuff basically that they would have had 1 year ago? I have to say that the main thing I like about Xubuntu is the larger options on downloadable programs and games that they have over plain Ubuntu. Have they changed it in the new v of Ubuntu to be able to get the new stuff or are they still stuck with the usual?  Seems that there are many more choices with Xubuntu. Maybe thats just because I have the 11.04 v of X.???

Thanks for taking the time to walk me through all of this, everyone involved.

---

### Post by bodhi.zazen on 2011-07-19
> **MG&TL said:**
> WELL...bodhi can probably answer better than me...but I imagine he's very busy, he posts EVERYWHERE.

What makes you say that ?

> Anyway:

1. Burn 'minimal' cd.

2. Boot it.

3. Go through the 'pseudo graphical' installer. It asks all the usual questions. But is considerably harder to deal with, especially if you have wireless internet.

4. It will boot to a DOS-type prompt. You will then have to install things via 'apt-get'  I would suggest installing the desktop of your choice (i.e Unity, GNOME, LXDE, XFCE, KDE, GNOME 3...the list goes on. Your choice really.) Unless you WANT a command line, that is...

5. You then have Ubuntu...without anything installed. Install the stuff you want. If you've installed a compiz-friendly desktop, compiz settings should work out of the box. I've never actually got this far, but the theory is that you get a completely customised Ubuntu desktop. But it's HARD.

Go [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) HERE for minimal .iso

and [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) HERE for installation instructions. I imagine it's very easy if you take up the entire disk, and use wired internet.

I don't do either, so as you can imagine, it's difficult.

Have (LOTS!!) of fun with that. :P

Looks like you are doing just fine.

Trimming down (removing packages from a standard desktop) or building up both take knowledge, and a minimal install will teach you what you need to know fast with less breakage.

A nice guide is posted here:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

> **Green Growbot said:**
> well what about the processes? Do you see anything there that can be removed or made inactive MG?

Well, this is what the man pages are for ;)

As with windows, you should not go removing or killing processes you do not understand.

Here is the man page for kthread

[http://manpages.ubuntu.com/manpages/oneiric/man9/kthread.9freebsd.html](http://manpages.ubuntu.com/manpages/oneiric/man9/kthread.9freebsd.html)

Probably not something you want to kill simply because you do not understand what it is ;)

---

### Post by MG&amp;TL on 2011-07-19
Ummm...LOTS of things have changed since (whatever you're using-10.10 at the latest) was released. There's a new desktop. Unity. Some people love it, some hate it. It's got a sidebar at one end. Unfortunately, compiz is a pain in the a*** to get running under Unity. Plain old GNOME2 is still around though as a backup. (you can use compiz on this, but it'll most probably screw up Unity.)

The magenta background's changed (you mean the out-of-focus lens flare thing?) to well... more magenta lens flare. But anyway, you can edit that with things like 'Ubuntu tweak'. (software centre it). Improved compatibility for a lot of things. It's worth having, I think. If you really hate Unity, you can always fall back on GNOME, install GNOME3 (dodgy at the mo) or any of the other 'buntu desktops (LXDE, XFCE, KDE).

It may or may not help your problem, as it is more 3d graphics intensive. However, if you could run Ubuntu, but not Xubuntu, I suggest it is probably a Xubuntu problem, and therefore to at least try 11.04

Let us know how you get on. :)

---

### Post by MG&amp;TL on 2011-07-19
'What makes you say that ?'

My mistake. You just seem to be answering all my questions, and I find your posts everywhere if I search the forum for something. Therefore I assumed you were some sort of Ubuntu deity and would therefore be extremely busy.:D My apologies.

Yep, it's NOT a good idea to kill something, just because it's there. Stuff WILL break. Maybe permamently.

[SIZE=1](but a lot of fun to my twisted mind)

EDIT: I had never heard of the 'man pages' V.interesting !
[/SIZE]

---

### Post by Green Growbot on 2011-07-19
[B]10.10, thats the version that I had. I see now that you can update to 11.04 from there which is really nice ive still got 10.10 on my wifes computer so it looks like it is pretty easy to update with just a little bit of terminal use. I am for sure going to go with 11.04 and see how that goes.
   Obviously its always a good idea to back up the drive when upgrading an OS of any kind BUT if I upgrade on the wifes computer is she going to lose all of her stuff or does it just work around what you already have?[/B]

---

### Post by MG&amp;TL on 2011-07-19
In theory, you can upgrade VERY easily and without losing data. If it's important, I would back it up anyway, but it should be OK.

Go to update manager. Click 'settings' and then enter your password.

Find the 'updates' tab, and, at the bottom, set the drop-down for ubuntu releases to 'Normal' rather than 'long-term' Once that is done, hit OK.

Press 'check' on update manager, and a button should pop up saying that there is a new release available. Click that and you're going. It may take several hours depending on your computer, and the faster your internet, the better. If you're using dial-up I imagine it would take days.

---

### Post by MG&amp;TL on 2011-07-19
Why are some of your posts in **BOLD**? It is a little distracting...:D

---

### Post by Green Growbot on 2011-07-19
i dont have to bold them. i did it the first post so that I could direct 2 responses to 2 different people. Ive just been doing it since then so they get noticed. no biggie.

---

### Post by bodhi.zazen on 2011-07-19
> **Green Growbot said:**
> i dont have to bold them. i did it the first post so that I could direct 2 responses to 2 different people. Ive just been doing it since then so they get noticed. no biggie.

use the quote box ;)

---

### Post by Green Growbot on 2011-07-19
Will do bodhi, thanks for all the great info both of you and taking all the time to help me through it. Im going to get the U11.04 and give that a shot. Ubuntu is the one I am most familiar with by far anyways.

Thanks again.
GG

---

### Post by mikewhatever on 2011-07-19
While it's certainly possible to reduce the number of processes most any given system runs, I don't think it's necessary in this particular case. It seems that the idea of 'trimming' got started by the conviction that Ubuntu runs less then 119 (or very few) processes. That's not the case. Perhaps not all processes where shown the way you checked, but I'd bet Ubuntu has more then 119 processes runnig by default.
You can see all running processes with **ps aux**.

If you want to know how many - **ps aux | wc -l**.

Here is mine:
```
~$ ps aux | wc -l
150

```

---

