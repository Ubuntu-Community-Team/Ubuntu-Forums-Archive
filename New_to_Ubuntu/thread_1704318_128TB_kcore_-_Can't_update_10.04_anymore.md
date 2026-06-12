---
title: "128TB kcore - Can't update 10.04 anymore"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by basicsearcher on 2011-03-10
A file (kcore) in /proc in / - is showing a file size of 128TB.
Result - each time i boot up, i get a dialog box saying, "The volume 'Filesystem root' has only 0 bytes disk space remaining." ' (The program displaying this might be: "update-notifier"?")
Now i can no longer update the OS (10.04.02), as it says there's no space when i try.

I see there's a bug report for this: [**Bug 629394**]("https://bugzilla.gnome.org/show_bug.cgi?id=629394") -        Nautilus displays wrong size of "/". The report is at:
[https://bugzilla.gnome.org/show_bug.cgi?id=629394](https://bugzilla.gnome.org/show_bug.cgi?id=629394)
There's also a patch attached to the above page, and if i knew how to apply patches, that would be the way to go i suppose?
Searched the forums, and found a number of refs. to the 128TB error. Tried 2 things:

1. Entered this command for sda5 (my rootsystem - i have a dual boot setup with Win7):
sudo tune2fs -i 1d /dev/sda5
The machine duly checked the / filesystem this a.m. on bootup. But still 128TB.

2. I read where someone had fixed this problem by booting the live gparted CD, selecting the / partition, and running the Check routine. So i did that.  But still 128TB.

I guess i can fix this by re-installing 10.04. But i'd rather not. Any suggestions? All gratefully received!

---

### Post by gradinaruvasile on 2011-03-10
Edit: Here:

[http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7004153&sliceId=1&docTypeID=DT_TID_1_1](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7004153&sliceId=1&docTypeID=DT_TID_1_1)

is some explanation. That is a virtual file, it does not take actual space. The problem is somewhere else.

Disregard what i posted earlier

(Is that kcore only? Please post the full path+name for it.

You may try deleting it - be warned this may render the system unbootable, so first post its full name here.
You may look up which package owns it with:

dpkg --search filenamewithfullpath)

---

### Post by basicsearcher on 2011-03-10
Thanks gradinaruvasile. Yes, it's frustrating to be held up to ransom by a file that takes up 0 space!

Here's the text from the terminal, after i'd run the commands you suggested:

patrick@patrick-laptop:~$ cd /proc
patrick@patrick-laptop:/proc$ ls /proc/kcore -s
0 /proc/kcore
patrick@patrick-laptop:/proc$ dpkg --search /proc/kcore
dpkg: /proc/kcore not found.
patrick@patrick-laptop:/proc$ 

If i were able to delete the file, and then the machine wouldn't boot up, what then? Sorry for ignorance on that one.

---

### Post by Seq on 2011-03-10
/proc/kcore is not a real file (gradinaruvasile edited his post). Furthermore, /proc it's own filesystem, not part of /, so it would not affect space on /.

Problem probably is that your root partition actually is full.

What is the output of `df -h` ?

You can try to use the "Disk Usage Analyzer" (baobab) to analyze your system for what is actually using space.

---

### Post by basicsearcher on 2011-03-11
Your reply appreciated, Seq.

You said, "Furthermore, /proc it's own filesystem, not part of /, so it would not affect space on /."
I don't fully understand that, but i can say that various parts of the system are taking 128TB for /proc/kcore as a serious figure, as per the bug report quoted in 1st post.

So, different parts of system are saying different things! As can be seen below:

1st, df -h
patrick@patrick-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
none                  1.4G  316K  1.4G   1% /dev
none                  1.4G  156K  1.4G   1% /dev/shm
none                  1.4G   84K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
/dev/sda8             4.6G  399M  4.0G   9% /var
/dev/sda10             91G  6.8G   79G   8% /home
/dev/sda9             4.6G  138M  4.3G   4% /tmp
/dev/sda7             4.6G  2.3G  2.2G  52% /usr
/dev/sdb1             1.9G  243M  1.7G  13% /media/USB DISK

As you see, /var, /home, /tmp, /usr each have their own partition. So / should be pretty small - not 2.2GB, i think.

Disk Usage Analyzer has these major figs:
/       100%    3.5GB        21 items (but it only lists 17 and /proc is not in list)
/usr   58.8%  2.1GB        10 items
/lib     17.0%  616.6MB   110 items
/var    7.2%   260.3MB     14 items
/home  7.1%  256.5MB      4 items
/media  6.7%  242.8MB      1 item
all remaining libs. are smaller (<100MB)

So, yes the above listing says / is full, but it gives a funny figure - 3.5 instead of 2.3GB, suggesting all is not well with the list?

Finally, when i put Nautilus up, and select Properties for /proc in / i get:
        Proc Properties

Basic

Name:        proc

Type:        folder (inode/directory)

Contents:     42,090 items, totalling 128.0 TB
        (some contents unreadable)

Location:    /

Volume:        unknown

Free space:    unknown

Confusing picture, but there we are. Will be very glad of any and all light!

---

### Post by mcduck on 2011-03-11
Actually 2,2 GB for root isn't much at all, not even with a separate partition for /usr. 2,3GB root partition is rather small and you should increase it's size at least a bit.

You'd probably use your disk space more efficiently by keeping /var, /usr and /tmp on the root partition.

The Disk Usage Analyzer is a pretty tricky tool to understand, don't let it confuse you. It's not for analyzing the available space on a disc or a partition, but for analyzing *how much the files on selected partitions use space*, and how much that's compared to the available space on the directory you are viewing at the moment.

Based on the Disc Usage Analyzer output, you were viewing all /, /usr, /lib, /var, /home and /media at the same time. So that's actually several partitions, thus the total size is larger than just your root partition.

..and yes, your error is caused by root partition being full, contents of /proc have nothing to do with it, they don't exist on your disc.

---

### Post by Seq on 2011-03-11
> **mcduck said:**
> Actually 2,2 GB for root isn't much at all, not even with a separate partition for /usr. 2,3GB root partition is rather small and you should increase it's size at least a bit.

I concur. I just did a check on my work machine (Excluding /var, /home, /tmp, /usr), which has very little installed on it and no experimentation with new packages and I'm already at 1G.

As an aside, I thought there were problems with Ubuntu's startup scripts not working properly with an external /var/lib. Has this been resolved?

```
$ sudo du -xchs bin/ boot/ etc/ lib/ media/ mnt/ opt/ root/ sbin/ selinux/ 
6.5M	bin/
147M	boot/
19M	etc/
837M	lib/
8.0K	media/
16K	mnt/
4.0K	opt/
1.2M	root/
7.9M	sbin/
4.0K	selinux/
1018M	total
```


> **mcduck said:**
> You'd probably use your disk space more efficiently by keeping /var, /usr and /tmp on the root partition. Or use LVM so you can resize as needed.

> **mcduck said:**
> The Disk Usage Analyzer is a pretty tricky tool to understand, don't let it confuse you. It's not for analyzing the available space on a disc or a partition, but for analyzing *how much the files on selected partitions use space*, and how much that's compared to the available space on the directory you are viewing at the moment..

This is true. It also will count hardlinks multiple times, so while it can show you what files are taking up space, the totals will be incorrect.

> **mcduck said:**
> Based on the Disc Usage Analyzer output, you were viewing all /, /usr, /lib, /var, /home and /media at the same time. So that's actually several partitions, thus the total size is larger than just your root partition.

Under preferences, you can disable your other partitions from being included in the regular filesystem scan.

---

### Post by Seq on 2011-03-11
> **basicsearcher said:**
> "Furthermore, /proc it's own filesystem, not part of /, so it would not affect space on /."
I don't fully understand that, but i can say that various parts of the system are taking 128TB for /proc/kcore as a serious figure, as per the bug report quoted in 1st post.

/proc/kcore is not a real file, and it is not on a real filesystem. It could say it takes up a fifteen petabytes, but that still doesn't mean it exists. /proc as a whole is low-level access to stuff in the kernel, and /proc/kcore is a low-level access to your systems memory. You're running 64-bit and a combination of things (probably chipset) have limited you to 128TB of address space, hence the 128TB fake memory file. The fact that all of that memory can't be mapped (unless you've got a lot of swap) doesn't matter.


