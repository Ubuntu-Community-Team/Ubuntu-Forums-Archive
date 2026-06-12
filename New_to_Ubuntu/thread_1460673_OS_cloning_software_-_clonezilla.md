---
title: "OS cloning software - clonezilla?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by listerdl on 2010-04-23
Hi, my laptop is bascially my life in terms of my work - I travel a lot and am paranoid that I will lose/damage the many useful programs, tweaks, preferences etc that I have accumulated.

Does a program like clonezilla literally copy every tweak, program, etc when it makes an image of your OS?

I have a dual boot so I imagine that it can completely clone both windows 7 and ubuntu, (seperately).

So basically if the worst happens then the re-install will re-install all the tweaks and programs right?

THANKS!!!!!!!!!!

---

### Post by da burger on 2010-04-23
Different programs work in different ways but if it is an imaging software (clonezilla is) it will make an exact copy of your hard drive or partition. There won't be a single difference between the two hard drives unless something hasn't worked properly.

On a side note be careful with clonezilla. If the source drive is bigger than the target drive clonezilla won't work.

Angus

---

### Post by HermanAB on 2010-04-23
Hmm, long ago I also fretted about backups of my system.  However, the reality is that Linux is so easy to install, that backing up the whole system is a total waste of time. It is much better to ignore the system and only backup your data.

One day when trouble strikes, you would not want to re-install a month old backup of a 3 year old system.  It would be better to install the latest version of Linux and recover your data.

---

### Post by listerdl on 2010-04-23
> **da burger said:**
> 

On a side note be careful with clonezilla. If the source drive is bigger than the target drive clonezilla won't work.

Angus

You mean if the, for example, external hard drive that is receiving the copied data is too small then clonezilla wont work?

---

### Post by da burger on 2010-04-23
I agree with Herman I was just answering the question.

Say you have a 100GB drive with 50GB of data and you clone it.
You then try to recover the clone onto a 70GB drive (after all there is only 50GB of data in the clone) it will not work from my understanding. This is something to do with the way the data is copied.
Angus

---

### Post by KdotJ on 2010-04-23
I worried about this kind if problem too in the past. But I agree with the fact it's much easie to just install Linux and then copy your data in. What I also do is have a text file which I update with my list of programs I use and what tweaks I've done and how to do them. So when I do have to reinstall a system, I just follow the instructions I've made for myself.

---

### Post by kaibob on 2010-04-23
> **da burger said:**
> Say you have a 100GB drive with 50GB of data and you clone it.
You then try to recover the clone onto a 70GB drive (after all there is only 50GB of data in the clone) it will not work from my understanding. This is something to do with the way the data is copied.
Angus

This is the clonezilla FAQ--it has a lot of useful information:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

As to the size question, I agree with da burger:

> Clonezilla is NOT able to restore the image from LARGE harddisk to smaller one, but it CAN restore the image from small harddisk to larger one.

[http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/26_resize.faq#26_resize.faq](http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/26_resize.faq#26_resize.faq)

BTW, the size of the drive that will be used to store the image file is not important as long as it has enough free space for the image file and for temporary files created by clonezilla. Large external hard drives are cheap now, so this shouldn't normally be an issue.

---

### Post by bumanie on 2010-04-23
Personally I like dd commands to clone hard drives. Regardless of whether you use dd or clonezilla, both will make a bit for bit clone of your hard drive. Why things won't work if the target drive is not of equal or larger size, is because it doesn't just copy data, it copies/clones the entire partition/drive.

---

### Post by Scotness on 2010-05-29
> **HermanAB said:**
> Hmm, long ago I also fretted about backups of my system.  However, the reality is that Linux is so easy to install, that backing up the whole system is a total waste of time. It is much better to ignore the system and only backup your data.

One day when trouble strikes, you would not want to re-install a month old backup of a 3 year old system.  It would be better to install the latest version of Linux and recover your data.

With all respect Herman I must disagree - manually restoring is a time intensive process that requires interaction - if you have a cloned back up you can just plug it in and go - and the process of cloning it first is basically set and forget ~ so you can use that time for something productive away from the computer.

I recently had a laptop hard drive die - I'm now running Karmic Koala off a USB drive - with another USB drive for documents and files etc. I have alot of packages and add ons etc installed so I don't want to reinstall everything manually - so I used these instructions to clone my boot USB:

[http://blog.nicolasbouliane.com/?p=1115](http://blog.nicolasbouliane.com/?p=1115)

- which worked fine for me - but you've got to be very careful you get the drive order right or you'll destroy what you want to back up!

So now I have an exact clone I can boot from and it did the original cloning without any time or interaction from me once I set it up.

So I have 2 x 8GB boot memory sticks - and a 4 GB stick for data. The two boots are EXT3 and the data is FAT32 -- I have Thunderbird portable installed on this drive so I can run it off a windows system for my email if I want - or off my Linux system - as my thunderbird install on Karmic is configured to read off the thunderbird portable profile on the 4gb stick.

The system is not bullet proof (I'm sure I'll find new and interesting ways to stuff it up!) - but as long as I back up the data regularly and the boot stick whenever I've accumulated enough changes to the original I should be fairly safe.

Scot

---

### Post by lazyart on 2010-05-30
My system just got hosed upgrading to Lucid.  No worries mate!

I booted into a live CD.  Ubuntu's disk recognized I had a RAID0 array but couldn't mount it.  I used Puppy instead which didn't see the array but let me access the drives individually.  I backed up my /home to an external disk.

Then I installed Lucid to the array.  Just as I thought it preserved my /home, but I was taking no chances.

Some time ago I had used this tutorial: [http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/) which made a list of the packages I had installed.  So I use it again to reinstall all my apps.  And I'm rolling all over again.  It might not be a bad thing to set that to run once a month and save it to somewhere like a Ubuntu One cloud.  That, along with the mirrored array, keeps me pretty bullet proof.

---

