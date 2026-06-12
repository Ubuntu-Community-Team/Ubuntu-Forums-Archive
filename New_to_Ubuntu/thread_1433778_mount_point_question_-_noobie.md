---
title: "mount point question - noobie"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by holadebob on 2010-03-19
When I installed Ubuntu, I put the root, system and swap files on three partitions of my 160G drive(sdb). I have a second 60G drive(sda) that I wanted to use as backup destination. When the partition phase of the installation came I got confused because there is no condition where I can partition the 60 G to a blank mount point. So I picked User/local, which was obviously a mistake since I can't write to it. 
How can I remove the User/local mount point from the 60G drive, return the User/local folder back to root, and then make the 60G drive a simple formatted ext3 open memory to use for whatever comes up. ?
If possible without reinstalling the system, I would kiss your toes. 
Thank you

---

### Post by doas777 on 2010-03-19
well, there may be an easier way, but the surest is to edit your fstab file, which stores information about the filesystems you mount at boot.

could you please post the output of this command:
```

sudo cat /etc/fstab

```

---

### Post by holadebob on 2010-03-19
Thanks for the quick response - interesting readout

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=31781129-9748-419f-93bd-5db3368832c7 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=a913e541-36b2-443a-adb8-51779c67f7f5 /home           ext3    relatime        0       2
# /usr/local was on /dev/sda5 during installation
UUID=7a8693a6-f4f0-4f03-aa0b-94c37d506e68 /usr/local      ext3    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=49690b4f-381c-485a-9698-095f89d2f1fd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
clark@office:~$ sudo cat /etc/fstab

---

### Post by sisco311 on 2010-03-19
Boot a Live CD/USB.  

Mount the partitions:
```
sudo mkdir /mnt/root
sudo mkdir /mnt/local
```
```
sudo mount /dev/disk/by-uuid/31781129-9748-419f-93bd-5db3368832c7 /mnt/root
sudo mount /dev/disk/by-uuid/7a8693a6-f4f0-4f03-aa0b-94c37d506e68 /mnt/local
```

Copy the data from the /usr/local partition to the root partition:
```
sudo cp -aR /mnt/local/* /mnt/root/usr/local
```

Edit the fstab file:
```
gksu gedit /mnt/root/tc/fstab
```

and comment out the /usr/local line:
```

# / was on /dev/sdb6 during installation
UUID=31781129-9748-419f-93bd-5db3368832c7 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=a913e541-36b2-443a-adb8-51779c67f7f5 /home           ext3    relatime        0       2
# /usr/local was on /dev/sda5 during installation
**#**UUID=7a8693a6-f4f0-4f03-aa0b-94c37d506e68 /usr/local      ext3    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=49690b4f-381c-485a-9698-095f89d2f1fd none            swap    sw              0       0

```

reboot.

---

### Post by coffeecat on 2010-03-19
> **sisco311 said:**
> Boot a Live CD/USB.  

Not necessary. You can edit /etc/fstab from an ordinary session, and then remount your partition, all from the ordinary session.

@holadebob.

Open a terminal.

1 - unmount sda5...

```
sudo umount /dev/sda5
```2 - Create a mountpoint...

```
sudo mkdir /media/sda5
```(Change the mountpoint name to whatever you want, and use /mnt if you don't want a desktop icon or an entry in Places.)

3 - Edit /etc/fstab...

```
gksudo gedit /etc/fstab
```Change this line....

```
UUID=7a8693a6-f4f0-4f03-aa0b-94c37d506e68    /usr/local         ext3    relatime        0       2
```.. to this...

```
UUID=7a8693a6-f4f0-4f03-aa0b-94c37d506e68    /media/sda5         ext3    relatime        0       2
```(Change /media/sda5 to /mnt/whatever or whatever you choose.)

4 - Remount sda5

```
sudo mount -a
```If you've chosen a mountpoint in /media, you'll get a desktop icon (which can be switched off) plus an entry in Places. If /mnt, you'll have to navigate through Places > Computer.

---

### Post by holadebob on 2010-03-19
Just to be on the safe side - from a nervous noob, 
when you say live CD/USB, do you mean one or the other? I have the live CD, but it's not a USB drive - it's an internal SATA disk drive. 
Also, when you say comment out the User/local line, do you mean the entire line....UUID=7a8693a6-f4f0-4f03-aa0b-94c37d506e68 /usr/local ?
Seems like you know the solution and you make me very happy :)

---

### Post by coffeecat on 2010-03-19
@holadebob, in case you didn't see it - we posted near-simultaneously - you don't need to use a live CD or boot from a USB device. See my earlier post.

