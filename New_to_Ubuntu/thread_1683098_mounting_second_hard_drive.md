---
title: "mounting second hard drive"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by j0hnnyv on 2011-02-07
I first installed 10.04lts through wubi a few months ago, and used my windows recovery hard drive d:\ to do it. everything was fine, and i could easily access my c:\ windows drive and read/write files. i had an error the other day after a kernel upgrade in 10.10(i upgraded almost immediately from 10.04lts and went through grub errors because of wubi and fixed all of them). 

Fast forward and I ended up using the live cd with 10.04 and installed it through that and created a new partition in my c:\ to dualboot with win7 and installed there.  This is really what I wanted in the first place, wubi isn't good long term. Well that all worked! I could see my windows files under places > windows and all of that is good.  

I booted into windows and formatted my d:\ which had my old dead ubuntu install. Done, fixed my bootloader so the old wubi entries weren't in there so everything is normal.

NOW, I have a 10gig d: not being used and freshly formatted.  I would love to be able to access that through ubuntu for extra storage.  Here is a screenshot from gparted. I have it set as ext3...ext4 I couldn't get to work.  When it did work and I thought I had this done, the only folder on d: was lost&found/ and I know it wasn't set right.

What can I do in gparted or elsewhere to get this drive usable through here for extra storage. I labeled the drive (ubuntuhd2) I have searched pretty good and couldn't find anything.

I appreciate your help in advance! ):P

---

### Post by LewRockwellFAN on 2011-02-08
I'm not sure I understand the question. Is the point that you want that partition to appear in the places menu? Have you tried getting there through Places,computer and then bookmarking it? If that doesn't do it try searching fstab here in the forum. I think you can control how a partition mounts with fstab but I forget the details. I'd have left this for an fstab expert to answer but for the fact it seems to have been up a surprisingly  long time with 0 answers.

---

### Post by vanadium on 2011-02-08
To have it automatically available after startup, you should indeed "declare" the partition in /etc/fstab.

You better use ext4 for an internal drive (no compatibility issues), so you may want to reformat sda1 to the ext4 file system. In fact, you can "convert" it without reformatting (make sure the drive is NOT mounted before running the command):
```

sudo tune2fs -O extents,uninit_bg,dir_index /dev/sda1

```
(source: [https://help.ubuntu.com/community/ConvertFilesystemToExt4](https://help.ubuntu.com/community/ConvertFilesystemToExt4))

Step 1 -  Make a mount point for the drive. This is in fact an empty directory, where the partition will be mounted.
```

sudo mkdir /mnt/data

```

Step 2 -  Find the unique identifier of the partition in the output of the blkid command
```

sudo blkid

```
Copy the part 'UUID="......"' of the line that starts with /dev/sda1 to the clipboard. You will use it in your /etc/fstab.

Step 3 -  Open the file /etc/fstab as root for editing
```

gksudo gedit /etc/fstab

```
Append a new line for your sda1 partition, which looks like
```

UUID="....."  /mnt/data  ext4   defaults   0   2

```
Paste the 'UUID=..' part from the clipboard: this is specific for your partition.
Save the file and close gedit.

This is it. Mount the drive and check if all is OK with the command:
```

sudo mount -a

```
There should be no output. If you made a mistake, an error message will appear.

If indeed there is no output, all is well and the data on the partition will be accessible when you navigate to /mnt/data.

Next issue will be permissions. In addition, you can make any directory on the new partition easily accessible by putting a link in the home directory of the user. This way, he will never have to navigate out of his home to reach the data.

---

### Post by j0hnnyv on 2011-02-08
Thank you very much.  That was very helpful.  I have done all that you said and there was output, so something isn't right:

johnv@samcro:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

johnv@samcro:~$ dmesg | tail
[ 1181.035556] EXT3-fs: barriers not enabled
[ 1181.052467] kjournald starting.  Commit interval 5 seconds
[ 1181.052829] EXT3-fs (sda1): using internal journal
[ 1181.052837] EXT3-fs (sda1): mounted filesystem with ordered data mode
[ 1200.859583] EXT3-fs: barriers not enabled
[ 1200.859940] kjournald starting.  Commit interval 5 seconds
[ 1200.869551] EXT3-fs (sda1): using internal journal
[ 1200.869568] EXT3-fs (sda1): mounted filesystem with ordered data mode
[ 1550.172092] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 0 failed (50297!=0)
[ 1550.172108] EXT4-fs (sda1): group descriptors corrupted!
johnv@samcro:~$ 



What next?

Thanks!

---

### Post by Rhizoid on 2011-02-08
Did you auto mount an ext3 partition as ext4?

---

### Post by j0hnnyv on 2011-02-08
> **Rhizoid said:**
> Did you auto mount an ext3 partition as ext4?

I did exactly as the post said to do. When I go into gparted now it shows /dev/sda1 as ext4....

---

### Post by Rhizoid on 2011-02-08
> **j0hnnyv said:**
> I did exactly as the post said to do. When I go into gparted now it shows /dev/sda1 as ext4....

...but did you reformat it to ext4 as it was ext3 before?

Just for kicks, re-edit the fstab file and change ext4 to ext3 on the line you added to mount /dev/sda1 then type; ```
sudo mount -a
```

Cheers,

---

### Post by j0hnnyv on 2011-02-08
Same exact error....and no I didn't reformat as ext4. Should I do that through gparted and start this process over?

I had it set before I even posted this thread and I could mount and sort of access it. The only folder was lost&found and it definitely wasnt set up properly...

thanks for your help, let me know.

---

### Post by Rhizoid on 2011-02-08
If you're sure there's no data on sda1 which you'd lose by reformatting it to ext4 there's no reason not to try it.  FWIW a blank ext4 partition will only contain a lost+found folder.

---

### Post by j0hnnyv on 2011-02-08
> **Rhizoid said:**
> If you're sure there's no data on sda1 which you'd lose by reformatting it to ext4 there's no reason not to try it.  FWIW a blank ext4 partition will only contain a lost+found folder.

That worked, now that drive is in /mnt/data

But now there are no permissions as you said.

See screenshot.

---

### Post by j0hnnyv on 2011-02-08
sudo mkdir /mnt/data/myusername
sudo chown myusername:users /mnt/data/myusername
ln -s /mnt/data/myusername ~/data

That fixed all of that.

I am all good now, thanks for all!

---

