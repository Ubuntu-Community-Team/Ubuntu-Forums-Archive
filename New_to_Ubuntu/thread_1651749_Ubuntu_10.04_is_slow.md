---
title: "Ubuntu 10.04 is slow"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by opetrenko on 2010-12-23
After **[painful ]("http://ubuntuforums.org/showthread.php?p=10272839")**installation my Ubuntu 10.04 alternate (all defaults) is up 
and running.
But *much *slower compared to XP. GUI actions taking XP 1-2 sec require 10-20s from Ubuntu. What was seamless in XP make me wait for a couple of secs with "Visual Effects" set to "None" 

System monitor shows CPU at 99%-100% busy, 
of which gnome-system-monitor is taking 14-16%
vino-server 5-8%
The rest processes are shown at 0% and "Sleeping"

[B]1. How 16+8 = 100 ?
[/B]**2. Are there any ways to speed up Ubuntu?, or it's usually slower then Windows?**

system:
P4 1.6GHz
750MB RAM

Ubuntu 10.04 (lucid)
Kernel Linux 2.6.32-26-generic
GNOME2.30.2

Thank you for taking time reading this and your advise.

---

### Post by sikander3786 on 2010-12-23
Applications > Accessories > Terminal, please post the output of top while your PC is acting slow.

```
top
```

And which graphics card is there?

```
lspci | grep VGA
```

Ubuntu is usually faster than Windows. Don't yet know why you are getting those problems.

---

### Post by sve$hnikov on 2010-12-23
Hi! i have the same thing also with my ubuntu 10.10 is slower
my ram:512
graphic card = Vanta Vanta lt NV6
what's the probleme
what we can a do :D

---

### Post by sikander3786 on 2010-12-23
> **sve$hnikov said:**
> Hi! i have the same thing also with my ubuntu 10.10 is slower
my ram:512
graphic card = Vanta Vanta lt NV6
what's the probleme
what we can a do :D
What is Vanta Vanta lt NV6? Never heard of that graphics card before???

With 512MB RAM, it might be a bit slow.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

What are your outputs for these commands?

```
top
```

```
free -m
```

---

### Post by sve$hnikov on 2010-12-23
top
--
top - 23:12:20 up 10 min,  2 users,  load average: 1.20, 1.28, 0.81
Tasks: 143 total,   2 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s): 19.1%us,  4.3%sy,  0.0%ni, 75.6%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:    508424k total,   501540k used,     6884k free,   121556k buffers
Swap:   261116k total,       40k used,   261076k free,   181248k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                        
 1157 root      20   0 42020  22m 7060 R 18.2  4.4   1:16.66 Xorg                           
 2273 jbr       20   0 90116  13m  10m S  6.0  2.7   0:03.30 gnome-terminal                 
 2296 jbr       20   0  2624 1112  832 R  0.7  0.2   0:00.25 top                            
 1370 jbr       20   0 99324  10m 8428 S  0.3  2.2   0:02.44 gnome-settings-                
    1 root      20   0  2892 1636 1168 S  0.0  0.3   0:00.64 init                           
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                       
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.16 ksoftirqd/0                    
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                    
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                     
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.06 events/0                       
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                         
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                        
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                          
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                      
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                             
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                    
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default
-----------------
free -m

             total       used       free     shared    buffers     cached
Mem:           496        487          9          0        116        176
-/+ buffers/cache:        193        302
Swap:          254          0        254

---

### Post by Hur Dur on 2010-12-23
Have you tried using a different desktop environment?

I recommend LXDE, which you can get by typing in:

sudo apt-get install lxde

If that still isn't optimal for you, try just using a window manager. Fluxbox, JWM, and IceWM* are well known for being light and fully functional. 

sudo apt-get install fluxbox
sudo apt-get install jwm
sudo apt-get install icewm-lite

*Note: I am not sure if all of these are in the repository. If not, you will need to get them manually. 

If you still have performance problems, you could try lighter Ubuntu-based distros like Bodhi Linux, or Lubuntu.

---

### Post by sve$hnikov on 2010-12-23
i reinstall ubuntu 
now is work fine no probleme
so what is the the job of LXDE
what he do ?? ;)

---

