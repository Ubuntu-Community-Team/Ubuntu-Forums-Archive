---
title: "what is killing my system ???"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by lightnin on 2009-04-30
I've just built a new box - amd phenom x4 2 gig ram

250gb hard drive 10 gig system 1 gig swap

some proccess is eating up my resorcess

hardware monitor show cpu levels up at 100 % sometimes when I have nothing going on

memory goes up to 98 %  and swap up to 100% then I am stuck and need to hard reset :(

I'll put some screen shots up in a sec

---

### Post by Dark Aspect on 2009-04-30
> **lightnin said:**
> I've just built a new box - amd phenom x4 2 gig ram

250gb hard drive 10 gig system 1 gig swap

some proccess is eating up my resorcess

hardware monitor show cpu levels up at 100 % sometimes when I have nothing going on

memory goes up to 98 %  and swap up to 100% then I am stuck and need to hard reset :(

I'll put some screen shots up in a sec

Ubuntu 9.04 I am assuming? Try another version of Ubuntu to see if the problem is still there. Are you using a UPS by any chance? I have heard that they causes this kind of problem on Linux but have never experienced it first hand.

---

### Post by kanikilu on 2009-04-30
Can you use **top** or **gnome-system-monitor** to see what it is that's using up resources? That'd be a good place to start...

---

### Post by lightnin on 2009-04-30
oh yeah - I'm running 9.04 64bit

I've loaded all my old packages from my old setup

tracker reports a corrupted index so I stopped that

[IMG]http://i121.photobucket.com/albums/o238/RichAAC-UK/Screenshot2.png[/IMG]

[IMG]http://i121.photobucket.com/albums/o238/RichAAC-UK/Screenshot1.png[/IMG]

once it's got to 98 / 100 % I cant take the scren shot ! - but those are the processes I'm running

HELP !!!!

:D

---

### Post by zzHanks on 2009-04-30
> **kanikilu said:**
> Can you use **top** or **gnome-system-monitor** to see what it is that's using up resources? That'd be a good place to start...

I think you mean htop (correct me if I'm wrong). Htop is much more accurate, system monitor itself takes a lot of process when viewing resources.

---

### Post by yeats on 2009-04-30
top is lighter on resources than htop or other top variants...

---

### Post by rhcm123 on 2009-04-30
> **lightnin said:**
> oh yeah - I'm running 9.04 64bit

I've loaded all my old packages from my old setup

tracker reports a corrupted index so I stopped that

<image snipped>

once it's got to 98 / 100 % I cant take the scren shot ! - but those are the processes I'm running

HELP !!!!

:D

accodring to the first image, dbus-daemon is using... **1.2 GIGABYTES OF RAM** :shock:. Well, there's your problem. Mine's only sucking 700 Kb.
This may be a hardware/software glitch between your system and the messaging dameon, or, more likely, it was this bug reported to launchpad regarding memory leakage, and you can read that [here.]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/295741")

This may be a bad idea, so I would wait for the community to back me up on this, but you can *try* to kill the process. If you can, pull up the system monitor, then read the process id for dbus (it was 3981 in the screenshot you provided), then run the following command in the terminal:

```
sudo kill -SIGHUP <pid>

```

EDIT: Also, would you mind clicking the "memory" column label, that will order processes using the most memory first, so we can see in comparison to other processes on your PC (or if this problem is bigger than we thought).

---

### Post by kanikilu on 2009-04-30
> **zzHanks said:**
> II think you mean htop (correct me if I'm wrong). Htop is much more accurate, system monitor itself takes a lot of process when viewing resources. No I meant **top**, I actually prefer **htop**, but it's not installed by default, hence my suggestion to use the former...

To the OP: I'm not really sure what it could mean, but dbus-daemon is taking a paltry 1MB of memory on my machine, and it's eating up over a gig on yours :confused:

---

### Post by rhcm123 on 2009-04-30
> **rhcm123 said:**
> 

EDIT: Also, would you mind clicking the "memory" column label, that will order processes using the most memory first, so we can see in comparison to other processes on your PC (or if this problem is bigger than we thought).

Just to show you what i meant, i want something like the attached pic.

---

### Post by lightnin on 2009-04-30
ok , I installed Htop

dbus and tracker were using the most cpu, so I killed tham and the usage stopped, but the memory is frozen at around 750 /1986mb



so ... what is dbus thingy (i'll read that bug report in a sec :)  )

and can I uninstall the tracker ?

---

### Post by rhcm123 on 2009-04-30
> **lightnin said:**
> ok , I installed Htop

dbus and tracker were using the most cpu, so I killed tham and the usage stopped, but the memory is frozen at around 750 /1986mb

so ... what is dbus thingy (i'll read that bug report in a sec :)  )

and can I uninstall the tracker ?

memory may just be leftovers from the processes that you killed - that won't go away until you reboot, or if thats the total usage, then that is normal - im using about 700, including swap (and i cut some stuff out of the default install). dbus is the system message bus - thats why i said it wasn't the best of ideas to kill it, but if your still working then there should be no problem.

What tracker are you having a problem with?

---

### Post by lightnin on 2009-04-30
the processes are trackerd and tracker-indexer(or indexing) I forget, I'll reboot and come back :)

when I 1st boot, I get a tracker appear in the top task bar - then an error - corrupt index , then an error loop on cancel, so I quit tracker with the right click, but it still shows on the system monitor

back in a min :)

---

### Post by rhcm123 on 2009-04-30
> **lightnin said:**
> the processes are trackerd and tracker-indexer(or indexing) I forget, I'll reboot and come back :)

when I 1st boot, I get a tracker appear in the top task bar - then an error - corrupt index , then an error loop on cancel, so I quit tracker with the right click, but it still shows on the system monitor

back in a min :)

i have no clue what tracker is - i don't really use 9.04, despite my signature - could you provide a screenshot?

---

### Post by lightnin on 2009-04-30
ok - the tracker is this one 
[http://projects.gnome.org/tracker/](http://projects.gnome.org/tracker/)


I rebooted

pulled up htop and sys mon

all was ok - then tracker came up with the error prompt and cpu went up to 97/100% on all 4 !

since then, system is sort of behaving (but it's only been a minute)

---

### Post by lightnin on 2009-04-30
I've just removed tracker with the package manager

gonna re-boot and see......

---

### Post by rhcm123 on 2009-04-30
> **lightnin said:**
> ok - the tracker is this one 
[http://projects.gnome.org/tracker/](http://projects.gnome.org/tracker/)


I rebooted

pulled up htop and sys mon

all was ok - then tracker came up with the error prompt and cpu went up to 97/100% on all 4 !

since then, system is sort of behaving (but it's only been a minute)

Ok, i guess i do use tracker then, I thought this was referring to the new 9.04 error tracker (and i was wondering what would happen if the bug report system was buggy :) ). Tracker is the searching/indexing system for GNOME, and its just close enough to useless as you can get. It's a bloated front end to the locate command, and you can shut it off with System ->  Prefrences -> Search and Indexing.

However, the fact that it's encountering problems may indicate a larger problem with your filesystem. If you still have your liveCD, can you boot it and use it to check the disk (not particularly nessecary, just a thought.)

---

### Post by lightnin on 2009-04-30
> **rhcm123 said:**
>  If you still have your liveCD, can you boot it and use it to check the disk (not particularly nessecary, just a thought.)

It wouldn't hurt I guess .

my system is behaving after the reboot tho.

maybe the tracker got confused when I copied my 32bit home directory over on top of my 64 bit home directory ???

I would love to know more about linux ! but no time ... :(

trouble with ubuntu is - it just works !  so you never get to learn , apart from the odd hickup

---

### Post by rhcm123 on 2009-04-30
> **lightnin said:**
> It wouldn't hurt I guess .

my system is behaving after the reboot tho.

maybe the tracker got confused when I copied my 32bit home directory over on top of my 64 bit home directory ???

I would love to know more about linux ! but no time ... :(

trouble with ubuntu is - it just works !  so you never get to learn , apart from the odd hickup

It may have been that - that could corrupt your index... come to think of it, you may have damaged the index. You should read up on this, see if there is away to rebuild the index. (Or just reinstall, if your really lazy, to one of the less-buggy versions, such as 8.04 or 8.10

---

### Post by lightnin on 2009-04-30
lol ! I'm sure 9.04 will be ok soon :)

I'll mark this solved for now and check my disk / re-install tracker and try and learn a bit !

thanks for your help :)

Rich

---

### Post by rhcm123 on 2009-04-30
> **lightnin said:**
> lol ! I'm sure 9.04 will be ok soon :)

I'll mark this solved for now and check my disk / re-install tracker and try and learn a bit !

thanks for your help :)

Rich
 i think that the solved plugin has been deleted indefinently :(

---

### Post by lightnin on 2009-04-30
> **rhcm123 said:**
> i think that the solved plugin has been deleted indefinently :(


haha ... that's why I cant find it then !

---

