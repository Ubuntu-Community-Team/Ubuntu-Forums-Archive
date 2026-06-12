---
title: "Installing Ubuntu on an existing Ubuntu partition"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by thk123 on 2010-04-05
Hello,

I have previously installed Ubuntu 9.10 x86. However, since I installed Windows 7 I have been unable to access the Grub menu and my computer jumps straight to Windows. I thought this would be a good time to change to the 64 bit version of Ubuntu which I have been meaning to do for a while.

When I load up the installation program from the Live disk I see that the original Ubuntu partition is still there. I don't really need both versions and I am happy to format the existing Ubuntu partition and stick the new version on top.

My question should be simple, how do you do that? I went to Specify Partitions manually (choosing side by side only lets me shrink the Windows partition and I don't want to erase the entire disk, just a single partition.) However, I cannot tick the format box for the Ubuntu partition. Do I need to resize it down to a size of 0? (I was nervous of doing this as it said it was irreversible so really I am just looking for reassurance this is the correct next step.)

Once I have done this, will I simply be able to click the greyed out Add button and make the required partition.

Thanks in advance.

---

### Post by byStanderone on 2010-04-05
...would suggest that you leave win7 partition untouched,  and focus on the existing ubuntu partition, and install your 64 there...take note of your partition infos...would surmise you have sda2 for your former ubuntu (x86)?

---

### Post by r-senior on 2010-04-05
You don't need to resize it. You should be able to format it. 

Is it mounted? If you are running the installer in the live CD session, it may have auto mounted it? I don't have a live CD around to check.

Installing from the front menu, without using the "Try Ubuntu without any changes ...", should work.

---

### Post by Paqman on 2010-04-05
In manual partition, select the partition > edit > format as EXT4 > select mount point as /.

After that when you return to the first screen you should see that it's now go the box checked for being formatted.

---

### Post by thk123 on 2010-04-05
Wow thank you very much for the speedy replies!

I selected the EXT4 as suggested and it is now currently installing, fingers crossed.

Thanks again,

(assuming this works, do I edit the original post to mark is solved?)

---

### Post by Paqman on 2010-04-05
> **thk123 said:**
> 
(assuming this works, do I edit the original post to mark is solved?)

You can mark the thread as solved from the "Thread tools" link at the top.

---

