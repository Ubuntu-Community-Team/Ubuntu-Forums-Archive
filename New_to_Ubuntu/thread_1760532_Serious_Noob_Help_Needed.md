---
title: "Serious Noob Help Needed"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Blacksheep427 on 2011-05-17
I had Ubuntu 10.10 successfully installed on a 50GB partition of my 500GB hard drive. I was running a dual boot with grub that installed from the same disk as 10.10. Both Windows 7 Pro and Ubuntu 10.10 previously booted via grub fine multiple times. I updated to 11.04 via Ubuntu's update manager, again successful in operation.

Ubuntu was asking me for a password that I set up from the beginning, which it would not accept even though I put the correct password in.

Anyway, I likely did a very stupid thing. While in Windows, I went to the disk manager and deleted the partition which had Ubuntu with the intention I would re-install 11.04 from a disk I just downloaded from the website. The 50 GB that did have Ubuntu is now labeled unallocated.

Now, I cannot boot anything, neither Windows or Ubuntu. I get an error message stating error:no such partition. grub rescue>

What, if anything, can I do to fix this? I'm still searching for the Windows Recovery disks, so far no results there. I'd like to avoid re-installing Windows, but whatever I have to do to get it working.

Thanks in advance to any help.

---

### Post by manishraj2011 on 2011-05-17
> **Blacksheep427 said:**
> I had Ubuntu 10.10 successfully installed on a 50GB partition of my 500GB hard drive. I was running a dual boot with grub that installed from the same disk as 10.10. Both Windows 7 Pro and Ubuntu 10.10 previously booted via grub fine multiple times. I updated to 11.04 via Ubuntu's update manager, again successful in operation.

Ubuntu was asking me for a password that I set up from the beginning, which it would not accept even though I put the correct password in.

Anyway, I likely did a very stupid thing. While in Windows, I went to the disk manager and deleted the partition which had Ubuntu with the intention I would re-install 11.04 from a disk I just downloaded from the website. The 50 GB that did have Ubuntu is now labeled unallocated.

Now, I cannot boot anything, neither Windows or Ubuntu. I get an error message stating error:no such partition. grub rescue>

What, if anything, can I do to fix this? I'm still searching for the Windows Recovery disks, so far no results there. I'd like to avoid re-installing Windows, but whatever I have to do to get it working.

Thanks in advance to any help.
The ubuntu partition is shown unallocated because you deleted it ( although by mistake ).

Now simply re-installing ubuntu on the very same partition should solve the issue ( You also get your windows 7 back ).

You can do this by selecting manual partitioning at time of installation. Just don't touch any other partition during the process.

---

### Post by Jagoly on 2011-05-17
Yes, just as pointed out. Installing ubuntu in that allocated space will reinstall and reconfigure grub.

