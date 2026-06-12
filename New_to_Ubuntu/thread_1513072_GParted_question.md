---
title: "GParted question"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by myolbug on 2010-06-18
Hello everyone!
Ok, here is what I need help with.  I have three partitions on my laptop.  One is Ubuntu 10.04, one is Mint and one is Win7.  I want to eliminate the two Linux partitions and replace them with Mint 9 64 bit and reduce my Win7 partition down.  I know that I can use GParted to do it, but I could use some pointers.  

Do I just remove all of the Linux partitions and just leave Windoze or is there another step in between?  Is there a GParted For Dummies?

When I looked at them a bit ago, it showed the three partitions, plus some other stuff, which right now I am apparently suffering from Mental Flatulence, because I can't remember what it is.  Soo, I'll boot into the live CD and I'll update this thread in a couple of minutes with all of the relevant info.

Advice is still welcome between now and then, though.

Thanks!

P.S.  Any easy ways to back up the few pics and docs I have on the two partitions?  I have never really gotten UbuntuNone figured out, because I have difficulty with it and I can never just do a bulk upload, I have to do it file by file.

Thanks again!

---

### Post by myolbug on 2010-06-18
Okay, I gotta remember, Swap.  Yes, I will remember...

Anywho, enough sarcasm, here is a screenshot of what I get.  

[IMG]http://i913.photobucket.com/albums/ac334/Myolbug/Screenshot--dev-sda-GParted.png?t=1276916888[/IMG]

Windoze shows up three times for some insane reason, prolly cuz Gateway upgraded it from Vistduh or something, I'll never understand Bill's minions!

I just want to replace the two Linux partitions with Mint 9 as I staed above.

Thanx

---

### Post by cj.surrusco on 2010-06-18
The second Windows partition is a partition that holds the boot files, and I'm pretty sure the first one would be a recovery partition. 

To answer your question, you are correct. All you have to do is remove all of the partitions inside the extended partition for Linux, then remove the extended partition itself. 

Then you can resize the Windows partition as you wish. You would want to resize the third one because that is your C: Drive. 

You'll then be okay to install Mint in the following free space.

---

### Post by wilee-nilee on 2010-06-18
First shrink W7 with the W7 disk manager, then delete all the Linux stuff with the live mint cd then install mint in the free space, I think mint with a regular not custom install makes a extended with a primary and a swap partitions inside. **When you shrink W7 reboot it while the Linux OS's are still there.** Once you remove the Linux if you wanted just W7 you would just need a recovery cd and a command to reload it.

As the second post suggests you have a recovery don't touch that only resize the partition that is the OS.

sda1 looks to be the recovery sda2 looks to be the boot it has a boot flag on it, sda3 looks to be the main os.

---

### Post by myolbug on 2010-06-18
> **wilee-nilee said:**
> First shrink W7 with the W7 disk manager, then delete all the Linux stuff with the live mint cd then install mint in the free space, I think mint with a regular not custom install makes a extended with a primary and a swap partitions inside. **When you shrink W7 reboot it while the Linux OS's are still there.** Once you remove the Linux if you wanted just W7 you would just need a recovery cd and a command to reload it.

Thanks for the tip!!!  I'll do so and get back witcha!  Any easy ways to upload the pics etc as mentioned above in post one???  Even compress them and what not?

I am learning, but still, toddler steps... :-k

---

### Post by cj.surrusco on 2010-06-18
I would just transfer them to the Windows 7 partition if there is enough space.

---

### Post by wilee-nilee on 2010-06-18
> **myolbug said:**
> Thanks for the tip!!!  I'll do so and get back witcha!  Any easy ways to upload the pics etc as mentioned above in post one???  Even compress them and what not?

I am learning, but still, toddler steps... :-k

Edited: I don't know about the pics, you should buy a external HD anyway to have stuff backed up off the computer.

The recovery if it was vista/XP? is not usable probably so you might consider deleting it if this is the case. It sounds like you have a ISO or DVD of W7; that is a compressed recovery.

If sda1 is the vista/XP? recovery, just make sure you know, and it may have some sort of boot mechanism in it, even though the boot flag is on sda2.

Really you want to make sure you have stuff backed up that you can't lose at the least.

---

### Post by k3lt01 on 2010-06-18
> **myolbug said:**
> P.S.  Any easy ways to back up the few pics and docs I have on the two partitions?  I have never really gotten UbuntuNone figured out, because I have difficulty with it and I can never just do a bulk upload, I have to do it file by file.

Thanks again!Before you do anything you will need to mount the Windows partitions from within your Linux partitions. So if you have pics and docs in Mint boot Mint and mount Windows. Then copy the Mint files you wish to keep to your Windows partition. Then do the same with your Ubuntu materials.