---

### Post by holadebob on 2010-03-19
oops, excuse the cd/usb question, I wasn't reading your response.

---

### Post by coffeecat on 2010-03-19
> **holadebob said:**
> oops, excuse the cd/usb question, I wasn't reading your response.

No problem. :) Don't forget to save your edited fstab! One thing I forgot to make clear.

---

### Post by sisco311 on 2010-03-19
> **coffeecat said:**
> Not necessary. You can edit /etc/fstab from an ordinary session, and then remount your partition, all from the ordinary session.


Yep, but you have to copy the content of the partition to the root partition. So you must mount the root partition to another location, copy the content, log out from the GUI, stop gdm, unmount the /usr/local... ;)

---

### Post by holadebob on 2010-03-19
Everything worked fantastic. 
One question - the files that were on the drive as User/local are now on the drive media. Should I just copy the files over to the new directory User/local?

---

### Post by holadebob on 2010-03-19
Also, I tried to delete the media icon and says I don't have permission. I don't mind living with it, just would be nice if I could.

---

### Post by coffeecat on 2010-03-19
> **sisco311 said:**
> Yep, but you have to copy the content of the partition to the root partition. So you must mount the root partition to another location, copy the content, log out from the GUI, stop gdm, unmount the /usr/local... ;)

You may very well be right. I was taking the OP literally, that they had made a mountpoint called /User/local. If they've used /usr/local then that does - ahem - complicate things. Oops!

How very astute of you.

**Edit:** it looks as though the OP has followed my directions and got sda5 mounted on /media/somewhere. Which means that the contents of /usr/local will be drifting about in /medai somewhere if the Ubuntu installer put them on sda5. So it does look like a live CD session to copy them over. I'll leave it to you. :|

---

### Post by holadebob on 2010-03-19
For lack of a better idea, I used /media/sda5

Throw it at me, I can handle it. :)

---

