---
title: "Cannot unmount/eject or save to USB Drive."
date: 2010-06-23
forum: New to Ubuntu
---

### Post by kirbyparufo on 2010-06-23
I recently installed Ubuntu 10.04 (Desktop) and am enjoying it immensely. However, I couldn't get USB drives to appear, and Ubuntu seemed to ignore them. After installing "automatically mount and unmount USB Mass Storage Devices," my USB drives appear, but I cannot save to them, unmount them, or eject them. The ejection option does not even appear for the drive, unmounting it leads to the error: "umount: /media/usb0 is not in the fstab (and you are not root)." When moving/creating files to/in the USB Drive, I get the following error: "Error opening file 'INSERT FILE HERE': Permission denied." Am I missing any downloads, or is my system just messed up?

---

### Post by garvinrick4 on 2010-06-24
Change the permissions on your usb drive to you.

My login is rick and my label on a usb drive is hp. ( use your own login name and label)

```
sudo chown -R rick:rick /media/hp
```Now rick (me has permissions on that usb or media.

After you make a label in disk utility or gparted on your usb drive when it is unmounted. You can run this to make a directory for it. (one time only thing)

```
sudo mkdir /media/hp
```Now it will always mount at /media/hp

About mounting on insert try going to configuration editor go to apps go to nautilus to preferences and see if auto_mount is checked.

Anywhich way you will now have full read and write permissions on that drive.

---

### Post by kirbyparufo on 2010-06-24
Thanks for the reply. Upon entering the first code, I get the following error message: "changing ownership of `/media/usb0 **(This is the USB Drive in question)** ': operation not permitted." Is this normal? I'm sorry, this is all very new to me.

---

### Post by garvinrick4 on 2010-06-24
what did you label your USB flash drive? You are saying it has a label of usb0. Go to gparted or disk utility and label the usb flash drive. Pick any name you want.
Then do this code.

```
sudo mkdir /media/(label you choose)

```
Redo the previous command with new label

---

### Post by garvinrick4 on 2010-06-24
After you give your flash drive a new label. run this and you will see the label.

```
sudo blkid
``` (small L second letter)

And it will also show up in gparted or disk utility.

That is the label you use for /media/new label -- not usb0

---

### Post by kirbyparufo on 2010-06-24
After doing this, if I mount the USB drive via Disk Utility, everything works fine. However, upon plugging the device into the USB drive, USB0 still shows up (it mounts to usb0 by default). I have to go to Disk Utility to unmount it, and than mount it from there. As for checking the configuration editor (from one of your earlier posts), I went to the specified entry and didn't see an auto-mount option at all. I saw options for media_automount (checked) and media_automount_open (checked).

---

### Post by garvinrick4 on 2010-06-24
> **kirbyparufo said:**
> After doing this, if I mount the USB drive via Disk Utility, everything works fine. However, upon plugging the device into the USB drive, USB0 still shows up (it mounts to usb0 by default). I have to go to Disk Utility to unmount it, and than mount it from there. As for checking the configuration editor (from one of your earlier posts), I went to the specified entry and didn't see an auto-mount option at all. I saw options for media_automount (checked) and media_automount_open (checked).
media_automount is it, all USB drives are called media.  As the usb0 thing while you are in Disk Utility there will be a place called Edit Filesystem Label you can change your label there to whatever you want. They are easier to mount in terminal and you will want to do that one day and you need a label to change permissions easier if needed. I label every partition. Like one lucid one maverick one karmic one redhat. As shown. 

rick@rick-laptop:~$ sudo blkid
[sudo] password for rick: 
/dev/sda1: LABEL="SYSTEM" UUID="C6EECCF3EECCDCB5" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="66B0BDBFB0BD95D1" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda5: LABEL="maverick" UUID="3b18e5ca-681d-40e2-921d-60133e72ec59" TYPE="ext4" 
/dev/sda6: LABEL="lucid" UUID="c4c94121-65f4-40a3-8ce3-80c720438f6b" TYPE="ext4" 
/dev/sda7: LABEL="home" UUID="1adc1fb7-dd51-48e9-8fea-77d6c6a75e78" TYPE="ext4" 
/dev/sda8: LABEL="DATA" UUID="E036-58D5" TYPE="vfat" 
/dev/sda9: LABEL="redhat" UUID="1543b6c8-a524-40c2-8906-12144d4386d5" TYPE="ext4" 
/dev/sdb1: LABEL="adataboot" UUID="45f7f3b1-dbf7-4e94-9610-424ec91c0fd8" TYPE="ext2" 
/dev/sdb5: LABEL="HOUSE" UUID="75E2-4B97" TYPE="vfat" 
/dev/sdb6: LABEL="meerkat" UUID="a82ca713-3c8b-4007-a400-e91e90f197a9" TYPE="ext4"

---

### Post by anewguy on 2010-06-24
Love your signature - also remember that after a few drinks, wherever you go there you are.


Dave ;)

---

### Post by garvinrick4 on 2010-06-24
> **anewguy said:**
> Love your signature - also remember that after a few drinks, wherever you go there you are.


Dave ;)
Have been there and every time after a few drinks I seemed to have woke up in spots.
(Tahoe, Reno, Vegas, Atlantic City) Had to put the cork back in the jug the spots were killing me. Do not even remember if I had fun, pity wasted a lot of good booze.

---

