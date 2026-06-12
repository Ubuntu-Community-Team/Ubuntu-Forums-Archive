---
title: "waking up to a black screen."
date: 2009-12-25
forum: New to Ubuntu
---

### Post by soryu on 2009-12-25
when my pc wakes up from hibernating . i get the splash screen then  a black screen.
anyone know how to fix this?
Btw when i click suspend nothing happens.
i had a dual boot with XP both worked fine. ubuntu just had hibernate no sleep.
reinstalled ubuntu to whole disk. upgraded to 9.10 hibernating was working installed CCSM (needed NVIDIA driver) now black screen after waking up.:confused:
if i remove CCSM i think hibernating will work again
i like CCSM anything i can change to keep it?

---

### Post by JC Cheloven on 2009-12-25
CompizConfig Settings Manager is only a tool to configure compiz. But compiz itself is already there. So it's hard to believe that installing CCSM would affect the system in any way. 

A black screen means a shell prompt, I assume (?)

You say "Nvidia driver was required". So there wasn't one previously installed. The culprit may be an improper nvidia driver installed. This can indeed cause gdm to not start.

---

### Post by droadtrip on 2009-12-25
[FONT=Georgia][SIZE=3][COLOR=Navy]Try to reconfigure your system settings. Go to Power Management, change the part where you want to enable password upon wake-up, even if you don't care about the password to do so. Then change it back to what you want. Apparantly it seems like the system is confused about having you enter your password or not and that causes the black screen. See how this works. [/COLOR][/SIZE][/FONT]

---

### Post by NagWolf on 2010-01-06
Hi,
I also have a Dual Vista and Karmic setup. Everything work(ed) perfect, I didn't install anything like additional drivers or anything different from the standard Setup...
I tried the Hibernate function last night, Laptop seems to have shutdown completely instead of going into a lowpower state, now if I choose which kernel to boot from Grub, it just goes over to a blank page with a "blinking cursor" right at the top.
I hope this is something that can be fixed from the Console, is there a "Swap state" or Hibernate file that can be deleted somewhere to reset Karmic to just boot normal?

Thanx ppl

---

### Post by soryu on 2010-01-07
My PC Wakes Up Normally Now. I Sudo Configured My NVIDIA Driver Settings.
My Problem Now Is That My PC Doesn't Sleep, Just Hibernates.''


Uhh ,Don't Know If There Is a Way To Reset The Way Karmic Boot's.
 But If you Can. Someone Here Should Know.

---

### Post by NagWolf on 2010-01-09
This is supposed to work:
Do a normal installation again from the Installation CD/DVD of choice, go through all the normal steps as always, just don't mark the partitions to be formatted, this then gives you a "Repair" Installation...

If that fails, like in my case, do all the above, but just mark the /   partition to be formatted, which will leave all your personal settings in place, but all software (*see note) and system updates will be gone as done before you had to format.

* If your Partition planning included specifying a partition specifically for the " /usr " , from what I understand, most of your additional programs installed afterwards will also be safe in installed.

Hope I explained myself correct, if the Longbeards will correct me so another will avoid pitfalls, please do so, all I can say is that mine is working again, I just had to re-update my system again, 'cause I don't have all separate partitions defined
Cheers
:popcorn:

---