> **basicsearcher said:**
> So, different parts of system are saying different things!

I agree that it is confusing. df seems to have special logic to skip /proc and /sys, both of which don't really exist. DUA seems to do the same. Nautilus should probably exclude them too, and that seems to be what the bug you linked to was indicating.

If you run `mount`, you will see a proc, sys, and possibly some other fake filesystems that are currently mounted that df didn't report.

> **basicsearcher said:**
> Confusing picture, but there we are. Will be very glad of any and all light!

Basically:

[LIST]
[*]nautilus is reporting confusing information, ignore it.
[*]df indicates your root is full. Listen to it.
[/LIST]

---

### Post by basicsearcher on 2011-03-11
Thanks a lot, Seq, mcduck, gradinaruvasile. Finally, finally, i got it.

I was told (by a Debian user) that 1GB would be enough for root. Now i see that df was telling the truth, and 2.3GB isn't enough. So if i put root up to 4GB, say (shrinking the other partitions to make space first) then all will be well!

I will try this with gparted (i have backup of my data). Hopefully, i won't have to re-install.

LVM sounds interesting. Perhaps i'll leave that until the next LTS comes out next year.

Thanks again, guys.

---

### Post by b0b138 on 2011-03-11
2.3 isn't close to enough. You've got plenty extra in /var and /tmp.

IMO though, all these separate partitions are pretty pointless and an extra headache. /, /home, and swap are sufficient.

---

### Post by basicsearcher on 2011-03-12
O.k. b0b138. So if i make root (alone) 10GB - is that nearer the mark? & to combine /var, /tmp, /usr with root, at its new combined size, i'll need to reinstall, surely?

If that's what i need to do, so be it. Thanks for the post.:D

---

### Post by Paqman on 2011-03-12
A reinstall would be the easy way out, yes. 10GB should be fine, unless you do anything that creates monster temp files, like authoring DVDs. Even if you were doing that a lot, 20GB would be more than sufficient.

---

### Post by basicsearcher on 2011-03-14
Thanks, b0b138, and thanks to all who helped me get over this. Gparted did the job for me today, and i sent them a grateful donation. Next time i install, i will do as you all suggest, and simplify the Ubuntu setup, so that i have  /, /home, and swap only.

Well done! My first venture into posting has been a real success.

---

