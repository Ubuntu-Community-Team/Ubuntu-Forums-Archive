---
title: "Ubuntu Netbook install problem-4 partitions already"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by wheelyfeet on 2010-12-08
My HP Mini 210 came with 4 partitions so I do not get the option to install Ubuntu alongside my current OS (Win7). Three are labeled volumes and the fourth is unlabeled. It's tiny and cannot be explored. I am hesitant to just delete a partition not knowing if it is necessary for something. My mini came with Splashtop (which I had to disable in BIOS in order for Ubuntu to load) and I wonder if that is where it resides. 
 
One idea I have is to move drive E contents to a USB drive (HP tools), but I'll need to find out if I can and if they'll run from a stick. OR should I run a boot info script as suggested in another thread I saw regarding this problem and have someone more computer literate look at it?
 
I am a COMPLETE Linux novice and since the days of MS DOS haven't really bothered to learn much about computers, so please speak very S L O W L Y and use small words! Thanks! 
 
Debra
 
Screen shot of Disk Management attached per Quackers advice.

---

### Post by Quackers on 2010-12-08
Thanks for that.
Is your hard drive approx 150GB?

---

### Post by wheelyfeet on 2010-12-08
> **Quackers said:**
> Thanks for that.
Is your hard drive approx 150GB?
 
160GB.  I should also mention that I don't plan to use Windows once I get Ubuntu up and running, but I do wish it to remain on my machine for now. So I don't think I need Windows on a large partition?? 
 
Thanks!

---

### Post by Quackers on 2010-12-08
Ok, what other users have done is to delete the HP Tools partition. This is a partition which holds diagnostic tools, but I believe these tools are available elsewhere, if needed. 
However that would only give you 99MB of space, which isn't enough to install an operating system on.
What I suggest is to first defragment the C: partition at least once, preferrably twice. (From memory I think defrag is in the maintenance section of the start menu).
When the defrag has run you should go back to the disk management screen and right-click on the C: partition and select "shrink". A new window will open up and give you details of the amount that you can shrink C: by. Select the amount you wish and click ok. After about 30 seconds or so the C: partition will appear smaller and a new entry will appear for unallocated space.
At this point you can right-click on the HP Tools partition and select delete volume. (If you want to back up the contents first you may need to show hidden files first).
So at that point you will have only 3 primary partitions and some unallocated space.
I would suggest that you reboot Windows at this time to make sure everything ran ok.

You can now boot from the Ubuntu Live cd/usb and install into that free space. If you are using the 10.10 installer I do not recommend that you choose "install alongside" other operating system. There have been problems with that!
I suggest you choose "specify manually" and create your swap space and root partitions manually (/home partition too, if required).
If you need help at any stage it will be safer to ask first :-)

---

### Post by wheelyfeet on 2010-12-09
> **Quackers said:**
> If you are using the 10.10 installer I do not recommend that you choose "install alongside" other operating system. There have been problems with that!
I suggest you choose "specify manually" and create your swap space and root partitions manually (/home partition too, if required).
If you need help at any stage it will be safer to ask first :-)

Thanks for the help thus far.  I've created the free space and now I'm to the point where I need to manually install the OS and here I lose it. If I try to install in the free space, I get an error that says I need a root file.  I have no idea how to create a "swap space" or a root file. Can you direct me to instructions?  

Thanks again.

---

### Post by wilee-nilee on 2010-12-09
> **wheelyfeet said:**
> Thanks for the help thus far.  I've created the free space and now I'm to the point where I need to manually install the OS and here I lose it. If I try to install in the free space, I get an error that says I need a root file.  I have no idea how to create a "swap space" or a root file. Can you direct me to instructions?  

Thanks again.

So lets see another picture of the disk manager, I'm looking for the amount of unallocated space you have now.

So W7 boots up and everything is okay there correct?

Are you booting a Ubuntu live cd or thumb for this install?

---

### Post by wheelyfeet on 2010-12-09
> **wilee-nilee said:**
> So lets see another picture of the disk manager, I'm looking for the amount of unallocated space you have now.
 
So W7 boots up and everything is okay there correct?
 
Are you booting a Ubuntu live cd or thumb for this install?
 
Win7 boots up fine. I am using a thumb drive. A picture of disk management with new space is attached.
 
Thanks! Debra

---

### Post by wilee-nilee on 2010-12-09
So the easier way to do this is to use gparted on the live cd to build the partitions then just use the custom install setting.

So click on that unallocated space in gparted and make a extended partition that will fill the whole unallocated space, inside the extended make a ext4 partition. And a swap partition around twice the total amount of ram you have if you intend to use the sleep or hibernate. 

Close gparted, and hit the install icon now.

You then use the custom button when you get to the partitioning In the install. At that choice of side by side whole disc or custom, is a where is the grub pointed is shown, with a drop down menu, I believe above or below this choice area make sure grub is pointed at the HD. Probably sda, just confirm that the HD is reading as sda when you build the partitions in gparted. No numbers after the sda you want it in the mbr=master boot record.

