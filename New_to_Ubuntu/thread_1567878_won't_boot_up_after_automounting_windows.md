---
title: "won't boot up after automounting windows"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by adobrakic on 2010-09-04
Hello, I have Ubuntu 10.04, and Windows 7 on two different partitions. I wanted to make the 7 partition automount on every boot, and have done so without problem in the past. I used ntfs-config or whatever that program is called to do this. When I boot up, it says:

/dev/sda5: clean, 142681/25796608 files, 3062529/103171430 blocks
init: ureadahead-other main process (931) terminated with status 4 
init: ureadahead-other main process (961) terminated with status 4

Also, if I hit S, it says:

/media/OS skipped by user (or something to that extent)

but it still just stays at that screen

---

### Post by Mark Phelps on 2010-09-05
I've tried to advise folks again and again to NOT mount MS Windows OS partitions read/write automatically -- but no one listens.

Looks like you have Win7 partition corruption -- which you're most likely NOT going to be able to repair from Ubuntu.  The ntfsfix app repairs SOME NTFS problems, but it's NOT a substitute for MS Windows CHKDSK (despite what some folks may tell you).

About all you can do right now is boot into MS Windows from a CD/DVD and try to run CHDSK -- and once you get it working, REMOVE the MS Windows automount from your fstab file (if that's how you're mounting it), or change the automount to read-only.

---

### Post by coffeecat on 2010-09-05
+1

I'm very wary about mounting a Windows C: partition. If you need to read or copy some files from your C: partition, use the Places menu to mount as and when you need it. Copy the files and then unmount as soon as you can. Avoid - like the plague - writing to a Windows C: partition. XP usually tolerates this. You can severely upset Vista and W7.

