---
title: "how best to do a clean lucid install on wp/lucid dual boot"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-05-22
Sigh I only just noticed I called "xp" wp in the title - and it should be a question


I've been wrestling with this stupid "DVD may or may not be there today" problem for weeks now ... the sheer amount of my time used to try to solve it is getting silly ...


Sooooooo ....

**  Feel free to skip over this paragraph it's just me whining a bit ** My last shot at making this OS work for me will be to do a clean install of Lucid over top of the current upgraded lucid I now have which is driving me crazy ...  if these DVD problems persist after this I will drop lucid and perhaps ubuntu entirely.  I like the product but at some point I have to put a value on my time.  I have hunted these forums, posted, waited, tried advice, prowled the internet ... all trying to find some answer to a problem that shouldn't be there.

The last time I did a clean install was when I first installed 6.06 so my current theory is there's some sort of leftover conflict/problem either from that or from the upgrade to 8.04 or the upgrade to 10.04.

To be honest I'm not comfortable working with partitions ... I'm pretty sure there are 4 on my disk: 

the first (sda1?) is for windows
the fourth (sda4?) is a linux swap

the second and third are both for linux ... not sure which is which or why I went with 2 in the first place... was following some advice or other (did i set up a separate one for home? I don't know maybe)

In any case, I want to completely erase all contents of both of the linux partitions ... the last thing I want to do is somehow carry forward this DVD problem ... wherever it is I want it gone.  As no linux OS has ever really been entirely stable for me I don't care about losing any old setting

If I understand the install a little then it will generally speaking overwrite one of those 2 partitions while leaving the other alone?

I want to make sure both get completely erased ... How can i do this?  is it something I should do before the install?  during? after?

  
I suppose the install will overwrite my existing old grub with the new one? ... There may be some issue with ext3 vs ext4? whatever that really means to me ...  Those issues at least seem to have solutions ...

For the life of me I can't find a solution to something that seems as basic as using a DVD/CD without trouble.  Everything I try either works for a little while before reverting or just seems to make more trouble or both.

How do I best just get rid of anything and everything ubuntu currently on my system and replace it with a fresh install?

---

### Post by -humanaut- on 2010-05-22
Looks like you've learn a time lesson about doing an upgrade vs a clean install. Format the partition with ubiquity install.

---

### Post by anothernewuser on 2010-05-22
Hmmm .. I have no idea what that means let me run a search ;)


And thx for offering some help.


I ran sudo fdisk -l and got this output:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3f2f3f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26500   212861218+   7  HPFS/NTFS
/dev/sda2           26501       28412    15358140   83  Linux
/dev/sda3           28413       30261    14852092+  83  Linux
/dev/sda4           30262       30401     1124550   82  Linux swap / Solaris


I'm not opposed to this structure for any particular reason - indeed I might want to make the linux partitions bigger as I've allocated more space to Windows than it really needs - I just want to make sure that whatever is in both of those linux partitions gets wiped clean ...

Will ubiquity do that? I looked at a screen shot and I think I won't be able to preserve 2 linux partitions? or will I? do you know?

---

### Post by anothernewuser on 2010-05-23
Sooooooooooooooo .... I'm ready to go ...

Have my copy of lucid in the drive and just need to reboot ....

I intend to install it into sda2 where I think the current copy is hiding ...

I suppose what I need to know ... if anyone out there can help me is this ...


How do I wipe sda3 in the deal? I don't want to get rid of it entirely just make sure its empty so nothing is carried forward to the next install

I think sda3 was set up many years ago to be my home directory (file system ... whatever the right name is) and that structure hasn't actually caused any trouble (or has it been the /root of all my troubles? sigh a joke in all this) ...  so I don't really need to actually get rid of the partition just erase it?


Sigh I have to trust my future with this operating system to the perfect functioning of a DVD drive that this OS likes to pretend doesn't exist... there's irony in there heavy irony.


Alrighty ... got the clean install in and running after 1 bad burn of the DVD ... dealing with "normal" problems now I suppose like multimedia and so on ...

Here's what I did:

I ran the Live DVD and selected "Try ubuntu without installing" or whatever that was exactly called ... and then I clicked on the "Install" icon on the desktop ... went through the install process told it how I wanted to manually set up the partitions ... and got some scary error warning telling me it probably wouldn't work and inviting me to stop ... so I did.

So I rebooted ... and this time just selected "Install Ubuntu" and it worked fine.

In manually setting up the partitions I chose to set up sda2 as "ext4" and "/" and I chose sda3 to be "ext4" and "/home".  I ticked the "format" option for both partitions and let it begin.

I've no idea why I would have chosen ext4 ... I don't even know what it is really.  

But all worked and now ... I'm back to being frustrated by why this OS doesn't come set up to play DVD's and that pesky "Mozilla Firefox" that doesn't want to let me make my own decisions ;)

---