So choose the custom you will see the ext4, by size in the partitions to choose from. Click on the little box then change, in the next popup choose ext4; with the drop down below it is another drop down choose / (/=root) click okay it will return to the custom menu click on that ext4 in its little check box then install, after that you will put your user name and password in.

Feel free to post any questions it is only once you hit that install after the custom choice where it actually starts to install, to that ext4 partition.

---

### Post by wheelyfeet on 2010-12-09
Thanks for the input Wilee; however, it's Greek to me. I looked at my thumb drive and don't see a gparted program.

---

### Post by wilee-nilee on 2010-12-09
> **wheelyfeet said:**
> Thanks for the input Wilee; however, it's Greek to me. I looked at my thumb drive and don't see a gparted program.

Menu-system-admin-gparted

you can also open it with a terminal command

```
gksudo gparted
```

---

### Post by wheelyfeet on 2010-12-09
Doh! I actually found it in the applications.  One question before I set up the partitions.  Windows Disk Manager only allowed me to shrink its drive to aprox 70GB; however, the program itself is only about 30GB.  Is it safe to shrink it further?  The unallocated space is only about 58GB and I'd rather have Ubuntu residing in the larger of the two.

---

### Post by wilee-nilee on 2010-12-09
> **wheelyfeet said:**
> Doh! I actually found it in the applications.  One question before I set up the partitions.  Windows Disk Manager only allowed me to shrink its drive to aprox 70GB; however, the program itself is only about 30GB.  Is it safe to shrink it further?  The unallocated space is only about 58GB and I'd rather have Ubuntu residing in the larger of the two.

So you have a netbook with no cd reader is this correct?

Do you have the W7 backed up so that in a worse case scenario you can reinstall it?

I believe you have a recovery partition=D that will be pretty much dead weight once you dual boot anyway, so really what I would do if it was me is use the W7 backup tool to make a image of the whole C partition onto a external drive, that can be just reloaded using a recovery cd. This image will reload activated and all I have done it myself. You can then remove the D partition gaining that space, we would want to see the bootscript in my signature though to confirm where all the W7 boot files are situated.

Just really trying to get to the best setup here. It is probably feasible to use gparted to shrink C, but in the past you had to follow some guidelines to do this safely. The problem is that in W7 there are unmovable files on the C partition that when moved by gparted will at the least trigger a chkdsk that you want to reboot to, then W7 again to make sure it is working. Worst scenario though is a borked W7 which if you have no backups and a way to boot a recovery disc leaves you a bit stranded.

If you have W7 install on a thumb though that will work as a reinstall and can be used to reload a backup.

It is good that your asking questions about all this it is the smart thing to do here.

---

### Post by wheelyfeet on 2010-12-10
I'm actually starting to wonder why I want or need to keep Windows at all.  I use some CAD programs that have to run in Windows on my desktop, but I certainly won't be using those on a netbook.  I think it's kind of that "I paid for it, I want to keep it" mentality, regardless of whether I will ever use it!  I think I'll sleep on it and decide tomorrow.  If I just do a clean install of the program, I don't need to partition drive space.  Is that correct?  It should do all that for me?  

Debra

---

### Post by wilee-nilee on 2010-12-10
> **wheelyfeet said:**
> I'm actually starting to wonder why I want or need to keep Windows at all.  I use some CAD programs that have to run in Windows on my desktop, but I certainly won't be using those on a netbook.  I think it's kind of that "I paid for it, I want to keep it" mentality, regardless of whether I will ever use it!  I think I'll sleep on it and decide tomorrow.  If I just do a clean install of the program, I don't need to partition drive space.  Is that correct?  It should do all that for me?  

Debra

It is up to you but you can probably get the OEM disc set to install it back or a straight ISO or straight install disc from the computer vendor I would want that if it was me at the least. A Straight install disc can be put on a thumb same as a ISO if needed for future reinstall. Hedge your investment so to speak.

I have W7 but I got it for 25$ with a student discount and only use it really to help windows users.

Also if your not really tied to it and can get reinstall stuff or just make a backup we can safely shrink it more with gparted and probably remove D and you will still have W7 and way more Ubuntu, you never know when you might like having W7 on there.

Here is my setup from gparted. I have W7 in one partition so we would as I said just want to make sure all the boot was in C if you kept it shrunken a bit more. I have an image of this install of W7 that is I think about 15 gigs on a external as well, as an ISO and 2 dvd's they sent me an extra dvd.
[ATTACH]177984[/ATTACH]

---

### Post by wheelyfeet on 2010-12-11
Thanks so much for the help to both Quackers and Wilee-Nilee. I found the screen shot really helpful.  

In the end, I decided to go with a full install on my netbook and don´t think I´ll regret it.  So far I love the interface and everything works.  

I have a full copy of Windows 7 pro and think I´ll do a dual boot set up on my desktop, so the advice in this thread will be referred to again.  In the meantime, I´ve checked out some books to study.  

Debra

---

### Post by Quackers on 2010-12-11
I'm sure I can speak for wilee-nilee as well when I say you're welcome :-)
Enjoy!

---

