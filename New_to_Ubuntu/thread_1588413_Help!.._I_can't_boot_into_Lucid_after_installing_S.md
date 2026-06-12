---
title: "Help!.. I can't boot into Lucid after installing SimplyMepis"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by mikodo on 2010-10-04
Hello everyone,

I thought I would try SimplyMepis in it's own Primary partition and still be able boot into Lucid. Well, I can't and when rebooting, all I can boot into is Mepis. I must have messed up the grub2, how it is attached to the MBR. 

So, I am writing this from the Live CD of Lucid. I want to delete the /dev/sda4 partition with Mepis and attach grub2 to the MBR with Lucid, so I can boot into Lucid again.  Everything except sda4, was to do with Lucid before I made the sda4 partition for Mepis. I am attaching an output of fdisk-l and screenshot of gparted showing the partitions.

I don't have a clue what to do next.

Thank you for help, again!

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+  83  Linux
/dev/sda2            1403        3503    16876282+  83  Linux
/dev/sda3            3504       15893    99522644+   5  Extended
/dev/sda4           27404       38913    92454075   83  Linux
/dev/sda5            3504        4140     5116671   82  Linux swap / Solaris
/dev/sda6            4141       15893    94405941   83  Linux
ubuntu@ubuntu:~$ 
```

---

### Post by robert shearer on 2010-10-04
Mepis uses grub legacy and does not recognise ext4 partitions.

No problem.
Just search with the following in your browser  
```
site:ubuntuforums.org restore grub2 live cd
```

and you will find threads that will show you how to reinstall grub2 from the live cd.

Once you have done that you will be able to boot both Mepis and Ubuntu.

---

### Post by mikodo on 2010-10-04
Thanks Robert,

Good eyes, yes I made the new partition for Mepis an Ext4!

I'll do as you say with the search.

Thank you.

Mike

---

### Post by andrewthomas on 2010-10-04
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by mikodo on 2010-10-05
Well thanks guys,

Nothing brought the grub2 back to life in Lucid. Tried many different ways. I did another clean install and brought my /home forward successfully from the last install. 

Funny, it was 6 months ago, when I did the same thing, when I had installed Karmic and Debian Lenny on other partitions, and then uninstalled/deleted the partitions, and hosed Hardy.

I swear on everything holy, all extra distros, I install from now on, are going in vm's in VirtualBox!!!

Thanks for the help.

I needed to try something, and your suggestions were the right ones. I just couldn't get them to work.

At least Lucid is snappier now! Having burned an iso Live CD of Maverick RC just yesterday, was tempting, to install. I resisted, as I need some stability in my life right now, including my computer habit. Wish I had taken that advice earlier today... LOL!

Best regards  :smile:
Mike

---

