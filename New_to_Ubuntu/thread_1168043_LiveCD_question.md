---
title: "LiveCD question"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by hellothere2 on 2009-05-23
So I am running Ubuntu off of the CD, choosing the option that says something to the effect of try ubuntu without any changes to your computer.

It's really cool, but I have a quick question:

I wanted to configure the settings so they were like this:

[http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0)

I downloaded compiz, atlantis, etc.  

But now what?  Should the system update automatically?  Do I need to do something?  Or is this simply not possible to do off of the CD?

I'm asking this because the screen still looks exactly the same.

Thanks!

---

### Post by whoop on 2009-05-23
System-->Preferences-->Appearance-->Visual effects. Try to select extra. What kind of graphics card do you have?

---

### Post by hellothere2 on 2009-05-23
> **whoop said:**
> System-->Preferences-->Appearance-->Visual effects. Try to select extra. What kind of graphics card do you have?

No clue.  But thanks; I'll try this.

Also, these effects will go away once I restart the computer anyways, correct?  IOW, there is no way to permanently save stuff while running ubuntu off the cd, is there?

---

### Post by utnubuuser on 2009-05-23
forget running off' the CD. Run: System>>Administration>>Partition Editor.

Select the right-most partiton by clicking on it, the select >>Move/Resize

Grab the right-hand handle of the partition, slide it to the left until you've freed up 5gigs, click apply.

Now go to the desktop and double-click on the "Install" icon, and when you come to the partitioning screen, select the option that says: Guided - use largest continuous free space. 

continue through the installation steps, (be sure to import your Windows settings/folders), and in about 15 minutes you'll be able to set any kind of preferences you want.
**_(NOTE:)_**
**Unless you're running Vista, in which case resizing a partition is only to be done with a Vista disk**

---

### Post by Tibuda on 2009-05-23
The Live CD has a low performance and is for testing only. You can't save your settings unless you install ubuntu in your computer.

---

### Post by whoop on 2009-05-23
> **danielrmt said:**
> The Live CD has a low performance and is for testing only. You can't save your settings unless you install ubuntu in your computer.

I think you can install anything you want on the livecd, as long as you don't need to reboot and don't run out of memory.

---

### Post by overdrank on 2009-05-23
> **hellothere2 said:**
> No clue.  But thanks; I'll try this.

Also, these effects will go away once I restart the computer anyways, correct?  IOW, there is no way to permanently save stuff while running ubuntu off the cd, is there?

You may also choose [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

