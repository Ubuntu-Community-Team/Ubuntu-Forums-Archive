---
title: "Two versions of Ubuntu installed.."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by theglowpt2 on 2009-09-20
I have two different versions of Ubuntu installed on my older IBM ThinkPad..

The reason for this is due to my frustration with not being able to get the internet working on the first installation (and other general problems) of Ubuntu.

So in order to fix the problem I simply re-installed a new version of Ubuntu.  This has solved my internet issue as well as some other basic problems I was having.

My problem now is that I'm running out of space on my laptop and I want to remove the first version of Ubuntu that I installed.  I tried to do this when I installed the second version, but I was not able to.

Any suggestions?

Thanks!

ps im a complete noob with Ubuntu

---

### Post by elliotn on 2009-09-20
format the partition with older version

---

### Post by elliotn on 2009-09-20
ahh gparted would do u some gr8 work

---

### Post by callumacrae on 2009-09-20
I would suggest just deleting the partition with the first installation on.

Boot up in 2nd installation
Install GParted
Delete first partition
Move free space onto second installation partition

I've never done this, but I think this should work (or mess up your computer, make a backup first)

Hope it helps,
~Callum

---

### Post by ajgreeny on 2009-09-20
Callumacrea nearly got it right, except that you will need to do it with your Ubuntu live CD.

Boot into the live CD, open System-Administration-partition Editor, (gparted) and in that delete the partition with your original install on it, and also the swap partition, if both installs have a separate swap.

Now as you are using the live CD you will be able to add space from the old partition(s) to your new current one, but as has been said, make sure you back up first, just in case everything goes wrong.  There is no real reason why it should go wrong, of course, but better safe than sorry.

---

### Post by theglowpt2 on 2009-09-20
i'm really bad with Ubuntu to be honest. Still trying to understand how to do everything.

for some reason i can't get gparted to work.

---

### Post by theglowpt2 on 2009-09-20
also, thanks for the feedback everybody..

i don't have the patience for using gparted (i'm just not getting it)
is there any other easy way to get rid of the other Ubuntu?

sorry for the lack of knowledge.

---

### Post by brookie on 2009-09-20
gparted is really not that hard to use. it just takes some time. Here are a couple of totorials: 

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/) 

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

...by the way, gparted resizing partitions does take some time so go get a pot of coffee or turn on the baseball game while you wait.

---

### Post by callumacrae on 2009-09-20
> **ajgreeny said:**
> Callumacrea nearly got it right, except that you will need to do it with your Ubuntu live CD.

Boot into the live CD, open System-Administration-partition Editor, (gparted) and in that delete the partition with your original install on it, and also the swap partition, if both installs have a separate swap.

Now as you are using the live CD you will be able to add space from the old partition(s) to your new current one, but as has been said, make sure you back up first, just in case everything goes wrong.  There is no real reason why it should go wrong, of course, but better safe than sorry.

Ah yes, I thought that... :)

I just did this on my test computer and its really simple.

The instructions above are about as simple as they can get, and I don't think there is any other way of doing it. Except from deleting everything and starting again, which would just be stupid.

~Callum

---

### Post by theglowpt2 on 2009-09-20
I don't have a Windows cd. 
Would these instructions still apply?

---

### Post by slakkie on 2009-09-20
You don't need a Windows CD for gparted.. Also, be aware of changing UUID's of your partitions. If that happens, you need to change your /etc/fstab file as well.

---

### Post by ajgreeny on 2009-09-20
You won't need a windows CD.  Just use the ubuntu live CD for gparted, delete the original ubuntu partition(s) but make sure you do not do anything to the windows partition.

After you have done all this it is just possible that you may need to edit the /boot/grub/menu.lst file to point to the ubuntu partition, but this will only be needed if the disk's UUID has changed, which I don't think will happen when you simply enlarge it, though I could be wrong.

---