### Post by anewguy on 2010-06-25
Took me close to 2 decades to cork the bottle.  I woke up at strange places as well and also always wondered how I ever got home.  Close to 2 decades that are just hard to remember much besides work.  The decade before that was just "hazy" ;)

Back to the OP's question - have you had any luck yet?  If not, I have something you could try - it might fix the problem but I really don't think it's the correct way to do it:

- open a terminal window (Applications/Accessories/Terminal)

- type:


sudo addgroup usbusers <press enter>

sudo adduser <your username here> usbusers <press enter>

sudo adduser root usbusers <press enter>

sudo gedit /lib/udev/rules.d/100-local-permissions.rules <press enter>

This should call up the editor and the file shown should be empty.

Add the following to the file shown:

# USB access limited to users in usbusers group

SUBSYSTEMS=="usb" MODE:="0666" GROUP:="usbusers"

Save the file, exit the editor and close the terminal window.


What this did was allow access to USB devices by all members of the usbusers group.  I suspect that right now your devices are getting mounted as owned by root.

If this works, perhaps it will help point someone in a direction to help you in a more correct way.

Dave ;)

---

### Post by kirbyparufo on 2010-06-25
I do believe the devices are getting mounted as root (under the permissions tab, I believe the devices were saying they belonged to root). For the time being, I've uninstalled "automatically mount and unmount USB Mass Storage Devices" via the software center (I still have to manually mount the USB drive through Disk Utility). I tried anewguy's method, but the USB still came up as USB0 with permissions to root when inserted.

---

### Post by anewguy on 2010-06-25
It would probably still say root owns it, but the permissions for group and world *should* allow you to write to it, etc., now I would think.

Dave ;)

---

### Post by kirbyparufo on 2010-06-25
I can read the USB drive (I'm not sure if I had this ability before, but now that I have files on it, I can verify this). However, I still cannot write to it. Depending on the programs I use, I get errors about not having permission or the USB not existing.

---

### Post by garvinrick4 on 2010-06-26
Here is a install that would not give me permissions to copy
items back and forth so I changed their permissions to rick (me).
They all said root root before changing.
```
sudo chown -R rick:rick /media/lucid
```  (to all my different media)
Redhat seems to not give you hardly any permissions by default so
you have to change them. Is possible to do it as root in nautilus also.

rick@rick-laptop:~$ sudo mount /dev/sda9 /media/redhat
[sudo] password for rick: 
rick@rick-laptop:~$ sudo chroot /media/redhat
[root@rick-laptop /]# cd /media
[root@rick-laptop media]# ls -la
total 24
drwxr-xr-x.  6 root root 4096 Jun 26  2010 .
dr-xr-xr-x. 24 root root 4096 Jun 26  2010 ..
drwxr-xr-x   2 rick rick 4096 Jun 25 18:44 lucid
drwxr-xr-x   2 rick rick 4096 Jun 25 18:45 maverick
drwxr-xr-x   2 rick rick 4096 Jun 25 18:45 meerkat
drwxr-xr-x   2 rick rick 4096 Jun 25 18:45 OS
[root@rick-laptop media]#

---

### Post by anewguy on 2010-06-28
Not sure if it would apply to your problem or not, but I found a kernel bug report while researching a problem I'm having with an external USB drive not be recognized by the system - the bug report mentions USB flash drives as well.  The link follows, but since this is a beginners forum, I want to caution new users from assuming this is their problem and trying this as well.  It involves installing a new kernel and knowing how to boot it.  It did indeed solve my problem (I think it's a problem with hot-plug USB devices), but the updated kernel also made me loose my wireless support, so I am just using the old kernel for now until I can figure it out.

The link to the bug report with it's long set of replies and recommendations is at:

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds")

 Dave ;)

---

### Post by kirbyparufo on 2010-06-28
If I go into Disk Utility, as soon as my USB is plugged into the system, it is recognized (name and model too), but it is mounted under the wrong name (USB 0) and as root. Therefor, I'm not sure if that fix is right for me. I think for now that I'll manually mount/unmount it through Disk Utility.

---

### Post by kirbyparufo on 2010-06-29
After the recent set of updates via update manager, the problem appears to have resolved itself. The machine now automounts correctly.

---

### Post by Erwacht on 2010-07-02
garvinrick4,

I had the same problem as kirbyparufo, and I successfully applied your solution to gain writing privileges to a USB thumb drive. However, it turned out to be a Pyhrric victory: My Windows desktop says the thing is unformatted now and won't read it! Obviously, Ubuntu can read it [Xubuntu 10.04 in this case, being a second, separate installation from my usual Ubuntu desktop], but the point was to use the drive on /any/ system.

How can I undo your process? I used GParted to give the thumb drive a label, by the way, in the process.

(And how is it that GParted, which works such magic as resizing Windows NTFS boot partitions -- talk about parting the waters! --, can't label a FAT thumb drive and leave it Windows-readable?! ... You don't have to answer that...)

==================================================================
Update:

Inserting the thumb drive again, Windows recognizes it this time! Thankfully! However, this thread was very useful to me (and I want to thank you, garvinrick4, for it), and I think my experience will make it marginally more useful for the next person who comes along with the original problem. So I'll post this anyway.

(And my apologies to the magnificent GParted for my impugning remarks!)

Erwacht

---

### Post by Zimmer on 2010-08-19
Quick tip: try out  'Disk Mounter' .  Right Click on the Gnome panel and 'Add to Panel' then select it from the list of Apps. A handy, simple application..

---