### Post by opetrenko on 2010-12-23
"top" showed completely different picture. 
Why would system monitor be hiding something?

[IMG]http://dl.dropbox.com/u/4703812/testdisk_screenshots/top.png[/IMG]


the video card is:
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
[]("http://dl.dropbox.com/u/4703812/testdisk_screenshots/top.png")

THANKS!

---

### Post by davidmohammed on 2010-12-23
> **sve$hnikov said:**
> i reinstall ubuntu 
now is work fine no probleme
so what is the the job of LXDE
what he do ?? ;)

lxde, fluxbox etc are the graphical front ends to linux.  These are generally much more simpler that the standard front ends KDE or GNOME i.e. use less RAM and hence are faster on memory constrained systems like yours.

With 512MB of RAM - you should really try lxde or fluxbox etc.

Note - the graphics card is important - you can see much better speed improvements if we know what it is

please type

lspci | grep VGA

and copy and paste the output in a reply.

---

### Post by sve$hnikov on 2010-12-23
i' so happy with this solution thanks men
this is the result of the command
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
my graphic card i think very lower 16 mb
:D i will try the LXDE thanks

---

### Post by davidmohammed on 2010-12-23
> **opetrenko said:**
> "top" showed completely different picture. 
Why would system monitor be hiding something?

[IMG]http://dl.dropbox.com/u/4703812/testdisk_screenshots/top.png[/IMG]


the video card is:
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
[]("http://dl.dropbox.com/u/4703812/testdisk_screenshots/top.png")

THANKS!

several people have reported the "100% backend" process issue.  Dont know what the real issue is.  However, you should be able to kill the process without any issues

sudo kill -9 <processid>

in your picture this would be

sudo kill -9 10122

---

### Post by amjjawad on 2010-12-23
Great, two users in one thread having the same issue?

Anyway, this is confusing so my answer will be general not specific. I'm not going to answer both :)

When you say slow, could you please define slow?
I'm running Ubuntu 10.04 on 448MB RAM and it's still MUCH more faster than Windows XP.
If we're talking about few seconds here ... so what?
If your RAM is FULL (all being used) then ... again ... so what? if you are NOT going to use ALL your RAM then this is a great waste indeed.

That slowness might be because of something else but definitely not Linux/Ubuntu.

I have installed Linux (Mint Fluxbox 9) on a 12 years old laptop with 64MB RAM and 366MHz P2 and ... it's still faster than XP.

People should not panic if it's few **seconds **slow or the RAM is all being used.

That's my humble opinion :)

---

### Post by sve$hnikov on 2010-12-23
thanks for your reply
but what you do to make it faster
??:D

---

### Post by amjjawad on 2010-12-23
> **sve$hnikov said:**
> Hi! i have the same thing also with my ubuntu 10.10 is slower
my ram:512
graphic card = Vanta Vanta lt NV6
what's the probleme
what we can a do :D

Your version of Ubuntu is not the same as the OP's version.
Your RAM is less than the OP's RAM.

This is in my opinion two different cases having the same output.

---

### Post by sve$hnikov on 2010-12-23
thanks so whats the solution??

---

### Post by davidmohammed on 2010-12-23
Myself and Hur Dur already gave you a solution...

---

### Post by madjr on 2010-12-23
just wanted to mention, that the more you use XP, the slower it gets (virus, malware, spyware, registry  problems / garbage, etc.). and the software for daily maintenance, sometimes can break your system, like it happen a few times to myself.

Now, with ubuntu/linux , is the other way around, the more you use it the better, the speed either doesn't get affected or actually gets a bit faster with updates.

as for the OP, check you SWAP partition size. Make sure is big enough.

also, you can see all processes by ticking "**All processes**" in the system monitor menu.

