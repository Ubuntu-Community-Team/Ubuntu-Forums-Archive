---
title: "Removing Ubuntu Partition and restoring Vista bootloader?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Noise... on 2009-05-02
Due to a new job, I may be needing to switch back to Windows (unfortunately).

I'd prefer not to loose everything on my Windows drive by putting in the recovery disks, so I need to know how to correctly remove Ubuntu, 

Can I use Vista's disk partitioner to do this, then restore the Microsoft Boot Loader with Super Grub Disk?

---

### Post by skymera on 2009-05-02
Check out EasyBCD

I was able to restore my mums Vista bootloader after Ubuntu went mad.

---

### Post by caljohnsmith on 2009-05-02
> **Noise... said:**
> Due to a new job, I may be needing to switch back to Windows (unfortunately).

I'd prefer not to loose everything on my Windows drive by putting in the recovery disks, so I need to know how to correctly remove Ubuntu, 

Can I use Vista's disk partitioner to do this, then restore the Microsoft Boot Loader with Super Grub Disk?
Sure, you could use the Super Grub Disk to restore a Windows MBR (Master Boot Record) to the HDD, and then it is safe to delete the Ubuntu partition. Or if you want to save yourself burning the Super Grub Disk, you can restore a Windows MBR to your HDD while you are in Ubuntu by doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="red"]sda[/COLOR] mbr
```
And change "sda" if the drive in question is different. Anyway, good luck and let me know how it goes or if you run into problems.

Cheers,
John

---

### Post by Noise... on 2009-05-02
> **caljohnsmith said:**
> Sure, you could use the Super Grub Disk to restore a Windows MBR (Master Boot Record) to the HDD, and then it is safe to delete the Ubuntu partition. Or if you want to save yourself burning the Super Grub Disk, you can restore a Windows MBR to your HDD while you are in Ubuntu by doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="red"]sda[/COLOR] mbr
```
And change "sda" if the drive in question is different. Anyway, good luck and let me know how it goes or if you run into problems.

Cheers,
John

Ok, great. 

How about the partition issues? Will I be able to do it from Vista, or do I need something else?

---

### Post by caljohnsmith on 2009-05-02
> **Noise... said:**
> Ok, great. 

How about the partition issues? Will I be able to do it from Vista, or do I need something else?
Probably Vista will be more than happy to delete your linux partition... :biggrin: But seriously, I have no more than 10 minutes of personal experience using Vista's Disk Management Tools, so I don't know for sure how Vista will handle deleting Ubuntu's partition. I think the safest thing to do would be to boot a Ubuntu Live CD, open the gparted partition editor (System > Admin > Partition Editor), and use that to delete your Ubuntu partition. Or maybe even better, you could use gparted to simply reformat the Ubuntu partition as NTFS so you can use it as a data partition accessible in Vista. 

Cheers,
John

---

### Post by Noise... on 2009-05-02
> **caljohnsmith said:**
> Probably Vista will be more than happy to delete your linux partition... :biggrin: But seriously, I have no more than 10 minutes of personal experience using Vista's Disk Management Tools, so I don't know for sure how Vista will handle deleting Ubuntu's partition. I think the safest thing to do would be to boot a Ubuntu Live CD, open the gparted partition editor (System > Admin > Partition Editor), and use that to delete your Ubuntu partition. Or maybe even better, you could use gparted to simply reformat the Ubuntu partition as NTFS so you can use it as a data partition accessible in Vista. 

Cheers,
John

That's the issue - I don't have a Live CD. I downloaded Ubuntu Studio 8.04 a while ago, and it lacks the live functions.

What about just going through the install process, and deleting the Ubuntu partition that way? Can Vista's partition editor recognize free space?

---

### Post by caljohnsmith on 2009-05-02
> **Noise... said:**
> That's the issue - I don't have a Live CD. I downloaded Ubuntu Studio 8.04 a while ago, and it lacks the live functions.

What about just going through the install process, and deleting the Ubuntu partition that way? Can Vista's partition editor recognize free space?
You could instead delete the Ubuntu partition while you are in Ubuntu using the "fdisk" command:
```
sudo fdisk /dev/sda
```
Press "p" to get a listing of your partitions, press "d" to delete a partition, and then enter the number of the Ubuntu partition. Press "p" again to make sure you deleted the correct partition, and if your partition table looks good, press "w" to write the changes to the HDD. Then immediately reboot, and when you boot into Vista (I assume you first either ran the lilo command or used the Super Grub Disk to restore a Windows MBR), you should see the unallocated space where the Ubuntu partition once was, and you could then use Vista's Disk Management to create a new NTFS partition with that space. Let me know how that goes or if you run into problems.

