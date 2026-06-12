---
title: "Corrupted drive -- any hope?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-07-30
My primary hard drive corrupted somehow and 9.10 won't load.  Grub loads.  I have been using an ARCO EzRaid, but it tends to do a great job of mirroring corruption from one drive to another, so the mirror drive won't load either.  Using the 9.10 bootable (trial) CD, I can look into the master drive running by itself and see that a LOT of directories are of zero length.

I'm using Ext4.  I assume that the partition directory (file table) is corrupted and the files can't be found, rather than a huge number of them being individually corrupted, but my knowledge of the inner workings of Ext4 is slight.

My question is: Is there software, either within the bootable CD or downloadable under the CD OS, or at worst downloadable after I generate a new installation on another drive, that will attempt to recover files and fix the file table?  My last copy of HOME is a few weeks old, so at least capturing as much of the Thunderbird files as possible is important.  Reinstalling the OS onto another drive once this one is semi-repaired is the lesser problem.

Thanks

kirby

---

### Post by KirbySmith on 2010-07-30
And the winner is: oldfred.  In a reponse to another user's question a few weeks ago, oldfred pointed to the web site 

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu)

inside this page I found the command (to be run with the target drive unmounted)

sudo fsck.ext4 -v /dev/xxx  (where xxx is sdc1 in my case)

Still operating from the live CD, I tried this.  fsck.ext4 did not find anything wrong with the superblock, but did find inode (what's an inode?) problems and byte count problems.  After a lot of y responses, it declared the partition ok.  And indeed, I am working from it now, although I haven't searched through the directories for any bad files yet.

Next I need to find a way to clone a booted drive in Ubuntu or clone it from the live Ubuntu CD.

Thanks oldfred

kirby

---

