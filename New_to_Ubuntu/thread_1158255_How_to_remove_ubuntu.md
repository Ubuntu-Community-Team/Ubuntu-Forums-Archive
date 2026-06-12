---
title: "How to remove ubuntu?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-13
Dont worry i am going to reinstall it anyway, I need to remove ubuntu with out damaging my windows boot loader so how to do it

---

### Post by amendt on 2009-05-13
If the boot loader is grub then it is the Ubuntu bootloader.

---

### Post by ravi_buz on 2009-05-13
yes it is grub , i need to know how to remove ubuntu and also able to boot in to windows

---

### Post by amendt on 2009-05-13
When you installed ubuntu, ubuntu probably resized your hard drive fdisk in windows can  modify that or better yet just boot off another live ubuntu cd and run gparted to view your hard drive infrastructure the do a install on the right partition.

---

### Post by neo_1in on 2009-05-13
Revert back to windows bootloader using the windows(xp) cd.
Long form: boot from windows cd, go to screen where it asks for repair of existing installation or new installation, choose reapir, choose your windows dir in following command prompt, enter password, enter commands "fixboot", "fixmbr", "exit". If everything goes smooth, grub will be gone.
After that you can delete the ubuntu partition from within windows from disk management.
Hope it helps!

---

### Post by billgoldberg on 2009-05-13
> **ravi_buz said:**
> Dont worry i am going to reinstall it anyway, I need to remove ubuntu with out damaging my windows boot loader so how to do it

Then just install Ubuntu again on the same partition it uses now.

If you want to remove Ubuntu and switch back to Windows, just say so.

Note: google this kind of thing in the future

---

### Post by ravi_buz on 2009-05-13
1st of all i am not going to switch to windows , its just that my hard disc patition are all jumbled up and so i need to make it in a order and install all over it again , And secondly i tried to repair windows using th cd but it didnt work

---

### Post by billgoldberg on 2009-05-13
> **ravi_buz said:**
> 1st of all i am not going to switch to windows , its just that my hard disc patition are all jumbled up and so i need to make it in a order and install all over it again , And secondly i tried to repair windows using th cd but it didnt work

[http://www.google.be/search?hl=nl&q=repair+windows+boot+loader&btnG=Google+zoeken&meta=&aq=0&oq=repair+windows+boot](http://www.google.be/search?hl=nl&q=repair+windows+boot+loader&btnG=Google+zoeken&meta=&aq=0&oq=repair+windows+boot)

---

### Post by HeirPixel on 2009-05-13
> **ravi_buz said:**
> 1st of all i am not going to switch to windows , its just that my hard disc patition are all jumbled up and so i need to make it in a order and install all over it again , And secondly i tried to repair windows using th cd but it didnt work

As long as you know which partition is Windows, you can use the LiveCD to remove all of the other partitions and reinstall Ubuntu from scratch. Just make sure **not** to touch the partition with Windows on it or you *will* lose it.

What do you mean you tried to "repair" Windows? Are you having a problem with that partition?

---

### Post by Bios Element on 2009-05-13
> **ravi_buz said:**
> And secondly i tried to repair windows using th cd but it didnt work

If you did that you probably broke grub...Windows doesn't play nice with grub/ubuntu.

---

### Post by KOld Iron on 2009-05-13
> **billgoldberg said:**
> Then just install Ubuntu again on the same partition it uses now.

If you want to remove Ubuntu and switch back to Windows, just say so.

Note: google this kind of thing in the future:(

May I quote from the **Ubuntu Forums Code of Conduct**

When answering technical support issues:
... New, or "green" users may not be able to follow you, and many will not ask you for an explanation in order to avoid looking stupid. RTFM, **"Go look on google" are two inappropriate responses to a question **. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question. Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.
...

---

### Post by Don1500 on 2009-05-13
11 You may have broken GRUB, but since you do have the Windows CD you can use FIXMBR to eliminate GRUB and get your windows back. 
If that worked or not next you should download "The Ultimate Boot Disk"(google for it). You will find both a FIXMBR program and G-Parted (mentioned above). I like using G-Parted from here because you can do everything needed without having to worry about locked partitions. But remember, if you can do everything, you can screw everything, so be careful.

BOOT FROM THE DISK

In G-Parted, find the hard drive you have windows on, DON'T TOUCH IT.
if you have data on other drives that you want to keep make a note of them, too. Everything that is left you can play with. You can delete partitions, resize them, whatever. (You can INLARGE your Windows Partition, but don't shrink it). Be sure to make an ext4 partition for Ubuntu /, and add a swap partition (usually about equal to the amount of RAM you have 1-4 gig). WRITE DOWN WHERE EXERYTHING IS. Now go back and install UBUNTU. In the setup put your /(root) directory on that ext4 partition and, if you want, put your /home directory on another (big) partition (ext4 also). Do not do anything to the Windows partition. This should set you up pretty well.

Note on ext4 partitions: some have said there may be problems with this format, I haven't found that. If you want to be extra safe, use ext3.

:popcorn: Now I'll shut up.

---