John

---

### Post by -kg- on 2009-05-02
Or alternatively you could download the [GPartEd Live CD,]("http://gparted.sourceforge.net/") which is specifically for partitioning operations.  It also isn't too large...around 80 or 90 MB, if my memory serves me.  With that you can easily delete all your Linux partitions, then boot into Vista and let it's Disk Management tool to expand the partition into the free space.

Bummer, though.  Why is it that you need to completely get rid of Linux?  Not enough hard drive space?  I personally would try to keep a minimal install while expanding Vista enough that it had sufficient space; that is, unless it was a company laptop and they required me to take it off.

---

### Post by kansasnoob on 2009-05-02
Wow! My day just got better!

Caljohnsmith is back!

Don't over do it my friend!

Outside of that I wonder what possible objection there could be to using Ubuntu on a small partition:confused:

But aside from that Vista is easy to restore:

You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

---

### Post by raymondh on 2009-05-02
Vista's disk managemeent tool can delete the ubuntu partition.  Right click on the partition you choose to delete (be careful in choosing the right partition) and go from there.  After deleting and making the space "free" / "unallocated", you then click on the vista partition to expand it.  From there, remember to defrag the new, bigger Vista partition.

Now on to fixing the MBR.  With the Vista install disc, navigate to system repair and command prompt.  type

```
bootrec.exe/FixMbr
```

Reboot.  Good luck.

Raymond

---

### Post by Noise... on 2009-05-02
Thanks guys. I'm not set on doing it just yet. I may keep Ubuntu around. 

But, basically what it comes down to is that I'd be in Windows all day long, and I simply won't have a reason to boot into Ubuntu. Aside from that, my iPod Touch and all of my games still only work with Windows, so I'll also be using Windows for that. 

I'll pretty much just have zero reason to boot into Ubuntu. Right now I use it for my web browsing during the day, which is what I do most of the time.

For now, will Vista's partitioner work to just make the Vista partition larger? It's at the bare minimum now, while Ubuntu's partition is most of the hard drive.

---

### Post by Noise... on 2009-05-03
Bump. I'm just going to repartition Windows for now so that I have room to install the programs I need.

Will Vista's partitioner do that?

---

### Post by cariboo on 2009-05-03
Vista disk management tools will delete the Ubuntu partitions, and allow you to resize you VIsta partition. **Back up any important data before doing anything.**

---

### Post by Noise... on 2009-05-03
> **cariboo907 said:**
> Vista disk management tools will delete the Ubuntu partitions, and allow you to resize you VIsta partition. **Back up any important data before doing anything.**

Will it just let me resize the Ubuntu partition, rather than just delete it? I'm going to keep Ubuntu for now, unless I really need the space.

---

### Post by Noise... on 2009-05-03
Ok. I'm posting from Vista now, and the partitioner can't touch the Ubuntu partitions to shrink them.

What else can I do? I really don't want to have to download Gparted, as 90MB is a lot for me to download on my 5GB a month bandwidth limit. :(

---

### Post by zvacet on 2009-05-03
I think that Gparted is best option for job you want to do.It is not to big download(same as better mp3 file),or you can ask your friends to download it for you.

---

### Post by -kg- on 2009-05-03
> **zvacet said:**
> I think that Gparted is best option for job you want to do.It is not to big download(same as better mp3 file),or you can ask your friends to download it for you.

Exactly, or you can use the partitioning tool off the Ubuntu Live CD.

Vista's Disk Management partitioner can't shrink (or create, or move, or any other operation except to delete) an ext2/3/4 partition.  You must use a partitioning tool that will work with those types of partitions.

You will need to shrink your Linux partition(s) with GPartEd (or a compatible partition editor), then use Vista's Disk Manager to resize your Vista partition to expand it into the free space that you created.  I've never had any particular problem with using GPartEd to perform operations on NTFS partitions, but I have heard that others have, so using Vista's partitioner is the safest bet for performing operations on the Vista partition itself.

Be forewarned though; I'm not sure, but it is possible that the UUID (Universally Unique Identifier, which is assigned to each partition to identify it absolutely) might change on the Linux partition(s), making GRUB unable to boot it. If Ubuntu becomes unbootable after these operations, just come back here and make another post with the problem.  This type of issue is easily solvable, and you will be helped with it.

---

