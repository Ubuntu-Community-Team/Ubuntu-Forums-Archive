---
title: "Copying and Pasting Commands in Terminal Question"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-18
Hello everyone,

Following a guide by **aysiu** on creating a separate home partition in Ubuntu, below is directed:

*************************************************************************

names to the ones appropriate for your setup):
[B]sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda3 /new
[/B]
Now we're going to back up the /home directory on the old partition and move it to the new partition:
[B]cd /old/home
find . -depth -print0 | cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home[/B]

Yes, one of those lines looks really complicated—so please copy and paste the commands into the terminal instead of retyping them.

**************************************************************************

**Question**: Does each line need to be pasted and entered independent of the others, one line at a time, or can each group of lines, (4 each), be pasted and entered in terminal together all at once? 

I am guessing each line, one at a time, must be entered in terminal, before the next line.

Thank you.

---

### Post by Schendje on 2009-08-18
You can do them all at once, it'll do it in that order. :)

---

### Post by Troll_the_Great on 2009-08-18
I am (almost) sure you should copy and paste them one by one...

---

### Post by mikodo on 2009-08-18
hmm... Two different responses!

---

### Post by whitethorn on 2009-08-18
I suggest you do each command / line seperately, if something doesn't work at least you'll know how far you got.  Since you are mounting partitions it might be a good idea to make sure the numbers (sda1,2,3) match with those on your pc.

---

### Post by mikodo on 2009-08-18
> **whitethorn said:**
> I suggest you do each command / line seperately, if something doesn't work at least you'll know how far you got.  Since you are mounting partitions it might be a good idea to make sure the numbers (sda1,2,3) match with those on your pc.


I see, to be careful and be able to diagnose problems, one line can better see difficulties as commands progress.

And yes, I will follow your advice in being careful with the numbers, as you also pointed out.

Thank you everyone.

---

