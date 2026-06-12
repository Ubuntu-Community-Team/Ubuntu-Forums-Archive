---
title: "[Ask] Increasing Ubuntu Partition"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by NeoIndigo on 2009-02-02
Hi, 

I want to delete my windows xp part and re-allocate all of the space to Ubuntu. 

What I have done so far:
- I have deleted the ntfs file system using gparted 

However, the space is free and it's not yet allocated to Ubuntu. 

How should I do it ? 

I have read some of explanation about it, where people ask to boot from LiveCD and go to the system > administration > partition editor. However, when I boot the LiveCD, which option should I go to ? "install ubuntu" or "Try Ubuntu without any change to your computer" ?

The LiveCD that I have is the one for Hardy. Some people suggest to go to "Start Ubuntu In safe graphic Mode". I don't see that in the option of my LiveCD. 

Can anybody help me with this ? 

Thanks

---

### Post by binbash on 2009-02-02
Download Gparted Live CD, boot with it, resize the partition.

---

### Post by Praxicoide on 2009-02-02
Hit enter on "Try Ubuntu..." once it boots up, you can go to system---->administration------>partition editor.

You can then resize your existing partitions to take up the unallocated space or create a new one, depending on how you have them set up.

---

### Post by Neural oD on 2009-02-02
yes - when dealing with partitions - they shouldn't be mounted - and thus you need to boot up a live cd!

---

### Post by indytim on 2009-02-02
In direct answer to your question. when using the Ubuntu LiveCD, you would use the **Try Ubuntu without any change to your computer** option.   As was suggested above, another option is to get a copy of GParted Live and use it.  Either approach will get you to a partition editor that you can use on your Ubuntu partition(s).

IndyTim

---

### Post by NeoIndigo on 2009-02-02
Thanks a lot guys. I will try to do it right now. :p

---

### Post by Praxicoide on 2009-02-02
If you have only one partition, now would be a good time to add a /home partition, which is recommended, since you can do a clean Ubuntu install without messing with your files or configuration.

Here's a [nice guide](http://www.psychocats.net/ubuntu/separatehome). You already have unallocated space, so you can jump to that step.

---

### Post by NeoIndigo on 2009-02-02
Hi guys, 

When I started the LiveCD and went to the partition editor, this is what I see

(I attached below)

I assume ext3 is the one I should increase. So, when I right click on it, I am confused about resizing it. it says free space preceeding and after it. Which way should I do ? 

Or should I just right click on the unallocated space and choose it to be ext3 ?

@Praxicoide : when should I do that ? Right now or after I am successful resizing it ? 

Thanks alot. please let me know if my response is a bit confusing. 

Thanks again.

---

### Post by Neural oD on 2009-02-02
can't see your screenshot - but yes i assume that the ext3 is your ubuntu - xp would use ntfs most probably. You need to grow that partition - not create another one.

---

### Post by Praxicoide on 2009-02-02
Those instructions are to be carried before you resize; that is, where you are currently. If you want to, of course.

That /dev/sda5 partition is a Windows partition, most likely the backup of the one you erased. If you want, you can erase that as well and gain more space (You would then shrink the extended partition it was on so that it only covers the swap).

What you would do next to install a separate home partition is to create a new ext3 partition in the empty space, then click "apply." Check the name of the new partition.

You can then follow the instructions (if you want) on that link starting from "Using the new partition" remembering to put the names of your partitions in place of the ones given in the example. Your old home will be in /dev/sda3.

EDIT: But of course the safe route would be to simply enlarge that partition, by moving the other partition out of the way, to the start of the disk.

---

### Post by linux_tech on 2009-02-02
To select a partition click on it , then with the mouse click onto the Partition menu and choose Resize-Move. Then click apply.

---

### Post by NeoIndigo on 2009-02-02
So guys, 

I still have one more issue. After I unallocated both of the ntfs file system, it has no format. So, in order to extend the ext3 file system to unallocated space, should I re-format the unallocated ones to the ext3 first ? 

Because right now, when I right click on the ext3, it says that the maximum size is only 17.48 (which has been used around 15.40). The only option I have is to either shrink it from the front or shrink it from the back. 

Any ideas ? 

I really appreciate your help. I attached the screen shot below. Hopefully, you can see it right now. Thanks.

---

### Post by carml on 2009-02-02
You can extend your existing ext3 partitions if there's near some free space,so firts of all you need to move a free partition to an ext3 if you want to extend this last one :)  .

---

### Post by Praxicoide on 2009-02-02
From the screenshot it looks like you still have a NTSF partition, the one named /dev/sda5 (in green). You probably want to erase that.

After that is done, you can shrink the extended partition (in aqua)(the empty frame around swap that used to have the NTSF partitions) so that it is only "wrapped around" the swap (in brown) with no empty space.

Once you've done that, you can either move this extended partition to the very start (so you have a lot of free space to extend your ext3 partition ((in blue))) or you can create a new ext3 partition in order to create a /home partition. (you could also move it a little to extend your existing parititon, but still give space for a new /home partition).

If this seems too complicated, then just move the extended partition to the start and enlarge your existing partition, although I recommend creating a separate /home partition, to keep your files safe from really ugly mistakes.

---

### Post by ChaiTan on 2009-02-02
According to [http://ubuntuforums.org/showthread.php?t=244261](http://ubuntuforums.org/showthread.php?t=244261), it's not possible to move the start of an ext3 partition, so the only solution would be moving /home to a separate partition.

---

### Post by NeoIndigo on 2009-02-02
Thanks a lot guys !! (especially for Praxicoide, you help me a lot man, thanks !!)

Now I have a lot of empty space to use. I haven't installed the /home partition yet. I just want to know why I need that (in depth). 

Thanks a lot !!

---

### Post by Praxicoide on 2009-02-02
Having /home on a separate partition means that the root partition (/) can be reformatted or erased without this affecting your personal files and settings (which are saved at /home). This way if you encounter a serious error that is practically unsolvable or too much of a hassle (most likely the latter) then you can reinstall Ubuntu without touching your /home partition. This also holds true if you want to do a clean install of a newer Ubuntu version (yes, you can update, but a clean install will probably mean fewer errors).

So, the next step would be to create an ext3 partition in the empty space, without assigning any mount point yet, and then hitting "apply"

---

