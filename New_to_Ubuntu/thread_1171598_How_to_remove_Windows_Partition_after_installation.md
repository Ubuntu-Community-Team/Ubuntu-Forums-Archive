---
title: "How to remove Windows Partition after installation of 9.04"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Zuato on 2009-05-27
My question is this - my laptop is currently dual boot Windows and Ubuntu 9.04. I want to delete my Windows partition and acquire that space for my Ubuntu install. What do I use and how? I have gparted, but my concern is will my boot record be removed if I delete my Windows partition and rebuild it as ext4?

A second (semi-related) question is that I have an external fire wire drive that I used gparted on to partition into two segments - one NTFS and one ext4. I cannot do anything with the ext4 partition other than read it. How do I set permissions so that I can use the ext4 partition on my external?

Thank you all very much in advance for the help/advice - I'm still pretty new to Ubuntu/Linux and am ready to switch off Windows. :)

---

### Post by taurus on 2009-05-27
1.  It depends where that ntfs partition is located.  You can use gparted from either Ubuntu LiveCD or GParted LiveCD (can't use gparted on your system since you cannot use it to resize the partition that you are using) to delete the ntfs partition and expand your root filesystem.

2.  If you want to be able to write to the ext4 partition, you need to change the ownership of the mount point (not the device) for that partition from root to your login name with the chown command.

```
sudo chown -R username:username /mount_point_for_that_partition
```

---

### Post by Zuato on 2009-05-27
Thank you for the info - it sounds like it might be just as easy for me to do a fresh install of Ubuntu 9.04 and modify the partitions that way - I already have a backup of all the data I need off the Windows partition.

I ran that command and I am still unable to do anything with the partition. The way I read that command is the username:username would be username that has permissions now on the left of the colon and to the right should be my username, correct? 

I did run that on the partition I created (dev/sda5) and that didn't work so I re-ran the command and then unmounted and remounted the drive - still same thing.

---

### Post by taurus on 2009-05-27
What was the exact command that you ran?  Remember, you need to replace username:username with your login name.  The first username belongs to the owner and the second username belongs to the group.

---

### Post by Zuato on 2009-05-28
I ran it two ways...the first way was:

sudo chown -R MYusername:MYusername /dev/sda5

The second time was:

sudo chown -R root:MYusername /dev/sda5

The reason I tried root on the second run was because I could see through the GUI that root is the current owner - I am starting to realize that was not the correct running of the command now. With that said, what is the correct way to run the chown command to gain permissions to this partition? 

You mention the second username in the command as a group - I'm from a heavy Windows Server background and don't recall setting up a group in Ubuntu during the install - is there a default group that my account would belong too or something else?

Thank you again for the time and help!

---

### Post by NHArticleTen on 2009-05-28
I think your idea of starting fresh is a good one.

Plan out your disk partitions and usage beforehand and then go for it(remembering swap and possible future OS additions).

I usually throw a Puppy Linux disk in to work with gparted after doing the DBAN thing(which, of course, means that I'm still using ext3).

---

### Post by taurus on 2009-05-28
> **Zuato said:**
> I ran it two ways...the first way was:

sudo chown -R MYusername:MYusername /dev/sda5

The second time was:

sudo chown -R root:MYusername /dev/sda5

The reason I tried root on the second run was because I could see through the GUI that root is the current owner - I am starting to realize that was not the correct running of the command now. With that said, what is the correct way to run the chown command to gain permissions to this partition? 

You mention the second username in the command as a group - I'm from a heavy Windows Server background and don't recall setting up a group in Ubuntu during the install - is there a default group that my account would belong too or something else?

Thank you again for the time and help!

1.  Both commands are wrong.  You suppose to replace the /dev/sda5 with the mount point, not the partition itself.  For instance, if you mount /dev/sda5 to /media/sda5, then you would use /media/sda5 when you want to change the ownership or permissions of /dev/sda5.

2.  The group (main) and your username are the same.  So if your login name is zuato, then you also belong to group zuato.

```
ls -la ~
```

---

### Post by Zuato on 2009-06-01
Ok, I think I understand better now...I tried the command with /media/sda5 and it returns an error "No such file or directory"

Any ideas on that one?

Thanks again!

---

