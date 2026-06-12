---
title: "No grub in Ubuntu HDD"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by newbub on 2009-12-12
Hello, I am new to Ubuntu although I have installed a couple other computers with Ubuntu with no other OS's. I did not have problems with those installs but I am having trouble with this one.

What happened was that I have a 2nd HDD that has lost it's windows COA so I decided to install Ubuntu. It was set up as a 2nd drive in my Vista computer so I proceeded to install Ubuntu in that drive. Little did I know that my MBR would be changed by this install. I have managed to get my Vista to boot normally but now the Ubuntu install shows no grub when I install it in the other desktop. 

I came upon vnbuddy2002's post which gives instructions on how to restore grub as follows:

                                  **HOWTO: Restore GRUB (if your MBR is messed up)**             
                                                                Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

What I don't know how to do is in Step 4 above, how to mount the appropriate linux partitions. I do manage to get into the partition manager and they are as follows:

/dev/sda1 ext3 76.7 MB
/dev/sda5 swap 3.3 MB

The HDD has no free space as the Ubuntu install has used up all of it. So how do I mount the appropriate linux partitions as in step 4 above?

---

### Post by raymondh on 2009-12-12
> **newbub said:**
> Hello, I am new to Ubuntu although I have installed a couple other computers with Ubuntu with no other OS's. I did not have problems with those installs but I am having trouble with this one.

What happened was that I have a 2nd HDD that has lost it's windows COA so I decided to install Ubuntu. It was set up as a 2nd drive in my Vista computer so I proceeded to install Ubuntu in that drive. Little did I know that my MBR would be changed by this install. I have managed to get my Vista to boot normally but now the Ubuntu install shows no grub when I install it in the other desktop. 

I came upon vnbuddy2002's post which gives instructions on how to restore grub as follows:

                                  **HOWTO: Restore GRUB (if your MBR is messed up)**             
                                                                Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

What I don't know how to do is in Step 4 above, how to mount the appropriate linux partitions. I do manage to get into the partition manager and they are as follows:

/dev/sda1 ext3 76.7 MB
/dev/sda5 swap 3.3 MB

The HDD has no free space as the Ubuntu install has used up all of it. So how do I mount the appropriate linux partitions as in step 4 above?

You mount it by highlighting the appropriate partition and SELECTING the mountpoint amongst the drop-down menu.

Let me ask a couple of questions:

1.  Do you want GRUB to be your bootloader?  If yes, why not just re-install GRUB which will by default, install itself on the HD that is set to boot first in your BIOS.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

2.  Do you want to control the boot thru QUICK BIOS changing?  If so, install GRUB in the MBR of the 2nd HD (as I presume Vista and it's bootloader is in the first HD).  If you are going thru the insstall process again as it seems in your post, in step 7 is an advanced button.  Click on that and choose where you want to install GRUB.

I just noticed (re-reading your thread) something. Are you installing Ubuntu in the 1st HD? And I hope the MB is just a typo.  It says :

[B]
/dev/sda1 ext3 76.7 MB
/dev/sda5 swap 3.3 MB[/B]

I thought you were installing in the 2nd HD which should be sdb.  This I am assuming that Vista is in the 1st HD and said HD is set to boot first in BIOS.

If you are in liveCD/live session now, kindly access terminal and type/post back results of

```
sudo fdisk -l
```

Also, how did you fix the Vista MBR issue.  Did you do the FixMbr command?  If so, that would have overwritten the existing MBR.  Just asking.

Thanks

---

### Post by newbub on 2009-12-12
Thank you for your reply Raymond... ok... lol... I would have easily re-installed Windows XP on this hdd were it not for the COA being partially torn. I had installed it on my HP because I was trying to recover the data (namely the COA) but the windows folder was no where to be found. So, as a last resort, I decided to install Ubuntu while the hdd was still in my HP. I thought that nothing would happen to my HP MBR but I did not go into the Advanced section when partitioning the new Ubuntu install on this 2nd hdd (or I did but did not understand Ubuntu partitioning well enough) so my Vista MBR was overwritten by default by the new install.

Anyways, I then took this 2nd hdd and mounted it in the other desktop (which is old so the size of the hdd is NOT a typo, lol) and thought that it would boot. But to my dismay, since the grub was written in my HP hdd, it wouldn't load. So I was trying to find a way to 'install' the grub portion to the already existing Ubuntu install.... hence, I cannot go to the Ubuntu desktop and follow the instructions in the link that you provided (which I had found before this post). 

I was hoping to be able to install the grub only but all this is pointless now as I am already reinstalling the Ubuntu as of now. If I had found a way to just install the grub within Ubuntu, it would have saved me hours of updating the system as the Ubuntu CD that I have is old and my internet connection is very slow.

And yes, I used my Vista DVD and did a repair installation and used the bootrec /fixmbr and then bootrec /fixboot commands then restarted my HP. After the restart, everything was back to normal for my HP.

Thanks again for your reply Raymond.

---

### Post by teward on 2009-12-12
Well, you could just install it directly to the second drive.  Had to do this on my desktop because it couldn't write the Windows boot loader away, and I changed boot order to the Ubuntu drive.

The methods are generally the same, but I did it through a clean install onto a second HDD

---

### Post by raymondh on 2009-12-12
update us on how to re-install went.

Happy ubuntu-ing and holidays as well :)

---

