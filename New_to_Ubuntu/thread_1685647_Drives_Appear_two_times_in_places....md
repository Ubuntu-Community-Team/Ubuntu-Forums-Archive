---
title: "Drives Appear two times in places..."
date: 2011-02-11
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-11
I have searched on Google and found some issue with that, and the solution was to add "[SIZE=2]/dev/disk/by-uuid[/SIZE]" in fstab.....So i done that, but the same Problem ...

Drive appear fine when i doesn't open Gparted, but when i open Gparted, then my drives appear two time in places....Those drives, which i had Auto-mounted i-e **NTFS**

My Fstab:-

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
/dev/disk/by-uuid/1ead48bc-592d-4d4e-9e28-aacf9e2fef51 /               ext4    errors=remount-ro 0       1
[B]#/dev/sda5 Data
/dev/disk/by-uuid/0E57D8995BE39FC3 /media/Data ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 0[/B]
[B]#dev/sda6
/dev/disk/by-uuid/4651B2B06FE30DAF /media/Multimedia ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 0[/B]
# swap was on /dev/sda7 during installation
/dev/disk/by-uuid/470fa908-b716-46f4-8564-f20fbae02fcf none            swap    sw              0       0

```I have Attached a** Screen-Shot** of my places menu, **DATA** &** MULTIMEDIA** which are NTFS, Appears two time....

---

### Post by Linyx on 2011-02-11
bump

---

### Post by robsoles on 2011-02-11
I haven't dug into the gnome mounter to surely nail this for you while you have those entries in your fstab file but I have a suggestion that I think easy enough.

I am going to suggest that you make a backup copy of your /etc/fstab file and remove these two drives from the original and just leave it to the gnome auto mounter to pick them up when you log into your GUI - the only reason this wouldn't be a tenable solution would be if you have users (including self) logging in via SSH (or similar) and requiring access to those drives and even then they could manually mount them at the command line regardless of absence in fstab.

Backup current fstab file```
sudo cp /etc/fstab /root/fstab.bak
```(/root is a perfectly reasonable place to keep such backups)

Edit fstab and kill NTFS entries```
sudo nano /etc/fstab
```(in nano just move cursor with arrow keys and delete entries relating to these two NTFS partitions/drives and then press [CTRL]+[X] (exit) [Y] (yes) [Enter] (writeout file to *name*))

Restart the system, log back into desktop and checkout places -> I am expecting you to have one each of the unnamed (in fstab) drives and be able to access them quite nicely, let me know how wrong I am if you have to ;)


Restore fstab```
sudo cp /root/fstab.bak /etc/fstab
```(Will/should ask for confirmation of overwrite destination)

Any good?

---

### Post by Linyx on 2011-02-12
Thanks for Reply, but i think i get quarter of your post...

Any way, I don't want to Mount them Manually Every-time... and I am the only user on my PC...

Therefore i have edited my fstab, but i have the only one issue  with this method, Which i have described in my 1st post.

---

### Post by jawilljr on 2011-02-12
[Linyx]("http://ubuntuforums.org/member.php?u=1205988"), I had the same problem as you.  What I did to fix the problem was changed the UUID number to the partition to "/dev/sdxx".

In other words change this line:

```
**/dev/disk/by-uuid/0E57D8995BE39FC3 /media/Data ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 0**

```to this:

```
**[B]/dev/sda5   **[/B]**[B]/dev/disk/by-uuid/0E57D8995BE39FC3 /media/Data ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 0**[/B]
```Do the same to "/dev/sda6"... then reboot.

It worked for me.

Jerry

---

### Post by Linyx on 2011-02-12
@Jawilljr:-

I have done exactly what you said, although i didn't reboot my PC yet, but now whenever i want to mount my NTFS partition via a Command "mount -a" it shows me an Error Message
> [mntent]: line 12 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad

Edit:- Can you post your fstab here...?How it works on your PC....

---

### Post by jawilljr on 2011-02-12
Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=cb2c194b-14bd-4327-9386-0ee88fca4355    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
#UUID=1CBCBF1FBCBEF27E    /media/WIN7    ntfs-3g    defaults,user,locale=en_US.UTF-8    0    0
/dev/sda1    /media/WIN7    ntfs-3g    defaults,user,locale=en_US.UTF-8    0    0
```All I did was change the UUID number to /dev/sda1... the rebooted.

Jerry

---

### Post by Linyx on 2011-02-12
Ohh...But actually you had Post the UUID and /dev/sdaXY **both** in your 1st post, I was Confused to see that.....

Anyway. It is better to use UUID instead on /dev/sdXY, because UUID will never change and your /dev/sdXY may change..