### Post by coffeecat on 2010-03-19
@holadebob, I apologise. I missed an important point that sisco311 noticed. If you mean that you originally chose to mount sda5 to /usr/local (that's different from User/local) then it's possible that the intended contents of /usr/local are in sda5. Which means that your system is unstable at the moment.

Have a look in /media/sda5. Are there a number of folders starting /bin, /etc, /games, /include.... ? Now have a look in /usr/local. Is it empty?  If so, then you need to:

```
sudo cp -a /media/sda5/* /usr/local/
```... to get all the contents of /usr/local back to - um - /usr/local. :-s

(The -a flag for copy preserves permissions and does a recursive copy.)

Before doing this, wait for sisco311 to comment. My brain must be firing on three cylinders atm, so it would be good for someone to double-check. :(

---

### Post by holadebob on 2010-03-19
No problem, I am very grateful for the chance to get help. 
Yes all the user/local files are on the drive sda5 and the use/local folder in root is empty, and I'm waiting for sisco311's reply.

---

### Post by coffeecat on 2010-03-19
> **holadebob said:**
> No problem, I am very grateful for the chance to get help. 
Yes all the user/local files are on the drive sda5 and the use/local folder in root is empty, and I'm waiting for sisco311's reply.

I'm 99% sure that my 'cp' line will do the trick. You've successfully mounted sda5 to /media/sda5. All the files that should be in /usr/local are in sda5 and /usr/local is empty. I'd go for it. The only oddity is that an empty folder called 'lost+found' will be copied to /usr/local.

By the way, when referring to directories and mountpoints, it's safer to follow Unix conventions and also to be accurate. All paths start with a '/' which represents the root of the filesystem. And remember that Linux/Unix is case-sensitive. So it's /usr/local not /user/local or User/local. :wink:

---

### Post by holadebob on 2010-03-19
Good advice, I can now see why the confusion. There is a drop down table in the partitioner that provides a choice of mount points and I chose that one cause it seems most logical. The /user/local files are now in the /user/local folder in root. 
Can I somehow delete those /user/local files that are in the /media/sda5 drive? Possible to delete the desktop icon? Don't know what kind of permission I need or where to get it.
Thanks for all your help coffeecat. 
I built my first computer, an 8080 based board with 16kb memory and used a handmade tape reader to input assembly in 1980. I've been from Sinclair Timex 8085 or 6 to this great system with a wonderful system program. I love the Ubuntu style and the cleanness of it. I'm almost 70 (some memory read problems) but enjoying it more.
Thank you

---

### Post by holadebob on 2010-03-19
Rats - can't copy anything to /media/sda5 without permissions. Can't make a folder there or delete anything.

---

### Post by doas777 on 2010-03-19
> **holadebob said:**
> Rats - can't copy anything to /media/sda5 without permissions. Can't make a folder there or delete anything.

just to clarify, i though you were moving stuff OFF sda5, right?

also, it's "/usr/local". very important.
/usr is a location for apps and configurations that are available to all users, so it is a system folder, and has nothing to do with your actuall user profile (your user profile is in /home).
no you don;t want to delete the old files until you have copied them to the root partitions /usr/local. if you did, then your system would not work correctly (prolly won;t even boot all the way).

use sudo or gksu to run it as root. if you are in command line
```

sudo mkdir <pathtodir>

```or if you are doing it with the windowed file manager, hit alt+F2 and enter 
```
gksu nautilus
```to launch a file manager window with admin (root) privileges.

---

### Post by coffeecat on 2010-03-19
I'm just about to have a much-needed supper. All your questions are easily solved. I'll post back in about an hour or two to tell you how to:

- remove the desktop icon

- get permanent permissions to write to /media/sda5

- how to delete all the redundant stuff in /media/sda5 which is owned by root.

Plus anything else that you might ask in the meantime. :p

Unless sisco gets in before me!

Better that way - a few calories inside and I'm less likely to make mistakes.

---

### Post by holadebob on 2010-03-19
that allowed me to delete the files in the drive. 
The problem is I can't transfer files into the drive or use the drive as a backup directory without going into root. I've got GParted, can I use that to change sda5 to accessible directory? If so, which mount point do I use?
Hope you're patience holds out....
Bob

---

### Post by holadebob on 2010-03-19
Thanks Coffeecat - I'll go out and pull weeds for a bit.

---

### Post by srs5694 on 2010-03-19
A couple of comments:

First, /usr/local is generally unused on a default installation. It's got directories defined, but they're all normally empty, save for subdirectories. The purpose of /usr/local is to hold programs and associated data that are locally compiled, as opposed to programs that you install via your package manager. Thus, completely wiping /usr/local (which is what the OP effectively did by following the advice he was given) won't make Ubuntu unstable; it'll just put a road block in place should he ever decide to compile software locally.

Second, permissions to any directory on a Linux-native filesystem can be controlled via the chown and chmod commands, but chances are these commands must be run as root (that is, via sudo), thus:

```

chown someuser:users /some/directory
chmod 755 /some/directory

```

The chown command takes a username (and optionally a group name after a colon or dot) and a file or directory name as options, as shown. Unfortunately, the permissions strings used by chmod are somewhat obscure. A quick Google turned up [this tutorial,](http://catcode.com/teachmod/) and [another one.](http://www.perlfect.com/articles/chmod.shtml) These should serve better than anything I could write in the short time I could devote to this post.

---

### Post by coffeecat on 2010-03-19
OK. Had my supper. :)

**Desktop icons:** Alt-F2 > type 'gonf-editor' in the field (no quotes) and click run. Now apps > nautilus > desktop and untick 'volumes_visible'. Unfortunately, that will mean that no mounted volumes will appear on the desktop - not even automounted USB drives. Although mounted USB drives will appear in Places, you have to go to Places > Computer to unmount them, which is not as convenient as right-clicking on the desktop icon.

The alternative is to make a mountpoint in /mnt, and edit fstab accordingly.

**Getting permissions to write to sda5:** 'gksudo nautilus' is a good way of accessing a root-owned folder, but anything you write there with a root nautilus will be owned by root, which doesn't get you very far.

To complement what srs5694 posted, in a terminal:

```
sudo chown yourusername: /media/sda5
```Substitute your login name for 'yourusername' and don't forget the trailing colon - that sets the correct group permission. Also substitute whatever mountpoint you decide on for /media/sda5 - that is if you change it. Now everything freshly created by your ordinary account in /media/sda5 will be owned by you because /media/sda5 is owned by you.

**Deleting redundant root-owned stuff:** it looks as though you've managed this but, for the record, using 'gksudo nautilus' is a good way.

---

### Post by holadebob on 2010-03-19
Coffeecat,
I used the chown command and it worked after I restarted system.
Everything seems to be working fine now, I've decided to leave the media icon on the desktop, could be handier there.

You sure save me a lot of hassle restoring all these files and updates, etc., at the expense of taking lots of your time and I really thank you for that. If there's anything I do for you from here in Panama, say the word. 
 
I will now fade into the swarm of happy Ubuntu users with a new profound respect for the group effort you folks are.
Bob

---

### Post by coffeecat on 2010-03-19
> **holadebob said:**
> I will now fade into the swarm of happy Ubuntu users

Happy Ubuntu-ing!

---

