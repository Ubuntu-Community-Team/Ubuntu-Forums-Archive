---
title: "Disk utility needed (for Dell 1520)"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by blueghoti on 2010-04-27
One of the reasons I migrated to Ubuntu 9.10 is because I suspected my Vista install could no longer handle what I assumed to be a bad sector.

Ubuntu flagged a problem on my disk - well two problems.  One was temperature (it was overheating) and the other was a single bad sector.  Everything else seemed fine.

When I accepted all the available updates / patches the other day the disk warning message disappeared, so I am really not sure where I stand.

Is there a good disk utility I can install to run a full scan and get a positive confirmation one way or the other if I have a problem?  If there's a problem, can Ubuntu just ignore it and work around any faults?

Thanks!
Chris

---

### Post by QLee on 2010-04-27
Generally the major manufacturers have a downloadable disk utility made for their specific drives, that's one. Dell is going to use one of the majors in their boxes.

[QUOTE=blueghoti] If there's a problem, can Ubuntu just ignore it and work around any faults?[/QUOTE]

Generally, it can.

You might want to run a fsck on the Ubuntu partition with a live CD (you don't want the partition to be mounted when you do the check).

---

### Post by philinux on 2010-04-27
> **blueghoti said:**
> One of the reasons I migrated to Ubuntu 9.10 is because I suspected my Vista install could no longer handle what I assumed to be a bad sector.

Ubuntu flagged a problem on my disk - well two problems.  One was temperature (it was overheating) and the other was a single bad sector.  Everything else seemed fine.

When I accepted all the available updates / patches the other day the disk warning message disappeared, so I am really not sure where I stand.

Is there a good disk utility I can install to run a full scan and get a positive confirmation one way or the other if I have a problem?  If there's a problem, can Ubuntu just ignore it and work around any faults?

Thanks!
Chris
System>admin>Disk utility has had the S.M.A.R.T feature disabled due to falsely reporting bad sectors for some users. While that is rectified try this.

Install gsmartcontrol from synaptic.

---

### Post by blueghoti on 2010-05-02
Thanks guys.

Philinux, I tried that app but ran into a "failed to execute child process error".  I did some digging and found this [https://bugs.launchpad.net/ubuntu/+source/gsmartcontrol/+bug/477652](https://bugs.launchpad.net/ubuntu/+source/gsmartcontrol/+bug/477652) which recommends executing this command (see reader comments) 

sudo aptitude install menu

That worked, the app launched and is running now - thanks again for your help!

Chris

---

### Post by no2498 on 2010-05-02
now stop the over heating turn off the computer
open the case look at the heat sink, fans
unplug and remove the power pack open it clean it fan and all
a new carpet can kill a computer
keep a bare arm on the case at all times
plug every thing back in leave the case open restart it look at all the fans make sure they are running close the case

hope this helps

---

### Post by blueghoti on 2010-06-01
Hi no2498 - 

Sorry about the delayed reply.  I was waiting to buy a new hdd and figured I would do everything at once when I had the computer open to replace the drive :-)

I checked - indeed, lots of dust.  Incredible!  I've blown all that out, but it seems that the fan has a problem with it.  The fan will spin ok - i.e. if I blow hard at it, you can see it move.  However, I think the power might be shot as it doesn't work on its own.

Is there a way to use Ubuntu 10 to diagnose what the issue might be, or is this purely a hardware issue that I need to address?

Thanks for your help!
Chris

---

