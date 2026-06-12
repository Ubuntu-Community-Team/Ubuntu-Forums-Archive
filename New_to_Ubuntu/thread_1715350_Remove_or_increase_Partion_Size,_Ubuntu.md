---
title: "Remove or increase Partion Size, Ubuntu"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by zenawenliang on 2011-03-26
Ok, So I installed Ubuntu last night and I am deciding I rather have it than Windows vista, So I was wondering how to either remove windows vista and make my whole hard disk ubuntu, or make the ubuntu partion bigger, I have already made my windows partion smaller so I have about 100 gigs free but I dont know how to add it to my ubuntu, So first tell me which one is easier and how to do it, any help apprecieted.:o

---

### Post by goldaryn on 2011-03-26
The easiest way to manage partitions is using a program called "gparted" (Gnome Partition Editor).

It can be found in Applications -> Ubuntu Software Centre

Search for it under "Get Software"

When installed it appears under System -> Administration -> GParted

If you are confident with what you want to do with the partitions, then go ahead. If not, it's probably to ask here again before you go ahead.

---

### Post by zenawenliang on 2011-03-26
I used the gparted on the livecd and removed like half of my windows partion so I have 100 GBs free space I just dont know how to increase a partion size I'll send a screenie If I can.

---

### Post by zenawenliang on 2011-03-26
Do I need any xtra addons for gparted?

---

### Post by beew on 2011-03-26
Since Vista is installed first it is on the left most portion of the harddrive if you look at it from gparted. So you have now 100G of unallocated space followed by Ubuntu's boot partition (/) and perhaps a home partition to the right of that (/home) The only way to use that unallocated space for Ubuntu would be to first move both the / and /home partition to the left to fill the void and then extend the /home partition to the right.  

The tricky part is to move the / partition to the left (moving both ends to the / partition to the left). I had expand the right boundary of the / partition  (to the right at the expense of /home) many times successfully with gparted before but I am under the impression that moving the left end of the / partition  may be troublesome. 

I have tried moving the whole / partition to the left  once (like what you try to do now) and my harddrive ended up not bootable (with lots of i/o errors) I have not figured out whether it was because of the move or the harddrive just happened to die at the same time.

One guy said that you can move your partitions by just cut and paste. I haven't tried it (I ended up installing another Linux distro to the space vacated by Windows instead of expanding Ubuntu) but if you want to follow his advice, please report back whether you are successful.

See post #7 by sydbat
[http://ubuntuforums.org/showthread.php?t=1689961](http://ubuntuforums.org/showthread.php?t=1689961)

---

### Post by zenawenliang on 2011-03-26
I didn't understand you at all, sorry, but heres a screenie just tell me what to do, 

[IMG]http://i56.tinypic.com/2zxzb7l.png[/IMG]

---

### Post by beew on 2011-03-26
Ok so you don't have a /home partition so it would be simpler. In this case you need to expand sda5 to the left to fill the unallocated space (by moving the left end of sda5 to the left). But like I said I am not sure if it is safe to move the left end with gparted. You can try the copy and paste solution suggested in my link and if it works then just delete the original Ubuntu partition and expand the new partition to the right (that I am sure would work, that is , expanding the right end)

Or you can wait until someone more knowledgeable to confirm that moving the left end of the Ubuntu partition is safe.

---

### Post by zenawenliang on 2011-03-26
Uhh, I have it open and I dont know how to move it to the left, sorry, noobin it up.

---

### Post by beew on 2011-03-26
You unmount the partition first (so you can't do it in your Ubuntu partition, have to boot from a live usb or live CD) then right click the partition (sda5) and choose "resize ...." and then just drag the left end of the partition all the way to the left so that it will cover all unallocated space. Then click apply. 

But I strongly suggest you wait for someone more knowledgeable to confirm that this won't render your hard disk not bootable.

---

### Post by zenawenliang on 2011-03-26
And whom may that be?

---

### Post by beew on 2011-03-26
> **zenawenliang said:**
> And whom may that be?

Don't know. Just wait. :)

---

### Post by beew on 2011-03-26
Oh, do you want to delete sda1 and sda2? (I thought vista is already deleted) If that is the case, you have to delete sda1 and sda2 and expand sda3 to the left before you expand sda5

---

### Post by samcot on 2011-03-26
I'm a noobie, too, but if I understand you correctly, you said that you don't care if you don't have Vista on your PC, and you'd just as soon make it all Ubuntu? If that is the case, there's nothing easier than doing an Ubuntu install that uses the entire disk. Are you interested in that approach?
 
*I'll add in the proviso that, just in case you ever wanted to put Vista back on the PC, you either possess or create a set of Vista recovery discs. :-)

---

### Post by goldaryn on 2011-03-27
You can see that sda5 is your Ubuntu root partition (you can tell by the "/" symbol. And there is a bunch of unallocated space to the left of it, within the same extended partition. So you should be able to drag sda5 to the left to fill that space.

It needs to be unmounted to do that, so you can't do it from your ubuntu install - do it from the Ubuntu live CD.

But need someone more experienced than me to confirm that this won't upset GRUB as the partition will start in a new place.

It will have the same name, so it shouldn't, but I'm not 100% sure. Can anyone confirm?

Failing that, if you don't mind reinstalling Ubuntu, you should be able to delete everything apart from sda1 (the Dell partition) and sda2 (the Windows partition) and then install Ubuntu into the big block of space you will then have.

---

### Post by priyal85 on 2011-04-14
I'm also having a similar problem. I have a Ubuntu 10.04 installation in dual boot with Windows XP. Now I want to expand my ext4 ubuntu partion. I could srink the windows partion using Ubuntu live CD and Gparted utility. But the 4.5GB of free unallocated space I could create is not allocatable to the my Ubuntu ext4 partion. I neither cant expand the Ubuntu partion nor move or drag. I'm attaching a screenshot of my Gparted view. I struggled a lot with this. Please someone help me this out.
 
[IMG]https://lh6.googleusercontent.com/_7PsgxyScNY4/Tabj9WsGs4I/AAAAAAAAAA8/KST8S7rEy9M/s640/Screenshot.png[/IMG]

---

### Post by priyal85 on 2011-04-24
I could sorted out this. All I needed to do was to move my SWAP partition to left of my ext4 partion. Then I could easily utilize all the unallocated space. :) (Erlier I was trying to move only the ext4 partition. Did not try to move the swap, where I made the mistake)

---

