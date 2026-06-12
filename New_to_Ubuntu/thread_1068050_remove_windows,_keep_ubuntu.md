---
title: "remove windows, keep ubuntu"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by hollowtd on 2009-02-12
I have installed Ubuntu 8.10 alongside Xp. I would now like to get rid of XP and keep Ubuntu. Is this possible or do I have to do everything from scratch? I'd like to free up the diskspace and just have the computer be a linux machine. Thanks again

---

### Post by kanikilu on 2009-02-12
If you just want to wipe out the Windows partition and reclaim the space, you can use the Ubuntu Live CD to run GParted. Just remove the Windows Partition and then you can resize the Ubuntu partition without losing your data. After that, you'll probably just want to make sure the Windows stanza is removed from your /boot/grub/menu.lst file (assuming you are using GRUB as your boot manager).

Here's a generic guide on using GParted:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

It recommends you download the GParted Live CD, but if you have the Ubuntu Live CD, just boot with that and then go to System > Administration > Partition editor, or press ALT+F2 and type gksu gparted.

Oh, and the resizing step can take a fair amount of time, or at least it did in my case...

---

### Post by hollowtd on 2009-02-12
Wow, thanks. I'll take a look into that and let you know if I run into any problems. Sounds sort of complicated for my level, however. I have the Ubuntu 8.10 CD that I got in the mail but that is all. I'm not sure what the windows stanza line means, so once I understand that, I think I know where you're coming from. I'm not sure what Gparted means either, but I'll look at the guide link you pasted here. Thanks

---

### Post by wolfen69 on 2009-02-12
just boot the live cd, open terminal and:
```
sudo su
```
then
```
gparted
```
then you will see the partitions on your computer. there is a pull down menu on the top right. select the windows partition. just right click it and delete. next go to the pull down menu again and select your ubuntu partition. right click and resize. you will then be able to "drag" the rectangular box to whatever size you want.

---

### Post by drjonze on 2009-02-12
> **hollowtd said:**
> Wow, thanks. I'll take a look into that and let you know if I run into any problems. Sounds sort of complicated for my level, however. I have the Ubuntu 8.10 CD that I got in the mail but that is all. I'm not sure what the windows stanza line means, so once I understand that, I think I know where you're coming from. I'm not sure what Gparted means either, but I'll look at the guide link you pasted here. Thanks

Its simpler than you think. The 'windows stanza' is the text you see in the boot menu, its the option you select to boot xp, you won't want it if you don't have it. All you have to do is edit your /boot/grub/menu.lst file. just type: > sudo gedit /boot/grub/menu.lst  and then delete the Windows xp text. Just delete everything after the line: > ### END DEBIAN AUTOMAGIC KERNELS LIST

'gparted' is a partition editor. It will allow you to see all of the partitions on your hard drive and edit them as needed.

---

### Post by hollowtd on 2009-02-12
Thanks again. I'll give it a go and let you know if this solves it. I'd like others to know as I had trouble finding anything detailing this sort of uninstall. Thanks again.

---

### Post by hollowtd on 2009-02-12
by live cd we're talking about my ubuntu 8.10 cd I got in the mail, correct?

---

### Post by Therion on 2009-02-12
> **hollowtd said:**
> by live cd we're talking about my ubuntu 8.10 cd I got in the mail, correct?
That's the one!

---

### Post by hollowtd on 2009-02-12
The cd gives me choices: select one: try ubuntu without change, install, check cd for defects, test memory and boot from first hard disk? which do I do I guess?

---

### Post by dazzlindonna on 2009-02-12
oh, and "the resizing step can take a fair amount of time" can mean hours and hours, so just be aware and allocate enough time.

---

### Post by marco123 on 2009-02-12
> **hollowtd said:**
> The cd gives me choices: select one: try ubuntu without change, install, check cd for defects, test memory and boot from first hard disk? which do I do I guess?

"Try Ubuntu without change" will boot you into a "Live" environment where you can open the terminal and enter the gparted commands above.

---

### Post by adder1972 on 2009-02-12
Congrats on becoming Windows free!

Remember that you don't have to resize your "old" XP-partition.  You can just reformat it and use it as a separate partition.

If you want, you can mount it at boot time to a folder in your home-folder for instance.  See some tips here:  [http://arcticlinux.blogspot.com/2007/08/mounting.html](http://arcticlinux.blogspot.com/2007/08/mounting.html)

---

### Post by drjonze on 2009-02-12
> **hollowtd said:**
> The cd gives me choices: select one: try ubuntu without change, install, check cd for defects, test memory and boot from first hard disk? which do I do I guess?

Select 'try Ubuntu without change'.

---

### Post by hollowtd on 2009-03-23
I put the live CD in now and it ask me the five things: try ubuntu and install etc. I already have Ubuntu on my computer. Which do I choose to get run it "live" and then get rid of XP? Just getting to this now?

---

### Post by hollowtd on 2009-03-23
I'm gonna try it now and become Windows Free I hope. I'll see if I run into trouble. Thanks

---

### Post by hollowtd on 2009-03-23
HELL YEAH, WINDOWS FREE. Now, How do I get rid of the boot menu stuff that loads when I turn on my computer so there's a nice clean boot up? Can someone explain to me this and gedit? thanks again

---

### Post by hollowtd on 2009-03-23
and how do I check for the freed up space? to see if it's there I guess?

---

