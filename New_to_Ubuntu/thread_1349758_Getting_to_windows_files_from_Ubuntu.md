---
title: "Getting to windows files from Ubuntu"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by grifan526 on 2009-12-08
After using Xubuntu for a while I realized the only thing I don't like is I don't have any of my files like my pics and music because they are still on Windows. So I was wondering what the easiest way to access those files would be, can I do directly to them or do I need to set up another partition, and if so how should I format it?

---

### Post by t0p on 2009-12-08
When you go into your file manager, isn't your Windows partition listed there?  When I used to dual boot Ubuntu and XP, I could directly access the Windows partition through the file manager - under 'Places' in Nautilus (the Ubuntu file manager), I don't know what the equivalent is in Xubuntu... but the partition *should* be visible.

---

### Post by Marvin666 on 2009-12-08
With a few packages, you should be able to mount the partition. I assume it's ntfs.
I don't know them off the top of my head, but it shouldn't be too hard to find them.

---

### Post by Locke_99GS on 2009-12-08
ntfs support has been default in Ubuntu for quite some time now. No extra packages needed, just mount the Windows drive and start using it.

---

### Post by The_Pirate_King on 2009-12-08
Under the "Places" menu you should see your windows partition, you can open it and navigate to your files. 
If, for some reason, you cannot mount the partition, you can always transfer your files to a CD, DVD, or USB and put them on Linux that way.

---

### Post by Locke_99GS on 2009-12-08
The the Windows partition is not showing up under the "Places" menu, we can still walk you through how to discover which partition contains Windows, and how to make it mount.

---

### Post by physeetcosmo on 2009-12-08
> **grifan526 said:**
> ... can I do directly to them or do I need to set up another partition, and if so how should I format it?...

grifan526-

This begs a vital question: is the drive/partition you want to mount ON the Xubuntu machine, or is it on another remote machine?

Ubuntu can access NTFS drives natively without conversion (that I know of anyway), I frequently access my LOCAL NTFS drives on my Dual-Boot server. 

For local drives: you can access the partition by simply clicking the "drive Icon" when you open up a file navigator window. The drives and your folder links are listed in the left-column.

---

### Post by llamabr on 2009-12-08
To simplify the process, install:

```
sudo apt-get install ntfs-config
```

---

### Post by Locke_99GS on 2009-12-08
If ntfs is already supported for him (which it has been out-of-box for quite some time, now) then ntfs-config will only make his life more difficult.

---

### Post by grifan526 on 2009-12-08
yea it the Windows partition is not showing up in my places directory, so how do I go about changing that?

---

### Post by rednano12 on 2009-12-08
Paste the output of this command:

```
sudo fdisk -l
```

---

### Post by grifan526 on 2009-12-08
Here is the out put for sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f41eb71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         863     6928384   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         863       11602    86262860    7  HPFS/NTFS
/dev/sda3           11603       14593    24025207+   5  Extended
/dev/sda5           11603       14463    22980951   83  Linux
/dev/sda6           14464       14593     1044193+  82  Linux swap / Solaris

---

### Post by Locke_99GS on 2009-12-08
```

sudo mkdir /mnt/Windows
sudo mount /dev/sda2 /mnt/Windows

ls /mnt/Windows

```

You can navigate to /mnt in Nautilus, and drag the Windows folder to the bottom of the laft-pane to create a bookmark for it so that it will show up in your "Places" menu.

If you want it to mount automagically at boot, let us know, and we'll show you how to add an fstab entry.

---

### Post by grifan526 on 2009-12-08
Awesome, that worked thanks.

---

### Post by JKyleOKC on 2009-12-08
> **Locke_99GS said:**
> 
You can navigate to /mnt in Nautilus, and drag the Windows folder to the bottom of the laft-pane to create a bookmark for it so that it will show up in your "Places" menu.The original poster seems to be using Xubuntu, which has Thunar as its file manager rather than Nautilus. I also use Xubuntu, and found that installing pysdm, through Synaptic, provided a total and very simple solution.

After installing pysdm, run it (it will be in the Applications menu's System category as Storage Device Manager), and expand the tree of drives in its left pane. Highlight the desired partition and click it; you'll see a message saying it has not been configured and asking if you want to do so. Click the Yes button, then click the Assistant button in the right pane to choose your options (I've found that the defaults are good, and also that they can be changed later if you need to do so). The most important, to me, is whether to mount at boot time or not.

Finally, click the Mount button in the right pane. You can then close pysdm, navigate to /media, and open the mounted drive. To put it on your Places menu, highlight the drive name in /media and drag it to the lower half of the left pane in the File Manager window. This establishes a shortcut. You can then rename the shortcut to something like WIN_C if you dislike the rather cryptic SDB1 or whatever partition name.

Hope this helps!

---

### Post by TinSoldier on 2009-12-08
Heres another file problem..

I have access to my windows drive files using file browser..

But under my firefox twitter (echofon, formerly "twitterfox") client, im trying to load a custom botification sound file.

Some .wav files show on my source drive but not all files, in particular the sound files i want, which i can see and play with the normal file browser.

So why are some of my files (show hidden checked) hidden ??? in firefox (twitter) file browsing process but not ubuntu's file browsing process ????

How do a access all my files ???

PS also how do i remove / add the default login for ubuntu so it just starts with out having to log-in every boot..??

---

### Post by Locke_99GS on 2009-12-08
I'm unsure about Echofon and Mozilla, but your second point (logging in automatically) run ```
gdmsetup
``` and tell it to log you in automatically.

---

### Post by TinSoldier on 2009-12-10
> **Locke_99GS said:**
> I'm unsure about Echofon and Mozilla, but your second point (logging in automatically) run ```
gdmsetup
``` and tell it to log you in automatically.

thankyou

---

