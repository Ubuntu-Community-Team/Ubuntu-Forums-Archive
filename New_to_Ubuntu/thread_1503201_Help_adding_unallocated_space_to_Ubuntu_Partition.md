---
title: "Help adding unallocated space to Ubuntu Partition?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by alex5454 on 2010-06-06
[SIZE=4]Hey everyone.  I recently partitioned my hard drive to dual boot Windows 7 and Ubuntu 10.04.  I am really starting to like Ubuntu and want to add more space to it.  I shrank my Windows partition and now around 54 gigs of unallocated space that I want to give to Ubuntu.  I booted into a Mint live Cd which has Gparted but I still can't figure out how to add it.  If someone could walk me though the steps that would be just fantastic.  I am a complete Linux newbie so bear with me if if I am a little slow.  Thanks =)

*I included a screen shot of GParted from withing Ubuntu
[/SIZE]

---

### Post by waynefoutz on 2010-06-06
You're going to need to do this with the live cd, It's not going to work with any part of the disk mounted.

---

### Post by cryptotheslow on 2010-06-06
what is the ext3 partition /dev/sda4 used for?

---

### Post by alex5454 on 2010-06-06
[SIZE=4]I have no idea.  Lol, I'm not entirely sure what any of the partitions are.[/SIZE]

---

### Post by Rodemire on 2010-06-06
Hi, 
I just want to make sure we are on the same page here. U want to add the unallocated 53.99Gb to /dev/sda5 right?
Well, i am not a guru but i think i can help. There's a small problem though, there's a partition, /dev/sda4, which is in the way,like cryptotheslow has pointed out. If /dev/sda4 has important data,try copying it elsewhere then proceed as follows; 
Remove /dev/sda4 and make it unallocated. This will effectively merge all the unallocated space between /dev/sda2 and dev/sda5. Then all you just do after that is to resize/move /dev/sda5 to cover the unallocated portion. Mind you, playing with partitions always carries a risk, backup all important data. And the process can actualy take a long time.
Hope this helps. I'm sorry fo any incorrect terminology i'm using a cellphone and i don't have a pc in front of me.

---

### Post by Joe of loath on 2010-06-06
Your partitions are a little messy... I think it'd be best to tidy them up before you try anything :lol:

---

### Post by cryptotheslow on 2010-06-06
Well without knowing what is in sda4 (not much by the look of it) I wouldn't advise deleting it.

From the Live CD go into GParted.

1. Right-click on the small sda (swap) partition and take the "Swapoff" option to unmount it
2. Right-click on sda4 and take the option to Move it all the way to the left next to sda2
3. Right-click on sda3 and take the option to Move it all the way over to the left next to sda4, whilst in there drag the right hand side of it all the way to the right to resize it to include the unallocated space.
4. Right-click on sda6 and move that all the way to the right in the new space within sda3
5. Right-click on sda5 and resize that by dragging the right-hand edge out to take up all the space between itself and sda6

Take the option to commit changes and sit back and wait - do not disturb until it completes.

Once done, exit GParted and reboot (removing your CD of course!) - and with luck that's it.

I've never had any problems using GParted to do complex partition moves and resizes - but data loss is always a risk when doing anything partition related - so always back up anything critical before starting.

---

### Post by tabernash on 2010-09-04
I have a question about partitioning. I used [https://help.ubuntu.com/community/SwapFaq#addswap](https://help.ubuntu.com/community/SwapFaq#addswap)  to add a swap file on my Ubuntu 10.04 install. When I rebooted it  showed that my swap file was a 2Gb file (as you can see it should only  have been a 512). Being a new user of Ubuntu, I figured that I could  just use Gparted and resize the swap to what I wanted. I did that and  when I checked again I had over a 1Gb of unallocated space. I am  wondering if it would behoove me to 'pretty up' the unallocated  partitions and merge them to the main bootable partition. I am a bit  'OCD' about stuff like that. ;-) I realize that I will have to use either Gparted LiveCD or the Ubuntu LiveCD to do that.

Since you gave very detailed instructions to alex5454, I was wondering if I could prevail on you to give me some tips on doing it.

Also, I am wondering if the swap file should be contiguous to the boot partition?

Or am I just being too concerned about a trivial matter?

Below is a scrcap of my Gparted and the results of my fdisk.

Thanks in advance!

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37419008   83  Linux
/dev/sda2            4659        4864     1648641    5  Extended
/dev/sda5            4660        4724      522112+  82  Linux swap / Solaris


[IMG]http://s984.photobucket.com/albums/ae322/tabernash_ubuntu/?action=view&current=gparted1.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i984.photobucket.com/albums/ae322/tabernash_ubuntu/th_gparted1.png[/IMG]

---

### Post by tabernash on 2010-09-04
Sorry... here's the image (I hope).

;-)

[http://i984.photobucket.com/albums/ae322/tabernash_ubuntu/gparted1.png](http://i984.photobucket.com/albums/ae322/tabernash_ubuntu/gparted1.png)

[IMG]http://i984.photobucket.com/albums/ae322/tabernash_ubuntu/gparted1.png[/IMG]

---

