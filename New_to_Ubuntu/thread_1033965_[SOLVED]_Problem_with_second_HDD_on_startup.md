---
title: "[SOLVED] Problem with second HDD on startup"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by floatingpoint on 2009-01-07
I had a second HDD while Windows was installed, and I put all my stuff (music, videos, pics, documents) onto it for the switch. When I got Ubuntu up and running I couldn't get into the drive, because it's NTFS (yeah?). So I searched and found out how to use the command line to force mount it, and that worked fine, 

Only problem now is, when I boot up, I have to navigate to the disk before it's recognised. This is a hassle, one particular repercussion being that when I start an application such as rhythmbox, my entire library of music is missing.

Is there a solution that would have the second HDD recognised automatically when I log in?

---

### Post by wolfen69 on 2009-01-07
you will need to add an entry to fstab. force mount it and post the output of ```
sudo fdisk -l
```

---

### Post by handydan918 on 2009-01-07
> **floatingpoint said:**
> I had a second HDD while Windows was installed, and I put all my stuff (music, videos, pics, documents) onto it for the switch. When I got Ubuntu up and running I couldn't get into the drive, because it's NTFS (yeah?). Most likely, it was because the NTFS volume had been uncleanly unmounted. That will cause headaches.> 

Only problem now is, when I boot up, I have to navigate to the disk before it's recognised. This is a hassle, one particular repercussion being that when I start an application such as rhythmbox, my entire library of music is missing.

Is there a solution that would have the second HDD recognised automatically when I log in?

Well, yeah. First is to consider reformatting that drive as ext3, if you aren't using it with that OTHER (legacy) O/S. That will be a much more reliable filesystem. 

The rest involves editing /etc/fstab so that the drive is automatically mounted at boot.  You'll want to post your fstab here so we can laugh at you--errr,, I mean analyze it and help you edit it.

---

### Post by floatingpoint on 2009-01-07
The info you asked for:

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10731073

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9638    77417203+  83  Linux
/dev/sda2            9639       10011     2996122+   5  Extended
/dev/sda5            9639       10011     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc989c989

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS
```


There's no OS on the second HDD, just important files. I ought to be able to fit everything onto the main HDD that I'm running Ubuntu from, to format the other, although disk space would be uncomfortably low while I did that ( <2gb ).

---

### Post by floatingpoint on 2009-01-07
While we're at it, I have a third HDD kicking about here, can I simply plug it in and then format it from ubuntu In regular fashion?  /sneakyninjabump

---

### Post by cdmike2k8 on 2009-01-07
You should be able to format it using gparted.

---

### Post by floatingpoint on 2009-01-07
Cool. Any thoughts on the initial problem?

---

### Post by cdmike2k8 on 2009-01-07
First, unmount the drive ```
sudo umount /dev/sdb1
```Then try adding the line in your fstab:```
/dev/sdb1 /media/data ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
```
where /media/data is the folder that you want it to mount to.  Make sure you create the folder /media/data("mkdir /media/data" without quotes in terminal to create the folder). To get to your fstab, open a terminal, and type [/code]sudo nano /etc/fstab[/code] and enter the line above.  Then restart, it should mount automatically.  Good luck, let me know if it doesn't work.
Michael

---

### Post by -kg- on 2009-01-08
> type [/code]sudo nano /etc/fstab[/code] and enter the line above.

Oops!  I'm sure he meant for you to type:

```
sudo nano /etc/fstab
```

instead of the above.

If you would be more comfortable with a GUI-based editor, type:

```
gksudo gedit /etc/fstab
```

and you can use the Gnome Editor to edit the configuration file.  Just click "save" after you enter the line.

Before performing either of the above, I would make a backup copy of your original fstab file:

```
sudo cp /etc/fstab /etc/fstab-backup
```

This will create a backup of your original fstab file, and if you run into problems you can reverse the above command:

```
sudo cp /etc/fstab-backup /etc/fstab
```

and have the original fstab file back in place.

---

### Post by Paqman on 2009-01-08
If you don't want to get into editing /etc/fstab there's a great tool called ntfs-config that will set up access to your ntfs partition in a jiffy.

---

### Post by floatingpoint on 2009-01-08
Thanks for all the advice. I went to bed before you posted, -kg-, so I didn't back up my fstab, glad nothing went wrong! At least not as far as I can tell. 

Keen to use and get acquainted with the command line, so I just used terminal (is it gnome-terminal?). All seems to work fine. I'm still getting used to the way the file system is structured. I take it i could have done ```
mkdir whatever/iwanted/
```?


So, it's all there when I start ubuntu, is that disk quite safe as it is now?

Also, when you mentioned backing up fstab: 
cp = copy   and then the file to be copied followed by the destination to copy it to?

(I hope i'm not overdoing it on the questions :P )

If I did want to format it to a more reliable filesystem, what would I do?

---

### Post by muteXe on 2009-01-08
open up gparted from the command line ("gksudo gparted", i think), then right click on the drive, choose "unmount", then right-click again and select "format to..." whatever you want.

Sitting in a course at the moment, so sorry if the details aren't correct.

---

### Post by floatingpoint on 2009-01-08
That didn't seem to do anything. Thanks anyway, I'll cross that bridge when I come to it, the HDD is working fine at the moment.

Cheers everyone.

---

### Post by handydan918 on 2009-01-08
> **floatingpoint said:**
> Thanks for all the advice. I went to bed before you posted, -kg-, so I didn't back up my fstab, glad nothing went wrong! At least not as far as I can tell. 

Keen to use and get acquainted with the command line, so I just used terminal (is it gnome-terminal?). All seems to work fine. I'm still getting used to the way the file system is structured. I take it i could have done ```
mkdir whatever/iwanted/
```?
Aye, that's the idea. > 
So, it's all there when I start ubuntu, is that disk quite safe as it is now?
[quote]Yes, except for the fact that it's still using a microsoft file system...
Also, when you mentioned backing up fstab: 
cp = copy   and then the file to be copied followed by the destination to copy it to?[/quote]Again, you have grasped the sum and substance of it. for more mind boggling details, see ```
man cp
```> 

(I hope i'm not overdoing it on the questions :P )

If I did want to format it to a more reliable filesystem, what would I do?

Fire up gparted (sudo apt-get install gparted) and format the partition in question. THIS WILL IRRETRIEVABLY DESTOY ALL DATA ON THE PARTITION!!

:)

---