If you are trying to access your personal files in Windows C:, you would be far better off creating a separate data partition, formatted ntfs, for all your personal data. Windows 7 will see this as E: or F: or whatever, and you can automount that instead with ntfs-config. (Personally I don't like ntfs-config - I prefer to edit /etc/fstab manually.)

Using a separate ntfs partition doesn't risk corrupting your C: partition. Vista and W7 are quite happy with an 'E:' ntfs drive written to by Linux - I've done it myself with both. And if you get filesystem problems with your data partition, you have Windows chkdsk available to repair it. As Mark Phelps pointed out, ntfsfix is not comprehensive.

---

### Post by adobrakic on 2010-09-05
> Looks like you have Win7 partition corruption -- which you're most likely NOT going to be able to repair from Ubuntu. The ntfsfix app repairs SOME NTFS problems, but it's NOT a substitute for MS Windows CHKDSK (despite what some folks may tell you).

About all you can do right now is boot into MS Windows from a CD/DVD and try to run CHDSK -- and once you get it working

Why from a CD? I can boot into Windows 7 just fine. I ran chkdsk and I also ran chkdsk /f, I still pretty much get the same error when booting linux up, with a few exceptions:

```

fsck from util-linux-ng 2.17.2
udevd[449]: can not read '/etc/udev/rules.d/z80_user.rules'

/dev/sda5: clean, 142681/25796608 files, 3062529/103171430 blocks
init: ureadahead-other main process (952) terminated with status 4
init: ureadahead-other main process (957) terminated with status 4

```

> REMOVE the MS Windows automount from your fstab file (if that's how you're mounting it), or change the automount to read-only.

I used the program 'ntfs-config' to make the partition automount on each boot. I don't understand why my entire Linux partition won't boot up just because it can't mount my Windows partition. I know Windows fails miserably at viewing Linux files out of the box, but is there a way for me to stop it from automounting from within Windows?

@coffeecat yeah, I'm definitely going to just make another partition for storage. I didn't know it could get this out of hand.

---

### Post by coffeecat on 2010-09-05
> **adobrakic said:**
> I can boot into Windows 7 just fine. I ran chkdsk and I also ran chkdsk /f, I still pretty much get the same error when booting linux up, with a few exceptions:

For some reason I read your post to say that you were unable to boot into Windows. I think Mark Phelps read the same.

Anyway... I googled your first error (with the 931) and came up with this:

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

... with this intriguing comment in post #5

> 
                 This is a normal exit code to indicate that there is no pack file for a separate filesystem you have in your fstab.
 The bug is that Upstart displays them (and is already filed elsewhere)
I have no idea what a pack file is (but I will google it later this evening), but if you were getting this on the first boot after running ntfsconfig to mount your Windows partition, then it sounds as though ntfsconfig has messed up its entry to /etc/fstab. I haven't googled the other error numbers. They might show up something else, but I would think the first priority is to mend your broken /etc/fstab.

Boot up from the live CD, mount your Ubuntu root partition, and browse to /etc/fstab in the filesystem of your hard drive Ubuntu - **not** the /etc/fstab in the live session. Post the contents and I'll tell you how and what to edit. If you are confident editing system files from a live session, you simply need to identify the ntfs line mounting your Windows partition and put a hash (as we say in the UK :wink:) = # sign as the beginning of the line.

---

### Post by adobrakic on 2010-09-05
Yup, here you go:

[http://www.divshare.com/download/12470215-b8c](http://www.divshare.com/download/12470215-b8c)

I would've posted the contents, but the live-cd wasn't connecting to the internet for whatever reason, so i had to transfer the file over to my Windows. In notepad, the text wasn't organized, so I just decided to upload it.

---

### Post by coffeecat on 2010-09-05
> **adobrakic said:**
> In notepad, the text wasn't organized, so I just decided to upload it.

Yes, that's a well known problem. The conventions for text files are different in Unix systems and Windows. Wordpad in Windows might have made a better go of it. Not to worry, because your uploaded file opens just fine in Gedit and here it is for anyone else wanting to comment:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=7fa4e1e8-72f2-43a9-b4d8-5e10fd6e52e4    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sda3 :
UUID=9E0C5A9E0C5A716F    /media/HP_RECOVERY    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda2 :
UUID=0A5E96C25E96A64B    /media/OS    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=BA1216E71216A881    /media/SYSTEM    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=22b1888b-805c-4d39-bd15-9cbc8b8be6f1    none    swap    sw    0    0
#Entry for /dev/sdf :
UUID=8668-9DE7    /media/OS    vfat    defaults    0    0
```First thing to say is that ntfsconfig has made a complete cockup of things. It's put in mount entries for your recovery partition and the Windows 7 boot partition in addition to the C: partition. Good grief! I should think it was one of the first two that was causing the problem.

OK you need to edit that file so that it looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=7fa4e1e8-72f2-43a9-b4d8-5e10fd6e52e4    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sda3 :
#UUID=9E0C5A9E0C5A716F    /media/HP_RECOVERY    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda2 :
#UUID=0A5E96C25E96A64B    /media/OS    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
#UUID=BA1216E71216A881    /media/SYSTEM    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=22b1888b-805c-4d39-bd15-9cbc8b8be6f1    none    swap    sw    0    0
#Entry for /dev/sdf :
UUID=8668-9DE7    /media/OS    vfat    defaults    0    0
```Or, even better, delete the lines referring to sda1, sda2 and sda3 (That includes the UUID lines I commented with a #.). Obliterate them. Cast them into outer darkness! :wink:

To do this, you need to boot up the live CD again and mount your Ubuntu partition from the places menu. Let the file browser open showing the root of your Ubuntu system (or browse there) and then press ctrl-L. The breadcrumb path trail will change to a text path - something like /media/something. Make a note of that. Now open a terminal, and:

```
gksudo gedit /media/something/etc/fstab
```Obviously, substitute whatever the mountpoint was for 'something'. Make your edits (carefully - double-check everything), save the file, exit gedit and the terminal and then reboot into your permanent Ubuntu.

---

### Post by Morbius1 on 2010-09-05
> First thing to say is that ntfsconfig has made a complete cockup of thingsA more enlightened observation I have never read especially since ntfs-config is so aggressive it even adds mountpoints used by something else:
> UUID=8668-9DE7 [COLOR=Blue]   /media/OS[/COLOR]    vfat    defaults    0    0
UUID=0A5E96C25E96A64B [COLOR=Blue]   /media/OS[/COLOR]    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0

---

### Post by coffeecat on 2010-09-05
> **Morbius1 said:**
> A more enlightened observation I have never read especially since ntfs-config is so aggressive it even adds mountpoints used by something else:

Good Lord, I missed that. I was so dumbfounded by ntfs-config mounting a recovery partition, I didn't expect it to get worse! :-s

---

### Post by adobrakic on 2010-09-05
Yeah, when I was looking at the fstab file, I was like WTF is this? 

sda 1 is where my Windows 7 is located, sda 3 is for Windows recovery. sda 5 is where linux is located. 

But yeah, I'll go in and delete the sda 1, 2, and 3 lines. I'll report back here. Thanks for all the help

--edit--

Alright, here's what I have for fstab currently:
[http://www.divshare.com/download/12470941-c56](http://www.divshare.com/download/12470941-c56)

However, after I tried rebooting into Ubuntu, it again said that /media/os cannot be mounted and just sits there. I'm positive I edited the correct fstab file, because I mounted my Ubuntu partition, went into /etc/, right-clicked, went to "open in terminal" and typed "gksudo gedit fstab." 

Is there possibly another file that has boot options? If not, I'll just go ahead and format my hard drive and reinstall everything. PITA, but it'll be better than not being able to use Linux at all.

---

### Post by Morbius1 on 2010-09-05
BTW, you are not going to win many friends around here if you insist on using [www.divshare.com](www.divshare.com). If you want someone to see your fstab then I suggest you do the following:

In a terminal:
```
cat /etc/fstab
```
Edit > Select All > Edit > Copy

Then post the output on your next posting.

---

### Post by adobrakic on 2010-09-05
> **Morbius1 said:**
> BTW, you are not going to win many friends around here if you insist on using [www.divshare.com](www.divshare.com).


You won't gain any friends here if you insist on reading the last few posts of the thread and not the entire thing. I already stated why I'm forced to use divshare.

---

### Post by coffeecat on 2010-09-06
> **adobrakic said:**
> However, after I tried rebooting into Ubuntu, it again said that /media/os cannot be mounted and just sits there.

/media/os is the mountpoint for a fat32 drive designated sdf. Possibly a flash drive, but do you know what that is? If you look back a few posts you'll see that someone picked up that your original fstab was trying to mount one of your Windows partitions as well as sdf1 to /media/os. No wonder the system was getting in a twist. But there's clearly something amiss with sdf as well.

Yes, you did edit the correct fstab. Try editing it again, and this time comment out or delete the last line - the one referring to sdf and vfat.

By the way, Morbius1 does have a point. Divshare is excessively irritating - I don't want to join up which means I have to watch the countdown counter before I can download the file. Morbius1's cat method is a good way but in your situation it does mean booting up with the live CD and the cat command would have to include the complete path to your fstab. If you are limited to Windows for uploading the file, try Wordpad or a proper Wordprocessor like OpenOffice or even - gasp - Microsoft Word. The fstab file *should* appear properly in that. Or even simpler, use the attach files utility in the reply page of this forum. You can upload text files to your post and they appear as a downloadable icon.

---

### Post by adobrakic on 2010-09-06
> **coffeecat said:**
> /media/os is the mountpoint for a fat32 drive designated sdf. Possibly a flash drive, but do you know what that is? If you look back a few posts you'll see that someone picked up that your original fstab was trying to mount one of your Windows partitions as well as sdf1 to /media/os. No wonder the system was getting in a twist. But there's clearly something amiss with sdf as well.


Oh wow, I didn't even make that connection when the user posted about it earlier. I deleted that line and everything is working fine again. Now to make a partition just for storage so I can hopefully avoid this mess in the future.

Thanks for the help everyone! ):P

---

### Post by coffeecat on 2010-09-06
> **adobrakic said:**
> Now to make a partition just for storage so I can hopefully avoid this mess in the future.

Now that you've had experience editing fstab, you'd be better adding your own line once you've made the partition. Here's a useful link:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Just a couple of comments about what they say about ntfs in the link. Two quotes:

> ntfs/vfat = permissions are set at the time of mounting the partition  with umask, dmask, and fmask and can not be changed with commands such  as chown or chmod. I advise dmask=027,fmask=137 (if you user umask=000 all your files will be executable). More permissive options would be dmask=000,fmask=111. and

> 
# NTFS ~ Use ntfs-3g for write access (rw) 
# /dev/hda1
UUID=12102C02102CEB83  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0All very wise, but I've found that you don't need all those options for NTFS. A simple:

```
device     mountpoint    ntfs    defaults    0 0
```.... works very well on a single user machine. In fact some options can cause date/time stamp changes if you copy a file from a Linux ext partition to the ntfs partition. This doesn't happen if you use a simple 'defaults'. Also, it doesn't matter whether you use 'ntfs' or 'ntfs-3g' in the third field. You get the ntfs-3g driver either way.

Obviously, substitute your device and mountpoint for 'device' and 'mountpoint'. You can use the form '/dev/sdax' instead of a UUID for device and don't forget to create a folder in /media for the mountpoint first. Once you've finished your edit of fstab you don't have to reboot to test it. Simply do 'sudo mount -a' from the terminal.

I'm glad the problem is sorted and good luck!

---

### Post by Trophy on 2010-09-10
Thanks guys .. I made the same mistake of saying yes to the automount thing ... after reading this post ...  i felt a bit better knowing i was not in for a re-install ... and i wasn't the only one that did it. I found a backup file of my fstab file ... so instead of editing the fstab .. i made a backup of it (just in case) ... and then replaced it with the backup i found .... all working again ... thanks for your help guys ... and adobrakic ... thanks for making the mistake before i did :p

---