I have done that already when i Auto-mounted my NTFS for the 1st time, but then i change it to UUID.

Actually my Partitions looks fine ...but when i Open up Gparted, it then shows me my drives two times, before that OR if i don't use Gparted, its fine for me then....

---

### Post by jawilljr on 2011-02-12
> Ohh...But actually you had Post the UUID and /dev/sdaXY **both** in your 1st post, I was Confused to see that.....Oops... Sorry about that... Hadn't have my first cup of coffee yet... my bad.

> Anyway. It is better to use UUID instead on /dev/sdXY, because UUID will never change and your /dev/sdXY may change..I know, but that is the only way that I know of to fix the bug...

Jerry

---

### Post by robsoles on 2011-02-12
If you just dump them out of your /etc/fstab altogether (delete the  lines flatout) then they will appear once in places (for the same reason  they are/were appearing twice) and 'manually mounting' them is as  difficult as clicking them in places.

I am (was trying) having you keep a copy of your original so that if for  some reason your system doesn't reveal drives on sata and ide ports to  the infrastructure behind the gnome-mounter in the same way that usb  drives are picked up in system - by keeping the original you can revert  to it if trying to follow any advice makes the other drives inaccessible  altogether.


> **Linyx said:**
> Ohh...

Anyway. It is better to use UUID instead on /dev/sdXY, because UUID will never change and your /dev/sdXY may change..

...


 I've been screwed by UUID in operations similar to ghosting drives and so forth - if you don't fiddle with BIOS settings nor cabling inside the PC /dev/sd? shouldn't shift on you :)

Jerry's stuff would have been fine if the '/dev/disk/by-uuid/0E57D8995BE39FC3' part had been removed as well.

---

### Post by Linyx on 2011-02-12
Ok so i had removed that lines, Now they are not appearing two times in places....

But Now they are not Auto-Mounting, Actually what i want to explain is "[SIZE=2]They appear twice **only when i open Gparted**, if i don't open Gparted, then they will appear once"[/SIZE]

---

### Post by robsoles on 2011-02-12
Do you mean that on reboot they don't appear in places after you login until you fiddle with mounting them in terminal _**or**_ do you mean that you need stuff to access these drives before you login?


I can't get myself in your situation within steps I am willing to take and then recover from.

Your first post has a backup of your /etc/fstab file in it so I needn't have fussed about copying it on your hard drive as well.

Here is an edit of that which I would like to know what results you get by trying it:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
/dev/disk/by-uuid/1ead48bc-592d-4d4e-9e28-aacf9e2fef51 /               ext4    errors=remount-ro 0       1
**/dev/sda5 /media/Data ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 0**
**/dev/sda6 /media/Multimedia ntfs defaults,utf8,umask=007,uid=1000,gid=1000 0 0**
# swap was on /dev/sda7 during installation
/dev/disk/by-uuid/470fa908-b716-46f4-8564-f20fbae02fcf none            swap    sw              0       0
```To replace it's contents you can open it in gedit for greater convenience, just got to do it from command line is all```
gksudo gedit /etc/fstab
```Please reboot, please don't muck around with mounting commands in terminal before rebooting.

Does it still make the duplicate entries in 'places' **when you open gparted** after you reboot with that in your /etc/fstab file?

---

### Post by Linyx on 2011-02-12
Ok, So i have Edit my fstab by /dev/sdxy instead of UUID, Rebooted it, but same problem...... :(

---

### Post by robsoles on 2011-02-12
Sorry then. I can't make it happen to me and I can't find anyone else in Google saying this happened to them (your thread is only actual relevant result I found for [www.google.com/search?q=gparted+makes+some+drives+appear+twice+in+places](www.google.com/search?q=gparted+makes+some+drives+appear+twice+in+places)) and so I am stumped.

All my extra drives\partitions in /etc/fstab are ext4 and I've worked with the idea that I should be able to get gparted to exhibit this behaviour on those and it just doesn't - I haven't got a spare partition I can turn NTFS to try much closer to your circumstances.


Do the extra entries under places persist after you close gparted? If they disappear again when you close gparted then that could be some explanation as to why nobody else has mentioned it.

If they don't disappear after you close gparted then surely they don't persist through a reboot - must you run gparted every time you reboot?


You may as well revert your /etc/fstab file to your original.

---

### Post by Linyx on 2011-02-13
Thanks for Support,

Actually When i open Gparted, then my drives appear two times as i have shown in my 1st post, if i close Gparted, they still appear two times, i fix it every time by un-mounting my NTFS Partitions & Mount them again, and then they are fine....

This means that when Gparted Check my Drives, then it Appear two times, if i don't touch Gparted, then it is fine....

---

