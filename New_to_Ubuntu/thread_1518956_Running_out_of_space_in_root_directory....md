---
title: "Running out of space in root directory..."
date: 2010-06-27
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-27
When I partitioned my new HDD, I set aside 9 Gb for the root directory, then created a separate /home partition (with 14 Gb).

I'm looking at gparted and it's showing / to only have 467 MiB free (with 8.7 Gib used). I can't see what is using up all the disk space. How can I determine what's using up all that space?

Thanks,

Andy

---

### Post by warfacegod on 2010-06-27
Got to: Applications> Accessories> Disk Usage...

You might want to set the Preferences to display sda1 only.

As an aside. Why on Earth do have so many partitions inside your /home partition. At least, that's what it looks like.

---

### Post by philinux on 2010-06-27
[RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by akelsall on 2010-06-27
warfacegod, I should have mentioned I look at Disk Usage Analyzer as well. That didn't help (see attached snapshot from DUA). 

To answer your question, I don;t :)    I have several in the extended partition. I did this so that if one partition went bad, I wouldn't lose everything.

Thanks,

Andy

---

### Post by da burger on 2010-06-27
Go to Edit>Preferences in DUA and untick all but the partition you have root on. Then run it again.

---

### Post by sanderj on 2010-06-27
> **akelsall said:**
> When I partitioned my new HDD, I set aside 9 Gb for the root directory, then created a separate /home partition (with 14 Gb).

I'm looking at gparted and it's showing / to only have 467 MiB free (with 8.7 Gib used). I can't see what is using up all the disk space. How can I determine what's using up all that space?

Thanks,

Andy

See [http://ubuntuforums.org/showpost.php?p=9492364&postcount=7](http://ubuntuforums.org/showpost.php?p=9492364&postcount=7)

---

### Post by akelsall on 2010-06-27
Thanks sanderj, but that didn't help either. It didn't really shed any light on what is taking up all the space in "/". I'm stumped. I thought setting aside nearly 10 Gb would be fine. What could "eating up" nearly all of the root directory space?

---

### Post by akelsall on 2010-06-27
Well, I just found part of the problem. I was scanning some images today, and had aborted a couple of them. Apparently, xsane didn't do a very good job of cleaning up, as I found a 3.6G file in my /tmp directory. Now I'm showing 5.4 GiB available (out of 9.2 GiB total). 

The commands I used were **sudo find / -size +500M | more** and **sudo find / -size +1G | more**



Still looking for ideas of where else I can find space being used that can be cleaned up. Any ideas?

Thanks,

Andy

---

### Post by sanderj on 2010-06-27
> **akelsall said:**
> Thanks sanderj, but that didn't help either. It didn't really shed any light on what is taking up all the space in "/". I'm stumped. I thought setting aside nearly 10 Gb would be fine. What could "eating up" nearly all of the root directory space?

Start by posting the output of the one-liner I referred to ...

---

### Post by warfacegod on 2010-06-27
> **akelsall said:**
> Thanks sanderj, but that didn't help either. It didn't really shed any light on what is taking up all the space in "/". I'm stumped. I thought setting aside nearly 10 Gb would be fine. What could "eating up" nearly all of the root directory space?

I use a 10 GB partition for / and it's never gotten more than 3.3 GB full. In that regard you should be fine. I've read several threads about this previously and, if I recall, ureadahead was the culprit.

Other things to try:

Get Ubuntu Tweak. It has some cleaning tools that are quite good. It's unlikely that you'll get back all that space with it but it may help some.

Check the /tmp folder. It can get full if it doesn't delete temp stuff like it's supposed to.

Run: ```
sudo apt-get auto remove
```

---

### Post by Paqman on 2010-06-27
> **akelsall said:**
> What could "eating up" nearly all of the root directory space?

Well, having a bit of a clean out could help out.

**Get rid of old kernels**
Open up Synaptic, hit the filter on the left to show "installed" package only the search for "linux-image". Uninstall all but the latest kernel or two. Do not uninstall "linux-image" itself, just the ones listed as linux-image-2.6.whatever. You have to keep the latest one, or your machine won't boot.

**Clean up the package manager**
Open a terminal and run:
```
sudo apt-get autoclean && sudo apt-get autoremove
```
This gets rid of obsolete packages in the cache or installed on the system.
If you want to completely clear the package manager's cache use the following instead of autoclean:
```
sudo apt-get clean
```

**Empty your trash**
Go to "Deleted Items" and click the "Empty deleted items" button. Likewise for any other users.

**Find any junk owned by root**
By running the Disk Usage Analyser as root by hitting Alt-F2 and entering:
```
gksu baobab
```
If you have got lots of junk owned by root let us know and we'll help you get rid of it safely. Deleting root-owned files is potentially risky if you you're not sure how to do it properly.

---

### Post by akelsall on 2010-07-03
Paqman, running those two commands helped some as well, but the biggest chunk were those "scraps" that were left from aborted scans (I aborted of couple of images I was scanning, and they were just left in my $HOME/.Trash-0/ directory.

Thanks to everyone for their suggestions. 

Andy

---

