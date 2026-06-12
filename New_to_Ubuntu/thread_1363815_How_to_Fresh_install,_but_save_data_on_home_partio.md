---
title: "How to Fresh install, but save data on /home partion?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-12-24
My /home is a partion on my laptop But when i went to upgrade to 9.10 it dosent seem to have worked so im going to do a clean install to 9.04 again. I want to save my data which is on a seperate partion. which is /home. How will i install again but save this data. Please help.

---

### Post by taurus on 2009-12-24
Since you already have /home on a separate partition, you just tell the installer where to install it, /.  Then, don't forget to tell the installer to mount the partition where /home is to /home, but DO NOT format it or all your data will be gone.

And if you create the same username, then you can use the same $HOME with all your settings intact.

---

### Post by Rave Gloves on 2009-12-24
> **taurus said:**
> Since you already have /home on a separate partition, you just tell the installer where to install it, /.  Then, don't forget to tell the installer to mount the partition where /home is to /home, but DO NOT format it or all your data will be gone.

And if you create the same username, then you can use the same $HOME with all your settings intact.

I went to the installer and went to the manual partition selector. When i defined the partitions it said that sda2 would be formatted then all partitions would be formatted during install. Could you possibly talk me through how to tell the install where to install ubuntu?. Im on the live session so i can go onto the installer and still post.

---

### Post by taurus on 2009-12-24
There is a square box in front of the mount point.  If you put a check mark on that, the partition will be formatted.  And if there is no check mark, then it won't be formatted.  How many partitions do you have anyway?  Can you post a screenshot of it or with gparted.

p.s.  Which partition is /home?

---

### Post by Rave Gloves on 2009-12-24
When i was being shown how to set up the partitions i made 3, a 2gig swap. a 15gig dev/sda2 and a 220gig dev/sda3 which is the home. 

the types were both ext4 and the 15gig was mounted at /
and the 220gig was mounted at /home

when the installer comes up will i just mount them to the / and /home as they were before?

---

### Post by taurus on 2009-12-24
Yes.  Tell the installer to mount /dev/sda2 to / and format it.  Then, mount /dev/sda3 to /home (make sure you have the right filesystem, ext3 _or_ ext4, for /dev/sda3) but do not format that partition, preserving all your personal files on /dev/sda3.

---

### Post by raymondh on 2009-12-24
> **Rave Gloves said:**
> When i was being shown how to set up the partitions i made 3, a 2gig swap. a 15gig dev/sda2 and a 220gig dev/sda3 which is the home. 

the types were both ext4 and the 15gig was mounted at /
and the 220gig was mounted at /home

when the installer comes up will i just mount them to the / and /home as they were before?

In step 4, select MANUAL.  Then, you'll need to identify and click to highlight the specific partitions:

swap - mount as LINUX SWAP FILE SYSTEM
15gb - mount as / (root) and format to ext3 or ext4
220g - mount as /home.  DO NOT FORMAT

Make sure you use the same username and password as in the previous Karmic install.  You'll do this in step 6, I think.

EDIT : I type slow, again.

---

### Post by Rave Gloves on 2009-12-24
> **taurus said:**
> Yes.  Tell the installer to mount /dev/sda2 to / and format it.  Then, mount /dev/sda3 to /home (make sure you have the right filesystem, ext3 _or_ ext4, for /dev/sda3) but do not format that partition, preserving all your personal files on /dev/sda3.

Okay its installing now, hopefully it will work :). thanks for your help. I will mark are solved once its all installed :)

---

### Post by Rave Gloves on 2009-12-24
> **raymondh said:**
> In step 4, select MANUAL.  Then, you'll need to identify and click to highlight the specific partitions:

swap - mount as LINUX SWAP FILE SYSTEM
15gb - mount as / (root) and format to ext3 or ext4
220g - mount as /home.  DO NOT FORMAT

Make sure you use the same username and password as in the previous Karmic install.  You'll do this in step 6, I think.

EDIT : I type slow, again.

Aha, cheers for the reply anyway!. i did what you have typed and have used to same user and password. Also it said on the last step that The swap and the 15gig partitions were the ones that would be formated so im guessing it has worked properly (:

---

### Post by Rave Gloves on 2009-12-24
Everything is working again guys, cheers!

---

### Post by raymondh on 2009-12-24
> **Rave Gloves said:**
> Everything is working again guys, cheers!

Congratulations.

Happy holidays :)

---