and last, if you guys need lighter distros for your older hardware, you can always check:
[http://blog.linuxmint.com/?p=1523](http://blog.linuxmint.com/?p=1523)
[http://blog.linuxmint.com/?p=1505](http://blog.linuxmint.com/?p=1505)
[http://puppylinux.org/](http://puppylinux.org/)

---

### Post by amjjawad on 2010-12-23
> **sve$hnikov said:**
> thanks so whats the solution??

So you have your own thread [[http://ubuntuforums.org/showthread.php?t=1651758]](http://ubuntuforums.org/showthread.php?t=1651758]) and you hijack someone's else thread?

Please, use ONLY one thread which you already started.
Posting in someone's else thread will confuse everybody including you!

Thanks for your understanding.

---

### Post by opetrenko on 2010-12-23
> **amjjawad said:**
> Great, two users in one thread having the same issue?

...

When you say slow, could you please define slow?
...

People should not panic if it's few **seconds **slow or the RAM is all being used.

That's my humble opinion :)

Please, let me know what kind of definition of *slow *you're looking for. I think I was quite specific.

Regarding a "few seconds": 
I'm used to work fast, not holding a mouse button down, so comp finally gets that I'm clicking "OK" button.  These "few seconds" is like talking with a person who makes a few seconds pause between words. Give it a try. 

My RAM is used ~30% of 750MB when nothing but system monitor is running.

davidmohammed: I'll try. Thanks

---

### Post by amjjawad on 2010-12-23
> **madjr said:**
> as for the OP, check you SWAP partition size. Make sure is big enough.


If my calculation is correct then he/she already has almost 2GB Swap Partition and his/her RAM is 750MB.
That's more than enough IMHO.

---

### Post by sve$hnikov on 2010-12-23
so i install the LXDE 
it's done i restart my computer
and i see no change in the desktop is it like that the LXDE
??
:D

---

### Post by opetrenko on 2010-12-23
madjr: Thanks!
The swap is about x3 times RAM of 750MB
RAM is used about 30% when nothing is running

---

### Post by davidmohammed on 2010-12-23
> **sve$hnikov said:**
> so i install the LXDE 
it's done i restart my computer
and i see no change in the desktop is it like that the LXDE
??
:D

... you should really start another thread since your issue is quite different.

Logout - on the login screen at the bottom is a session drop-down.  Select lxde from there.  Then login again.

---

### Post by amjjawad on 2010-12-23
> **opetrenko said:**
> Please, let me know what kind of definition of *slow *you're looking for. I think I was quite specific.

Regarding a "few seconds": 
I'm used to work fast, not holding a mouse button down, so comp finally gets that I'm clicking "OK" button.  These "few seconds" is like talking with a person who makes a few seconds pause between words. Give it a try. 

My RAM is used ~30% of 750MB when nothing but system monitor is running.

davidmohammed: I'll try. Thanks

I think we're talking apples and oranges here.
If your 750MB RAM is 30% used it doesn't mean anything bad or wrong in my humble opinion.

Your output of "top" doesn't even show that your whole RAM is being used.

---

### Post by davidmohammed on 2010-12-23
> **opetrenko said:**
> madjr: Thanks!
The swap is about x3 times RAM of 750MB
RAM is used about 30% when nothing is running

30% when doing nothing looks correct.  Did killing backend fix the high CPU usage?

---

### Post by madjr on 2010-12-23
> **sve$hnikov said:**
> so i install the LXDE 
it's done i restart my computer
and i see no change in the desktop is it like that the LXDE
??
:D

in the login screen you can choose lxde.

or try [http://lubuntu.net/](http://lubuntu.net/) (which might actually have a few extra tweaks)

else install "lubuntu-desktop" to get them.

---

### Post by opetrenko on 2010-12-23
davidmohammed:
I killed it and that process is gone. 
however CPU is still at 100%

[IMG]http://dl.dropbox.com/u/4703812/testdisk_screenshots/slowUbuntu/SysMonGauge.png[/IMG]

I guess I have just to get used to it. 

here are the results of top and processes snapshot in sys monitor. 

[IMG]http://dl.dropbox.com/u/4703812/testdisk_screenshots/slowUbuntu/top2.png[/IMG]

[IMG]http://dl.dropbox.com/u/4703812/testdisk_screenshots/slowUbuntu/SysMon.png[/IMG]

Thank you!

---

### Post by amjjawad on 2010-12-23
> **opetrenko said:**
> davidmohammed:
I killed it and that process is gone. 
however CPU is still at 100%


[http://ubuntuforums.org/showthread.php?t=1642561](http://ubuntuforums.org/showthread.php?t=1642561)

---

### Post by opetrenko on 2010-12-23
amjjawad
Indeed it was thumbnails that were hogging CPU

Turning them off in a folder explorer ( Edit->Preferences->Preview tab )
fixed the problem after restart. 

Now, if nothing is running CPU is at 30%. And comp is much more responsive. 
Thank you

---

### Post by amjjawad on 2010-12-24
> **opetrenko said:**
> amjjawad
Indeed it was thumbnails that were hogging CPU

Turning them off in a folder explorer ( Edit->Preferences->Preview tab )
fixed the problem after restart. 

Now, if nothing is running CPU is at 30%. And comp is much more responsive. 
Thank you

Anytime :)
Glad it's working much better now. If the problem is solved, please mark this thread as "SOLVED" for future reference :) I mean others will know how did you fix it and follow the same steps.

If you have any other question, please don't hesitate to ask.

There's a facebook's page in my signature ... try to check it out because it has tons of useful links.

---

### Post by mastablasta on 2010-12-24
> **opetrenko said:**
> "top" showed completely different picture. 
Why would system monitor be hiding something?

 
It's not hiding it just doesn't funciton too well :-).
 
> 
the video card is:
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
 
 
I think bad drivers for this card might be the issue here. this card is in legacy support as it uses opensource drivers designed by community. ATI dropped support for this card and you can send them a thank you note for that. :-)
the only solution would be to find a testing version of those. maybe something could also be done on configuration side, but i am not well versed in that. otherwise they are a hit or miss. sometimes (with some cards) they run fantastic. othertimes not good at all.
 
> **davidmohammed said:**
>  
With 512MB of RAM - you should really try lxde or fluxbox etc.

 
 
And you base this on what? Minimum requirements on Ubuntu documentation site are not really accurate. Xubuntu is supposedly running well on 256MB ram. but guess what? i am running GNOME well on 224MB ram (10.04). Upon boot it takes up about 120 MB ram.graphical instaltion was with no issues. So 512MB should be more than enough to run it. even the 10.10 edition. and it should run faster than windowsXP on the same amount of RAM.
 
OK LXDE would be even faster but i don't think it's necessary to abandon a more mature and better supported (by applications) GNOME in this case.

---

### Post by amjjawad on 2010-12-24
> **mastablasta said:**
> And you base this on what? Minimum requirements on Ubuntu documentation site are not really accurate. Xubuntu is supposedly running well on 256MB ram. but guess what? i am running GNOME well on 224MB ram (10.04). Upon boot it takes up about 120 MB ram.graphical instaltion was with no issues. So 512MB should be more than enough to run it. even the 10.10 edition. and it should run faster than windowsXP on the same amount of RAM.
 
OK LXDE would be even faster but i don't think it's necessary to abandon a more mature and better supported (by applications) GNOME in this case.

I do agree with you that Ubuntu will run even faster than XP with less than 512MB RAM but still we need to stick with the information on the official site.

I've never imagined how fast Linux could be until I installed Mint Fluxbox 9 on P2 with 64MB of RAM.
I'm planning now to reduce the RAM on my 2nd PC by sharing half of it (I have 512MB) as a Graphics Memory. It means, Ubuntu will use 256MB only. I can't wait to see how fast it will be :D

---

### Post by sve$hnikov on 2010-12-24
so LXDE is bad than Gnmoe in appication and programs??
what i can do in gnome to make her more faster ?
:D

---

### Post by amjjawad on 2010-12-24
I increased the shared RAM for my Graphics Card and my RAM is **256MB** for Ubuntu.

My machine is P4 @ 3.00GHz - 1M L2 Cashe
Physical RAM is 512MB. 256MB for the Graphics Card.
It took 1 min and 25 seconds from power on to a functional Desktop.
It should be faster but my PC for some reason is talking so much time on checking whether there's a CD to boot from or not. So, I guess it's 1 min only.

---

### Post by sve$hnikov on 2010-12-24
how you increase it ?

---

### Post by amjjawad on 2010-12-24
> **sve$hnikov said:**
> how you increase it ?

Just ignore that. It's between me and mastablasta ;)

If you have built-in Graphics Card, it will take some of your RAM. I made it 50:50 and Ubuntu is still fast like nothing happened.

---

