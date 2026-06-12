---
title: "idle disk spin down blocked by webmin and other I/O"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Bradburts on 2011-09-04
Hi,
I am trying to get my disks to spin down when idle.
I have managed to get hdparams.conf to work and can also configure spin down from the command line using[FONT=Courier New] sudo hdparam -S 120[/FONT]
[FONT=Courier New][FONT=Verdana]The drives spin up every hour or so. [/FONT][/FONT]
[FONT=Courier New][FONT=Verdana]Q) Is there a command which shows total accumulated I/O such that I can leave the system running and then find who has written? Something like top but showing accumulated I/O rather than snapshot.[/FONT][/FONT]
 
[FONT=Courier New][FONT=Verdana]The second problem is that I have now installed webmin  (yes I know that I shouldn't & there may be issues!) and samba.  Since that install the hard drives will not spin down.[/FONT][/FONT]
Using iotop I find that that webmin updates [FONT=Courier New][SIZE=2]/etc/webmin/miniserv.conf [/SIZE][/FONT][FONT=Courier New][FONT=Verdana]every 20 seconds or so. I also see updates from [FONT=Courier New][SIZE=2]jbd2/dm-0-8[/SIZE][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana]. [/FONT][/FONT]
 
[FONT=Courier New][FONT=Verdana]I have tried to mount root with noatime guessing that webmin periodically reloads configuration and this would otherwise causes a disk write. However changed root to noatime and the writes still happen.[/FONT][/FONT]
Q) Can I configure webmin to stop doing whatever to the configuration (or reduce the rate)?
 
I don't know how I would stop samba writting to [FONT=Courier New][SIZE=2]browse.dat[/SIZE][/FONT], this is not so frequent but is often enough to wear my disks unless sorted, any ideas? 
Finally what is the [FONT=Courier New][SIZE=2]jbd2/dm-0-8[/SIZE][/FONT] process doing?

---

### Post by Bradburts on 2011-09-05
oops, wrong forum, moving.....

---

### Post by atca on 2011-09-05
keen to hear the solution here

---

### Post by Bradburts on 2011-09-06
Hi,
So am I!
I closed this question and reraised in the regular forum as its not a newbie question.

---

