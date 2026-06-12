---
title: "Optimal parition size for ubuntu &amp; Win7 dual boot 500GB"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by cjsiva on 2011-06-02
I have a HP laptop with AMD 64bit, 4GB RAM, 500GB HDD. I would like to install ubuntu 11 on it with my current Win7 as a dual boot. Could someone please let me know what is optimal size I need to partition for Windows and Linux + data storage that needs to accessible on both(I'm not sure if I can access Linux data on windows but I know other way is possible). I'm not a game user or heavy video editing user except some photo shop editior.  I would really appreciate if you could give me the break down on
currently I have about ~450GB of C drive
1. Win 7 for OS
2. Linux for OS (swap space, etc)
3. Data parition ( ideally want to access this from linux + windows) 

In the past I had used windows partition utility to repartition and made them unallocated and done linux installation from windows. BTW from which system I need to do the partition. 
All your help is highly appreciated.

---

### Post by jtarin on 2011-06-02
I put all my data and movies,music etc on an external USB 1TB drive.The only thing I have on my Operating System drives are application programs.sda5 is Ubuntu.sda1 is Win7.The Windows and Ubuntu are on a drive that is 300GB's and divided into 3 partitions. The balance of that drive is used for dual backups of both systems....one backup on the 300 and another mirror image on the 1TB. 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              79G   36G   40G  48% /

/dev/sda1             103G   22G   81G  21% /media/BAE8CB58E8CB1195_
```

---

### Post by mcduck on 2011-06-02
It really just depends on how much your own personal files are gong to take space. :)

For Ubuntu itself, and programs, something around 10-20GB should be enough. Add as much to that value as you think your own stuff would take (unless you plan on using a separate /home partition)

Swap partition should be equal (or larger) than the amount of installed RAM, so I recommend going for a 4GB swap. Or, if you never suspend your computer, even less than that would be OK.

Also, the best system to do the partitioning from is Ubuntu's installer. :)

---

### Post by vkbidve on 2011-06-02
What I suggest is:

1. Keep around 60 GB (which is much more than sufficient) for your Win 7 partition. This will be C drive.
2. Keep around 370 GB for your data partition. Format this as NTFS partition. This will be drive D. Linux and Win 7 both can access NTFS partitions very happily.
3. Keep 4 GB (equal to RAM size) as Swap area for Linux.
4. Rest 30 GB is much more than sufficient for Linux installation. Choose Ext3 or Ext4 as file system for this.

If you are planning to install more than one linux distro, then you can keep more partitions for them. I don't think any of linux distro (even after installing GNOME, KDE, Xfce, LXDE, Open Office, Libre Office and hundreds of many applications all at once) will ever go beyond 20 GB. Still I suggested 10 GB extra in point 4 above, as remastering your installation lateron generally needs this extra space.

You can use 'Ease Us Partition Manager' for this. This is freeware and can create Linux file systems even while working in Windows. Go to [http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)  for download.

---

### Post by vkbidve on 2011-06-02
The Ease Us Partition Master will take care of your existing data while shrinking the existing big partition. I am not sure whether ubuntu installer's partition manager does this or not.

---

### Post by mcduck on 2011-06-02
> **vkbidve said:**
> The Ease Us Partition Master will take care of your existing data while shrinking the existing big partition. I am not sure whether ubuntu installer's partition manager does this or not.

It does.

There are very few reasons to use any other tool for partitioning, as you will anyway need to use Ubuntu's partitioning tool during the install. Might as well let it do the partitioning at the same time. :)

---

### Post by vkbidve on 2011-06-02
> **mcduck said:**
> It does.

There are very few reasons to use any other tool for partitioning, as you will anyway need to use Ubuntu's partitioning tool during the install. Might as well let it do the partitioning at the same time. :)

OK. No issues then.

---

### Post by Mark Phelps on 2011-06-02
Actually, there ARE issues with using Ubuntu's partitioning tool to shrink Win7OS partitions -- as it has demonstrated in the past to sometimes corrupt the Win7 filesystem in the process.

Safest approach is to use the Win7 Disk Management utility to do the shrinkage -- and then reboot into Win7 a couple of times to let it do any filesystem adjustments.

Don't know about EASEUS Partition Master -- it may be OK, since it's an MS Windows tool.

---

### Post by Legendary_Bibo on 2011-06-02
> **Mark Phelps said:**
> Actually, there ARE issues with using Ubuntu's partitioning tool to shrink Win7OS partitions -- as it has demonstrated in the past to sometimes corrupt the Win7 filesystem in the process.

Safest approach is to use the Win7 Disk Management utility to do the shrinkage -- and then reboot into Win7 a couple of times to let it do any filesystem adjustments.

Don't know about EASEUS Partition Master -- it may be OK, since it's an MS Windows tool.

I think those bugs have been fixed, and it only happened rarely. I created my Windows 7 partition after installing Ubuntu and they play along just nicely.

---

### Post by cjsiva on 2011-06-02
Thanks a lot vkbidve and others for your replies. I'm planning to install ubuntu from windows installer version. Will the linux installer see my 450GB in total and allow to me parition them as I go. I hope this wouldn't cause a problem in Windows seeing those NTFS data partition right?. Also I read in this forum that ext4 is faster than ext3(is this for primary linux partition or for both swap and linux) and I believe there would be an option in linux installer to do a NTFS as well.
Thanks.

---

### Post by cjsiva on 2011-06-02
Now I'm confused about Wubi and Clean install,all these time I thought there was no difference. But there is, now I want to do a clean install without affecting my Windows. Should I do paritions etc from windows before starting linux installtion? 
I mean NTFS partition etc should I do resize C:\ drive to say 60GB and 370 NTFS from windows and make the reset as unallocated then start linux installtion and install them on the unallocated partition and give 4GB swap + 30GB as ext3/4 from linux. Any help is highly appreciated.

Experts please help me. :-)

---

### Post by vkbidve on 2011-06-03
> **cjsiva said:**
> Now I'm confused about Wubi and Clean install,all these time I thought there was no difference. But there is, now I want to do a clean install without affecting my Windows. Should I do paritions etc from windows before starting linux installtion? 
I mean NTFS partition etc should I do resize C:\ drive to say 60GB and 370 NTFS from windows and make the reset as unallocated then start linux installtion and install them on the unallocated partition and give 4GB swap + 30GB as ext3/4 from linux. Any help is highly appreciated.

Experts please help me. :-)

Actually, I am not an "Expert", but still trying to help others by sharing knowledge and experience and views. 

Yes, Wubi creates some problems on many machines. Clean install is most recommended for all times. If you want to resize your Win 7 partition within windows itself, then there is no issue at all. Use windows' built-in disk utility or use Ease-Us, anything. You need not put rest of the drive unallocated, as ubuntu installer will format them as ext3/4 whatever you choose. If u put it unallocated, even then you have a chance to partition it during installation. No issues. Do whatever you would be more interested in learning in. Nothing will go wrong.

BTW, swap partition is neither formatted, nor does it hold any file system. It just holds a raw image of RAM contents. So ext3/4 is not applicable to swap as you said in your post #10.

---

### Post by cjsiva on 2011-06-03
vkbidve,Thanks for clarification

---

