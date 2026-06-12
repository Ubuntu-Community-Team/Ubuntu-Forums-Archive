---
title: "Disk Space available=13.6 Disk Space free=12.7"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-08-27
I have tried to google this but I can't seem to figure it out, I have tried

```
sudo rm /var/cache/apt/archives/*.deb
```

and

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```
 
And still nothing and I don't know how else to be able to use that space.  So if anyone knows why, I would much appreciated if you let me in on it, thanks in advance for any help.

---

### Post by NoaHall on 2009-08-27
What's your problem?

---

### Post by Grifulkin on 2009-08-27
> **NoaHall said:**
> What's your problem?

My disk space availability is 13.6 GB but my disk space free is 12.7 GB, so I'm missing .9GB somewhere.

---

### Post by NoaHall on 2009-08-27
You know about the difference between bytes and bits right? There's your "missing" space. I think.

---

### Post by LewRockwell on 2009-08-27
> **Grifulkin said:**
> My disk space availability is 13.6 GB but my disk space free is 12.7 GB, so I'm missing .9GB somewhere.

nevermind

been answering too many questions regarding small capacity drives...obviously...

.

---

### Post by jerome1232 on 2009-08-27
I think it's just ext3 reserving 5% of the disk space for root. That way if you disk fills up completly and your system becomes unusable by the regular user you can still get a root prompt and clean up some space.

---

### Post by DaithiF on 2009-08-27
is this an ext partition?  if so, can you run & post the output from
```
sudo tune2fs -l /dev/<yourpartition>
```

if you don't know the partition, run 
```
sudo fdisk -l 
```

(the parameters to both commands are lower-case L)

---

### Post by Grifulkin on 2009-08-27
> **NoaHall said:**
> You know about the difference between bytes and bits right? There's your "missing" space.

Yes, but that doesn't seem right I had 13.3 GB free the other day and downloaded some stuff and then earlier everything I downloaded I  got rid off, but it still says 12.7 GB.  If that is the reason than I apologize for asking such a dumb question I didn't think that was the reason.

---

### Post by Grifulkin on 2009-08-27
> **DaithiF said:**
> is this an ext partition?  if so, can you run & post the output from
```
sudo tune2fs -l /dev/<yourpartition>
```

if you don't know the partition, run 
```
sudo fdisk -l 
```

(the parameters to both commands are lower-case L)

```

ryan@Ubuntu:~$ sudo tune2fs -l /dev/sda1
[sudo] password for ryan: 
tune2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          6a8fc764-0bb9-4cd6-80c7-8fba7ad1c6fc
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1160992
Block count:              4638760
Reserved block count:     231938
Free blocks:              3554303
Free inodes:              1034814
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1022
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8176
Inode blocks per group:   511
Flex block group size:    16
Filesystem created:       Fri Aug  7 20:43:39 2009
Last mount time:          Thu Aug 27 09:33:54 2009
Last write time:          Thu Aug 27 09:33:54 2009
Mount count:              4
Maximum mount count:      31
Last checked:             Mon Aug 24 14:50:45 2009
Check interval:           15552000 (6 months)
Next check after:         Sat Feb 20 13:50:45 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       50284
Default directory hash:   half_md4
Directory Hash Seed:      d749ccdb-3354-4f32-9988-259b9fadce89
Journal backup:           inode blocks

```

---

### Post by NoaHall on 2009-08-27
> **Grifulkin said:**
> Yes, but that doesn't seem right I had 13.3 GB free the other day and downloaded some stuff and then earlier everything I downloaded I  got rid off, but it still says 12.7 GB.  If that is the reason than I apologize for asking such a dumb question I didn't think that was the reason.

Meh, it seems I was wrong. Well, it was a good guess. Because on mine, the file system is marked as used.

---

### Post by drs305 on 2009-08-27
> **Grifulkin said:**
> Yes, but that doesn't seem right I had 13.3 GB free the other day and downloaded some stuff and then earlier [COLOR="DarkRed"]everything I downloaded I  got rid off[/COLOR], but it still says 12.7 GB.  If that is the reason than I apologize for asking such a dumb question I didn't think that was the reason.

Have you emptied your trash *and* root's trash? The files in the trash bin continue to take up space until they are permanently removed. Some users forget to empty root's trash. Click on the "Trash" link in my signature line for a guide I wrote about the subject.

---

### Post by Grifulkin on 2009-08-27
But to be honest I'm not totally retarded people I know that the filesystem uses space, but this hard drive is only 20 GB to begin with and the partition is only 18 GB.  Now having said that, if I overlooked something you could be nice about it, I'm not a complete n00b but if I didn't have a reason to ask, say the things I downloaded got deleted and I ended up with the same amount of space, this question wouldn't be in the forums, but I had a reason to ask so I asked.

---

### Post by DaithiF on 2009-08-27
reserved blocks 231938 x block size 4096 = your reserved space in bytes., so roughly the 0.9GB you're missing.

This is space the system reserves for its use so it can keep running if the rest of the filesystem has filled up.  You can reduce it if you wish, particularly if this is a data partition (as opposed to where / is mounted)
```
sudo tune2fs -m X /dev/yourpartition
```
where X is a number representing the percentage to reserve ... 1, 2, 3 etc (5% is the existing value)

---

### Post by Grifulkin on 2009-08-27
> **DaithiF said:**
> reserved blocks 231938 x block size 4096 = your reserved space in bytes., so roughly the 0.9GB you're missing.

This is space the system reserves for its use so it can keep running if the rest of the filesystem has filled up.  You can reduce it if you wish, particularly if this is a data partition (as opposed to where / is mounted)
```
sudo tune2fs -m X /dev/yourpartition
```
where X is a number representing the percentage to reserve ... 1, 2, 3 etc (5% is the existing value)

Thank you, seems like a dumb question now.  I must not have deleted everything I downloaded then.  Thank you everyone though, sorry again for the silly question.

---

