---
title: "Making Ubuntu Partion Bigger"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by akrchstn on 2009-05-01
I just installed a 20 gig Ubuntu partion using wubi and in a few days I was wondering if I could just make the partion bigger so it takes up the whole HD instead of re-installing ubuntu to take up the whole HD.

EDIT:  After I first installed a restricted driver thing popped up but I closed it, is there any way I can bring that up again without restarting?

---

### Post by Niniel on 2009-05-01
Sure you can; GPartEd is your friend (System/Administration/Partition Editor).
Best use a Live CD for this though, since it won't work on mounted disks. With a live CD, you can unmount your hd prior to working on it.

---

### Post by test_test_testing on 2009-05-01
**EDIT:** should've read the OP's post a bit more carefully :D (ignore below)

> **akrchstn said:**
> I just installed a 20 gig Ubuntu partion using wubi and in a few days I was wondering if I could just make the partion bigger so it takes up the whole HD instead of re-installing ubuntu to take up the whole HD.

Wubi creates a virtual hard-drive (actually just a file) on your Windows partition, therefore its size is limited by the size of your Windows partition.

As for resizing, there should be some kind of shortcut on your desktop that's like "resize/transfer virtual disk" or something, that allows you to either resize or move to its own partition. I took this route quite a while ago, but can't remember the precise details. :)

---

### Post by beastrace91 on 2009-05-01
To bring up restricted hardware drivers goto system -> administration -> hardware drivers

~Jeff

---

### Post by pastalavista on 2009-05-01
For the hardware driver thing, go to System > Administration > Hardware Drivers

---

### Post by drs305 on 2009-05-01
Unless something has changed in wubi, you can't resize the file once you have installed it. You can use LVPM to move your wubi install/allow you put things elsewhere or you can move your /home to another location. 

Here is a link to the wubi wiki:
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by akrchstn on 2009-05-01
Meh, I'm only waiting until May 12th to fully install ubuntu.  Right now I guess I'll just get back into the groove of ubuntu.

---