Just for future reference, a partition that contained an old version of ubuntu can be wiped, then have the latest version installed with a single button in the installer on the 11.04 live cd. Personolly, I always put my new distros/releases on new partitions (in case I don't like them).

---

### Post by Blacksheep427 on 2011-05-17
Ok, but how do I reinstall it? I do not have access to even Windows. It stops loading at the error msg.

---

### Post by NCLI on 2011-05-17
> **Blacksheep427 said:**
> Ok, but how do I reinstall it? I do not have access to even Windows. It stops loading at the error msg.

Did you not write the cd before wiping Ubuntu? If so, you'll have to either borrow another computer to write the cd, or reinstall Ubuntu from an older cd.

---

### Post by Blacksheep427 on 2011-05-17
I did make a CD of 11.04 from Ubuntu's website (likely not what you are referring to, though) while my computer was last operational, but that disk, nor the older 10.10 disk from the initial Ubuntu install will boot. 10.10 disk starts to load, but it stops on a purple screen with a rectangle symbol the = sign and a man icon. No other progress. It gave gray screen and blinking cursor after sitting for few hrs. From grub rescue prompt, what should I do? With an unallocated 50 GB space, ought I now assume I need to find Windows recovery disks to start all over?

Thanks for above replies.

---

### Post by Blacksheep427 on 2011-05-17
> **manishraj2011 said:**
> The ubuntu partition is shown unallocated because you deleted it ( although by mistake ).

Now simply re-installing ubuntu on the very same partition should solve the issue ( You also get your windows 7 back ).

You can do this by selecting manual partitioning at time of installation. Just don't touch any other partition during the process.
 
Neither the new 11.04 or old (originally used) 10.10 disks will give any boot or install options. 10.10 tries to progress, but sometimes shows various error codes then stops at the "purple screen with a rectangle symbol, the = sign and a man icon". No more progress, period. At other times I get the "error:no such partition. grub rescue>" message. I do not know enough to progress any further. If I cannot fix this, I will need to find the Windows recovery disks and start Windows that way.

---

### Post by Prince Valiant on 2011-05-17
Hi!

The grub rescue prompt has almost no options, and will not be useful for booting into windows.  

As far as the purple screen, the =, and the man, have you tried pressing enter at that point?  When I've used the install disk, that's the point at which I press enter to choose my language.

The problem is that all the GRUB files are located on the Ubuntu Partiton, and were lost when you deleted it.  I've done the exact same thing as you before. :-D

-Val

---

### Post by potat on 2011-05-17
Maybe try making another LiveCD? There's no reason that deleting the partition should prevent you from booting from a CD. If that doesn't work, try making a live USB drive.

---

### Post by Blacksheep427 on 2011-05-17
No, I had not done that. But I am doing that now. I will update on status. Thanks.

---

### Post by Blacksheep427 on 2011-05-17
> **Prince Valiant said:**
> Hi!

The grub rescue prompt has almost no options, and will not be useful for booting into windows.  

As far as the purple screen, the =, and the man, have you tried pressing enter at that point?  When I've used the install disk, that's the point at which I press enter to choose my language.

The problem is that all the GRUB files are located on the Ubuntu Partiton, and were lost when you deleted it.  I've done the exact same thing as you before. :-D

-Val

Well, a little progress. You were right, it was waiting for me to push start. That brought me to language screen, then to an ubuntu menu. Try ubintu and install ubuntu and other options here do not seem to do anything.

Some progress though...

---

### Post by Prince Valiant on 2011-05-17
After you got to the install Ubuntu and Try Ubuntu options, did you hit enter to choose one?  

If you look at the bottom of that same screen, there should also be an option to hit F6, F5, F4, etc.  One of them is labeled 'options.'  Try selecting that, and then use the arrow buttons to highlight "noacpi."  Press enter to select that, then Esc to go back to the main screen, then Install Ubuntu or Try Ubuntu (your choice).  That, if I remember right, disables fancy graphics or drivers that cause problems on some computers.

---

### Post by Blacksheep427 on 2011-05-17
Ok. Followed to the F6 option, etc. as you said. Escaped to main, and trying to see if install will work. All has worked thus far. Still waiting on install progress...

Ok, did try ubuntu. Got to busybox v1.15.3
I entered help for a list of built-in commands. Also says: (initials) stein: I/O error mounting /dev/loop0 on //filesystem.squashfs failed: no such device
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

PS: I was trying 10.10. Because I did have 11.04 installed, maybe I should use that disk. Waiting for other pc to finish download to put on cd or jump drive.

---

### Post by manishraj2011 on 2011-05-17
> **Blacksheep427 said:**
> Ok. Followed to the F6 option, etc. as you said. Escaped to main, and trying to see if install will work. All has worked thus far. Still waiting on install progress...

Ok, did try ubuntu. Got to busybox v1.15.3
I entered help for a list of built-in commands. Also says: (initials) stein: I/O error mounting /dev/loop0 on //filesystem.squashfs failed: no such device
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

PS: I was trying 10.10. Because I did have 11.04 installed, maybe I should use that disk. Waiting for other pc to finish download to put on cd or jump drive.
Seems like.... your old 10.10 ubuntu CD / DVD is a corrupted one. 

Have You tried checking the CD/DVD for errors ( You will get option option like  " check installation media / CD / DVD for error " when you boot-up using the CD/DVD ).

---

### Post by Blacksheep427 on 2011-05-17
No, I did not check the disk. But I will do. Am also making new 11.04. Other pc slow downloading. Will update progress.

---

### Post by Blacksheep427 on 2011-05-18
Thanks to each of you for assistance. Up and running good again. Had to burn new copy of 11.04. Other pc took extremely long in download, considering we have 10 Kbps DSL. Ubuntu went right back into place. Only difference is that Ubuntu split the 50 GB 47 and 3 to give itself a swap file. No problem as far as I am considered. Thank you all again.

---

### Post by Prince Valiant on 2011-05-20
Glad it's fixed!  For future reference for the rest of the community, would you mark the thread as solved?  

Thread tools --> mark thread as solved.

Thanks!

-Val

---

### Post by Blacksheep427 on 2011-05-21
I sure will; I guess I forgot to do that. My apology. :)

---

### Post by Prince Valiant on 2011-05-24
No problem.  Have fun!  :-D

-Val

---

