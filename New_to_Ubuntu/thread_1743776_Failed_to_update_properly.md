---
title: "Failed to update properly"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by damnupdates on 2011-04-29
today i was prompted to upgrade from 10.10 netbook to 11.04. i let it it do its upgrade. I checked on it 2 hours later and i got an error that says 
```
[CENTER]Ubuntu 10.10
the disk drive for / (and /tmp)is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery[/CENTER]
```
this is not a dual boot system. i made ubuntu the only OS on the netbook. 
when i press S to skip it says:
```
Mountall: Plymouth command failed
Mountall: Disconnected from Plymouth
```

when i press M to recover it takes me to the shell.

---

### Post by cariboo on 2011-04-29
Does it take you to a busybox prompt or the regular console prompt? If you takes you to a regular console prompt, you may be able to fix your upgrade by typing the following command:

```
apt-get -f install
```

depending on if you are at a root prompt or just the regular prompt, you may have use sudo with the above command.

---

### Post by th1rt3en on 2011-04-30
I don't have a dual boot either, but I get the same message upon some boots.
I always just wait and it figures it out itself, however.
Does this error message go away if you leave it alone long enough?

Just a side note too, if all else fails you could try a clean install of 11.4.

---

### Post by damnupdates on 2011-04-30
> **cariboo907 said:**
> Does it take you to a busybox prompt or the regular console prompt? If you takes you to a regular console prompt, you may be able to fix your upgrade by typing the following command:

```
apt-get -f install
```

depending on if you are at a root prompt or just the regular prompt, you may have use sudo with the above command.

does not take me to a busybox prompt... just the maintenance one with M. S does nothing except what i stated. if i just wait for something to happen i get nothing still. 
when i load into M it takes me to maintenance shell and says
```
Root filesystem check failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@(myname):~#
```
and i typed the apt-get -f install and with sudo and it gives be the message
```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The Package lists or status file could not be parsed or opened.
```

---

### Post by damnupdates on 2011-04-30
dont know if bumps are aloud on these forums or if its against the rules... but bump

---

### Post by damnupdates on 2011-05-01
another bump

---

### Post by wep940 on 2011-05-01
Bumps are allowed - but only once every 24 hours.
 
Wish I could help with your problem !
 
Best of luck!

---

### Post by K_45 on 2011-05-01
Have you encrypted your HDD?

---

### Post by damnupdates on 2011-05-01
nope.

---

### Post by beew on 2011-05-01
Do a fresh install if you have had your important files backup. 

They should disable by default that stupid popup inviting you to upgrade. (It can be disabled by going to update manager and choose only notify distro upgrade when new LTS is available, don't remember if you can turn it off completely) This is a trap for inexperienced users. No one should do Os update/upgrade in a haste because of a prompt  from a popup (no testing, no research and no backing up the old system) And no one should upgrade/update their main systems on the first day of a new release!

---

### Post by damnupdates on 2011-05-01
were can i now find the netbook version of ubuntu? or is it now the same for all computers? my net book has 1g of ram

---

### Post by wep940 on 2011-05-02
It's all the same now.

---

### Post by pennysolucky on 2011-05-03
> **beew said:**
> Do a fresh install if you have had your important files backup. 

They should disable by default that stupid popup inviting you to upgrade. (It can be disabled by going to update manager and choose only notify distro upgrade when new LTS is available, don't remember if you can turn it off completely) This is a trap for inexperienced users. No one should do Os update/upgrade in a haste because of a prompt  from a popup (no testing, no research and no backing up the old system) And no one should upgrade/update their main systems on the first day of a new release!
 

I could not be greener if I were shot from a laser.  I, like damnupdates, fell into this trap and have run into the same error codes.  The computer I am using was inherited from a dear departed friend and much of his work is in there.  Luckily he backed up most of it on a couple of flash drives.  I am  gathering up the courage to do a fresh install.  Meanwhile I hope other less drastic measures prove successful.

I will be watching this thread with baited breath.  I have a question though.  What's a bump?

---

### Post by RobertVarga on 2011-05-03
I also saw that message and i just had to wait a little and he mounted the drive, system started properly. Happened two times and after not anymore.

---

### Post by Linux&amp;Gsus on 2011-05-03
> **pennysolucky said:**
> I could not be greener if I were shot from a laser.  I, like damnupdates, fell into this trap and have run into the same error codes.  The computer I am using was inherited from a dear departed friend and much of his work is in there.  Luckily he backed up most of it on a couple of flash drives.  I am  gathering up the courage to do a fresh install.  Meanwhile I hope other less drastic measures prove successful.

If you have a separate /home partition it's actually rather easy to do a fresh install without losing any of your data. I did that a couple days ago (for the first time), as well.
Usually I just upgraded or complete re-installed because I changed the the partitions, as well. But if you have a separate /home it's actually really easy to get your system back with all your data still in place.

Having said that, a backup is always vital to have. Not only when updating the system!


> **pennysolucky said:**
> I will be watching this thread with baited breath.  I have a question though.  What's a bump?

Bump is to basically write something (more or less) meaningless in ones thread, e.g. "bump", to bring the thread back up on the first page -> bump it up. Hoping that people would see it sooner and therefore answer quicker, compared to when the thread is going down to the 2nd, 3rd, 4th page.
--> Just imagine everyone would do that with their threads as soon as it moves to the 2nd page... I don't think it needs further explanation to imagine how that would look like. :D

---

### Post by damnupdates on 2011-05-03
i just did a completely fresh copy. i did backup all data before i upgraded because it seemed like it was a large up date... love skydrives. but i got every thing back and running. hope some one knows how to fix this for any one else that has this problem. would hate to see people loose there docs pics and other files because they forgot to do a backup. i was just hoping for i fix so i would not have to take the rout of installing a fresh copy.

---

