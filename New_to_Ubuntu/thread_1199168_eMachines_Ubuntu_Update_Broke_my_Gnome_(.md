---
title: "eMachines Ubuntu Update: Broke my Gnome :("
date: 2009-06-28
forum: New to Ubuntu
---

### Post by logmau on 2009-06-28
Hi,

We just bought an eMachines EL1200 on AMD Athlon 64., it was nice & cheap (£209) and so was a good machine to dip our toes in the Linux ocean... It came out of the box, "Ubuntu Certified" with version 8.04 installed.  FYI manufacturer sticker says it was made on 2008-10-16.

So we fired it up and connected to the net with no problems, then Update Manager appeared and suggest we download the latest updates - 170+ of them.  Having been used to Windows doing this to us we thought we may as well just let it.  This took over a day to download and install, with no intervention from us.  All seems fine except that the Administration rights have disappeared in Gnome and the "Unlock" button hangs for 15 seconds or more then says "Error cannot authenticate".  So although we still seem to have admin rights we can't create or delete users or unlock the Users & Groups admin boxes.

There is at least on post about that, "200634" on launchnet.com and one unsolved query on Gnome (523366 on bugzilla.gnome).  The guy who reported it says the problem went away with a Gnome update (our install left us with Gnome 2.22.3).  So what should we do now?  We're on 8.04 plus latest patches loaded from Ubuntu, so:

A). it seems that if we try to update Gnome we risk breaking the rest of Gnome on this install - so should we cut our losses and upgrade to 8.1 or 9.04? 
B). ...or should we try to upgrade Gnome...?

So advice please: if A, which version of Gnome do we go for? if B, should we go for 8.1, 9.04 (32) or 9.04(64)?  and would we risk losing special eMachine hardware drivers in doing so?

FYI, we had a RAM upgrade when we bought the machine so it now has 2.5GiB.

Any advice, gratefully received!

---

### Post by starcannon on 2009-06-28
Go again with 8.04, I'm not sure what happened during your updates, but I think 8.04 is the easiest to learn along with.

After your install is complete, it may be a good idea to set the upgrade manager to only grab LTS upgrades; and, be sure the update manager is ticked to check everyday. Your first boot will have a bunch of updates required; but, once done its only a few here and there.

Update Manager Settings are located in:
System>Administration>Software Sources

There is a "getting to know you" phase when one switches Operating Systems; so, try not to get discouraged. Once you know how, I think you will find computing in Ubuntu GNU/Linux to be very enjoyable.

GLAHF

---

### Post by pastalavista on 2009-06-28
I was wondering what kind of Ubuntu disk came along with an OEM installation and how it is configured to start up. (and if there was any crap-ware added). 
If you hit escape at the first boot screen, you can access the grub menu. I'm sure 8.04 has upgraded the kernel a time or two by now (I use 9.04 and it's kernel has been upgraded twice already), but you may be able to access previous kernels in grub. Boot with one of them and see if it helps your problem. My current kernel no longer supports my graphics card. Sometimes we just wait for a fix. The devs always come through eventually.

---

### Post by logmau on 2009-06-29
Hi,

Hmm, we don't have the System>Administration>Software Sources option on the machine..!  This is worrying, I thought older versions were supposed to be at least a *bit* stable and yet it seems the auto updates have fouled it up twice already.    Also, tried download a later version of Gnome but the download time is estimated at 3 days!?! Again its weird, the Ubuntu 9.04 downloaded in < an hour so its not my machine/connection.

I guess the complete re-install is beckoning.

---

### Post by pastalavista on 2009-06-29
The same menu is in System >Administration >  Synaptic Package Manager under the 'Settings' tab. There are several other tools in Synaptic you could try such as dependency search and broken packages.
The reference for this list is /etc/apt/sources.list which may also be edited.

---