After you are sure you have saved everything you want to save boot into Windows and do a disk check and defragment. This will tidy up your Windows partition and make it much less likely to stuff anything up with the shrinking and moving.

Now all that is done use GParted, I prefer the actual GParted cd which you can download and burn easily, to make your changes. You can simply deleted /dev/sda4 because it contains all your Linux installs and then format over it. A word of advice, IMO your SWAP partitions are way overkill, you shouldn't need anything larger than 2gb SWAP.

Now work out what partition is your ACTUAL Windows partition, probably /dev/sda3 and change it to the size you want.

After that is done make sure the new (old Windows) free space is part of the old Linux free space. Make your new Mint partitions how you want them and then with your Mint disk install Mint.

---

### Post by myolbug on 2010-06-19
> **k3lt01 said:**
> Before you do anything you will need to mount the Windows partitions from within your Linux partitions. So if you have pics and docs in Mint boot Mint and mount Windows. Then copy the Mint files you wish to keep to your Windows partition. Then do the same with your Ubuntu materials.

After you are sure you have saved everything you want to save boot into Windows and do a disk check and defragment. This will tidy up your Windows partition and make it much less likely to stuff anything up with the shrinking and moving.

Now all that is done use GParted, I prefer the actual GParted cd which you can download and burn easily, to make your changes. You can simply deleted /dev/sda4 because it contains all your Linux installs and then format over it. A word of advice, IMO your SWAP partitions are way overkill, you shouldn't need anything larger than 2gb SWAP.

Now work out what partition is your ACTUAL Windows partition, probably /dev/sda3 and change it to the size you want.

After that is done make sure the new (old Windows) free space is part of the old Linux free space. Make your new Mint partitions how you want them and then with your Mint disk install Mint.

I never really noticed the swap size!!!!  Big enough for ya?  That was all set up by the LiveDVD that I used for both installs.  I'll pay closer attention to that.   
How do I mount Windoze in Linux?  I have heard of such an animal, I just have never seen it!     (Annoying smiley here.)

Is this a good way to do it?  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by wilee-nilee on 2010-06-19
Go to home and the W7 partition will be in the sidebar. Or in the menu-places-computer dropdown.

---

### Post by myolbug on 2010-06-19
> **wilee-nilee said:**
> Go to home and the W7 partition will be in the sidebar. Or in the menu-places-computer dropdown.

(Sheepishly ducks head!)  

Oh, I guess I have been doing this all along...  I have in the past had difficulty getting Linux stuff to transfer to Windows, I'll try it now while I am in the LiveDVD, but any suggestions if I run into this snag?

I have been able to copy stuff from windows to Linux, but not Vice Versa.

---

### Post by k3lt01 on 2010-06-19
> **myolbug said:**
> How do I mount Windoze in Linux?  I have heard of such an animal, I just have never seen it!     (Annoying smiley here.)

Is this a good way to do it?  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)Psychocats method is spot on. Bookmark that blog and refer to it often, it will help answer many questions.

---

### Post by myolbug on 2010-06-19
> **k3lt01 said:**
> Psychocats method is spot on. Bookmark that blog and refer to it often, it will help answer many questions.

Thanks, I installed it on LiveDVD and then I just drug a pic into Windows and it shows that it is there, no problems!  So, since my Ubuntu partition is encrypted, I am going to boot into that and drag all my goodies into Windows from there.  Thanks for all the help everyone, if I run into any snags, I'll let you know!

EAT: Allow me to elucidate a bit.  I went into a terminal and used *sudo apt-get install ntfs-config* and it did it's thang.  I then went into Admin and used the auto config.  After I closed everything, I was able to drag a pic from my Mint partition to Winders.

I have yet to read the above blog, but it seemed the logical thing to do.

---

### Post by myolbug on 2010-06-19
Okay ditto to the above, I did it on my encrypted partition and "Bob's your uncle!"  I am now going to venture into the realm of the much venerated GParted.  Wish me luck!!:lolflag:

---

### Post by k3lt01 on 2010-06-19
Good luck :popcorn:

---

### Post by myolbug on 2010-06-19
Well, thanks to your assistance with this, I have successfully completed my first partition removal, etc.  Without the knowledge that you all have provided, it looked really intimidating, but, now that I know, it was really simple.
I know have Mint 9 64bit, with all updates on my laptop and all is as it should be, so, thanks again!  I'll be sure to pass this knowledge on to anyone I run across that needs it!!!

---

### Post by k3lt01 on 2010-06-19
Well done :popcorn:

---

