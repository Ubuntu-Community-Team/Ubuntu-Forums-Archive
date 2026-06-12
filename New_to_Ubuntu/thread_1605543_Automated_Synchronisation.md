---
title: "Automated Synchronisation"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Ghostlove on 2010-10-25
Hi there, I'm a long-term Ubuntu user who fled to Windows 7 for a while because I was lured in by the shiny and my need to sync my iPhone using Windows. Now I'm dual-booting and using Ubuntu as my main OS again (only using Windows for iTunes and Lightroom).

Anyway, on to my question. I had a fabulous programme in Windows called Allway Sync that backed up all my files to my external hard drive. I'm looking for a similar programme in Ubuntu. The main criteria are that it needs to be able to be set up to do automated synchronisations (Allway Sync did it every day at a time I set) and the ability to propagate deletions (i.e. if I have deleted something on the source disk, it will also delete it on the external hard drive).

Does such a piece of software exist for Ubuntu? At the moment I am trying out 'luckyBackup' which seems perfect aside from that it doesn't seem to do automated syncs. 

If there is not a piece of software available that will do what I need it to, is there a way of making luckyBackup run its synchronisations at a certain time each night?

Thanks in advance for any help! :)

---

### Post by cstudent on 2010-10-25
I do something similar using [gadmin-rsync]("http://gadmintools.flippedweb.com/index.php?option=com_content&task=view&id=51&Itemid=38").

---

### Post by cstudent on 2010-10-25
And it's available in the repos using synaptic btw.

---

### Post by Ghostlove on 2010-10-25
I've downloaded that and it looks great, thanks! I'm trying to save the backup though and it's giving me the error: "Error: The time schedule server "cron(d)" does not seem to be running." Any idea what that means?

---

### Post by CaptainMark on 2010-10-25
you could use symbolic linked folders and then write a script to run a sync anytime you want

---

### Post by Ghostlove on 2010-10-25
> **CaptainMark said:**
> you could use symbolic linked folders and then write a script to run a sync anytime you want

That just went straight over my head I'm afraid (that's why I put this in Absolute Beginner Talk!). :P

---

### Post by CaptainMark on 2010-10-25
a symolic link is where you have a folder that mirrors another folder, for instance one on your hdd and one on usb to mirror it, then a script is a small program that can run commands like at a set time, update one folder into another. 
ps, i just noticed your location, hey neighbour

---

### Post by cstudent on 2010-10-25
I get that error too but the backup actually runs. A little bug I suspect. You can test by scheduling a backup a few minutes ahead and wait for it to run. Then check the log and destination directory.

---

### Post by ArgusVision on 2010-10-25
It might be a little late, but I just bookmarked a page on that today. 

[http://blogs.techrepublic.com.com/10things/?p=895](http://blogs.techrepublic.com.com/10things/?p=895)

---

### Post by Ghostlove on 2010-10-26
> **cstudent said:**
> I get that error too but the backup actually runs. A little bug I suspect. You can test by scheduling a backup a few minutes ahead and wait for it to run. Then check the log and destination directory.

You're right - I set it for 1am and it seems to have run when I told it to, so that's good! Thanks for your help. :)

---

### Post by Ghostlove on 2010-10-26
> **CaptainMark said:**
> ps, i just noticed your location, hey neighbour

Hi! *waves*

---

