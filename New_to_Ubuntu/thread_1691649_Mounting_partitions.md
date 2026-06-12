---
title: "Mounting partitions"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by vendetta993 on 2011-02-20
I replaced XP with Xubuntu, and i added mount points as in some tutorial i've seen.

On partition that was once system partition (C:) i typed "/" (without "").

On the other 2, i typed something like this :

/media/D (the partition that was on XP D:)
/media/E (the partition that was on XP E:)

Of course, i formated all the partitions into Ext4.
Is it normal that these two partitions need to be mounted ? Why does Xubuntu mount them ? Why aren't they as C: ? And is this normal ?

---

### Post by Morbius1 on 2011-02-20
> **vendetta993 said:**
> Is it normal that these two partitions need to be mounted ? 
You have the option during your initial install to have the installer create fstab entries that will automount these partitions on boot. If you don't do it during the initial install then you will have to create fstab entries yourself.
> Why does Xubuntu mount them ?Don't understand the question. They are mounting because you told them to mount by adding an fstab entry. 
> Why aren't they as C:The whole concept of giving partitions letters and calling a partition a "drive" is a Windows thing not a Linux/Unix thing.
> And is this normal ?Yes

---

### Post by yeats on 2011-02-20
> **vendetta993 said:**
> I replaced XP with Xubuntu, and i added mount points as in some tutorial i've seen.

I understand this to mean that you installed Xubuntu over Windows XP and somehow preserved the Windows partitions.  Is that correct?

> On partition that was once system partition (C:) i typed "/" (without "").

On the other 2, i typed something like this :

/media/D (the partition that was on XP D:)
/media/E (the partition that was on XP E:)

Where did you type this?

> Of course, i formated all the partitions into Ext4.

If you formatted the previously Windows partitions to be Ext4, that would have removed all the data in those partitions.  Did you back that data up before doing this?

> Is it normal that these two partitions need to be mounted ?

> And is this normal ?

What you've set up here is not typical, so whether it's normal or not is something you'll have to clarify. ;-)

> Why does Xubuntu mount them ? 

[X]ubuntu will mount by default whatever is listed in the file /etc/fstab - you can view that file to see what's listed.

> Why aren't they as C: ?

"C:", "D:", and the like are all Windows-assigned constructs.  In Linux, the base filesystem is "/", pronounced "root" or "the root directory".  In the place of "D:" and other commonly used Windows letter assignments, Linux systems use /mnt or /media on more recent systems (it's /media on Ubuntu).

Does that help?

---

### Post by vendetta993 on 2011-02-20
> **Morbius1 said:**
> You have the option during your initial install to have the installer create fstab entries that will automount these partitions on boot. If you don't do it during the initial install then you will have to create fstab entries yourself.
Don't understand the question. They are mounting because you told them to mount by adding an fstab entry. 
The whole concept of giving partitions letters and calling a partition a "drive" is a Windows thing not a Linux/Unix thing.
Yes

Ok if that's normal, i'm just not used to see anything mounted besides ISO images i mount in daemon tools :)

Yeah i know my questions causes a lot of confusion :lolflag: It's just when i click on Computer on Ubuntu, i see Filesystem and the other two partitions. The other two partitions are mounted. It looks like this, and i'm just asking if this is normal :

EDIT 2

So this is normal, right ?

> **yeats said:**
> I understand this to mean that you installed Xubuntu over Windows XP and somehow preserved the Windows partitions.  Is that correct?



Where did you type this?



If you formatted the previously Windows partitions to be Ext4, that would have removed all the data in those partitions.  Did you back that data up before doing this?





What you've set up here is not typical, so whether it's normal or not is something you'll have to clarify. ;-)

 

[X]ubuntu will mount by default whatever is listed in the file /etc/fstab - you can view that file to see what's listed.



"C:", "D:", and the like are all Windows-assigned constructs.  In Linux, the base filesystem is "/", pronounced "root" or "the root directory".  In the place of "D:" and other commonly used Windows letter assignments, Linux systems use /mnt or /media on more recent systems (it's /media on Ubuntu).

Does that help?

Yes, i was trying to preserve that :)

When i was installing, when i was configuring partitions and formating them manually, i formated all of them in Ext4, and added mount points as described above.

Yes of course, I'm maybe a beginner in Linux, but certainly not that stupid in other things :D

Yeah I've typed /media/D and /media/E , they look mounted like in the picture, and the filesystem looks just like that, that's normal, right ?

---

### Post by yeats on 2011-02-20
> So this is normal, right ?

Yes, that's the way a Windows filesystem looks in Ubuntu.  Looks like you're okay.

---

### Post by vendetta993 on 2011-02-20
Ah bad picture, i'll upload a picture when i installed and formated all the partitions in Ext4, just to be sure if i've done everything correctly.

[IMG]http://img91.imageshack.us/img91/4413/screenshotap.png[/IMG]

Filesystem and 2 additional partitions, all of them formated to Ext4, so this is normal, and this is how it's supposed to look ?

---

### Post by Morbius1 on 2011-02-20
That depends. Based on your description of what you did that is not correct:
> On the other 2, i typed something like this :

/media/D (the partition that was on XP D:smile:
/media/E (the partition that was on XP E:smile:I'm betting that you did not create the "D" and "E" mountpoints first. Or you created the fstab entries when they were NTFS and then reformatted them so your fstab entries are being ignored.

Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by vendetta993 on 2011-02-20
When i was installing, in this window i configured everything : 

[IMG]http://img12.imageshack.us/img12/3632/screenshot1rbk.png[/IMG]

And for the sda5 and sda6 (D and E) mountpoints were :

/media/D
/media/E

---

### Post by Morbius1 on 2011-02-20
Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```That will tell us what's up.

For example, your "D Drive" in fstab should look something like this:
```
UUID=e92eaf02-ff61-4db0-9397-35f1aadb98e8 /media/D ext4 defaults        0       2
```The UUID number will be different but the general form of the fstab entry is how the installer adds things to fstab.

---

