---
title: "cannot change file permissions on usb"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by brokenhachi on 2011-05-28
Hi guys, 

i'm trying to install katana sec suite on my usb thumb drive, and i cant seem to get it to run the install script. here is the output

```
grass boot # ./bootinst.sh
bash: ./bootinst.sh: Permission denied

```

so i check the permissions

```
grass boot # ls -l bootinst.sh
-rw-r--r-- 1 me me 2410 May 27 20:23 bootinst.sh

```

ok, so it's not executable... we can change that:)

```
grass boot # chmod -v +x bootinst.sh
mode of `bootinst.sh' changed to 0755 (rwxr-xr-x)

```

```
grass boot # ./bootinst.sh
bash: ./bootinst.sh: Permission denied
grass boot # ls -l bootinst.sh
-rw-r--r-- 1 me me 2410 May 27 20:23 bootinst.sh

```

:confused::confused:

```

grass boot # chmod -v u+x bootinst.sh
mode of `bootinst.sh' changed to 0744 (rwxr--r--)
grass boot # ./bootinst.sh
bash: ./bootinst.sh: Permission denied
grass boot # ls -l bootinst.sh
-rw-r--r-- 1 me me 2410 May 27 20:23 bootinst.sh

```

:confused::confused:

so what if i try 777...?

```
grass boot # chmod -v 777 bootinst.sh
mode of `bootinst.sh' changed to 0777 (rwxrwxrwx)
grass boot # ls -l bootinst.sh
-rw-r--r-- 1 me me 2410 May 27 20:23 bootinst.sh
```

what about changing ownership?

```
grass boot # chown -v root bootinst.sh
chown: changing ownership of `bootinst.sh': Operation not permitted
failed to change ownership of `bootinst.sh' to root

```

i'm logged in as root but, why am i not able to change the permissions?

the thumb drive is formatted in fat32, and i know there are issues with changing permissions under FAT but it should be changeable as root, correct?

help!!

---

### Post by TeoBigusGeekus on 2011-05-29
Fat32 and Ntfs have no way of understanding what a permission is.
Try with a linux filesystem.

---

### Post by Anders H on 2011-06-02
I'm having the same issue. 

Ok so FAT32 does not understand file permissions, check, but if you read  the katana documentation it looks like that katana has to be installed  on a FAT32 USB stick. 

[http://www.hackfromacave.com/katana.html#katana_installation](http://www.hackfromacave.com/katana.html#katana_installation)

I have yet to test them out but I have two ideas on how to fix this problem 

one - copy files to linux hard drive, run script, move files out to FAT32 USB

or (possibly better)

two - change the formatting of USB stick to ext4 (or whatever) run  "bootinst.sh" and see if it will work. 

However the Katana tool kit does  run under a windows environment and I wonder if ext4 will screw it up, Backtrack 4 and the other Linux software should be fine, but I'm worried about loosing the tools of the Katana tool kit.

---

### Post by Anders H on 2011-06-02
maybe this will help

[http://ubuntuforums.org/showthread.php?t=1698919&highlight=katana](http://ubuntuforums.org/showthread.php?t=1698919&highlight=katana)

---

### Post by catsandogs on 2011-12-25
I solved this problem by booting from CD into Puppy Linux 5.28 ("Lucid Puppy"), which let me run ./bootinst.sh on my USB drive with no problem.

Discussion: According to Pureh@te, an OS is worthless if it doesn't allow you to run scripts as root on a USB drive. I've run this very script on older versions of Ubuntu in the past. Now, on 10.10, it is impossible, and I'm wondering whether this change is some sort of regression, part of the dumbing-down of Ubuntu, or some sort of attempt to defend the interests of big business in some way that I can't fathom, or all of the above. Anyone?

---

### Post by Morbius1 on 2011-12-25
> According to Pureh@te, an OS is worthless if it doesn't allow you to run scripts as root on a USB drive.Well, If Pureh@te says it it must be so. 
> and I'm wondering whether this change is some sort of regression, part  of the dumbing-down of Ubuntu, or some sort of attempt to defend the  interests of big business in some way that I can't fathom, or all of the  above.I believe it's option (c) - part of a vast big business conspiracy. I suppose you could reformat the USB device to a linux filesystem then it's just a matter of setting the execute bit and you're good to go. Of couse then your USB device can't communicate with anything other than another Linux machine but it's only a matter of time before Linux dominates the desktop.

But usually external USB drives are formatted in FAT32 or NTFS and therein lies the problem. In the good old days these would automatically mount with the user as owner and all files executable and life was good. But then someone in Linuxdom thought "that doesn't make any sense - even simple *.txt and *.log files are being made executable", so they changed it such that all files are not executable.

When you mount a FAT32 or NTFS partition in Linux you are looking at a view. This view superimposes a set of file permissions that permeate all files contained within that partition because a given Windows file does not contain any Linux permission bit's to set individually. The old way had them all executable the new way none of them.

---

### Post by danelwillis on 2012-11-05
Its been a while since this was commented on and I was wondering if there is any new solutions to this old problem. I have the new Katana and I still cant change permission or make the usb bootable.

---

### Post by mcduck on 2012-11-05
> **danelwillis said:**
> Its been a while since this was commented on and I was wondering if there is any new solutions to this old problem. I have the new Katana and I still cant change permission or make the usb bootable.

easy. run the script by specifing the shell and giving the script as a parameter, reather than trying to just execute the script itself. That way you shouldn't need the execute permission on the script file.

```
sh bootinst.sh
```
instead of
```
./bootinst.sh
```

What comes to changing the permissions given to a FAT or NTFS filesystem, that's something you'd need to do at the time it's mounted. If you don't need to have the drive in question always mounted with such permissions, but only need it once to set things up, the easiest way is to just mount the drive manually with the options you want.

---

### Post by danelwillis on 2012-11-05
I have tired mounting an using sh bootinst.sh and still no luck it. It wont let me change the permission on the usb or run the it.

---

### Post by mcduck on 2012-11-05
> **danelwillis said:**
> I have tired mounting an using sh bootinst.sh and still no luck it. It wont let me change the permission on the usb or run the it.

There is no way you could possibly change the permissions after the drive has been mounted, as people have already said the FAT filesystem doesn't support that. The point is that you have to define the permissions you want *while you mount the drive*, in the mount command.

```
sudo mount -t vfat -o rw,user,umask=000 /path/to/device /path/to/mount/dir
```

---

### Post by Morbius1 on 2012-11-05
Or a variation of post #4 here: [http://ubuntuforums.org/showthread.php?t=2057357](http://ubuntuforums.org/showthread.php?t=2057357)

[] If the usb device is currently mounted unmount it.

[] Install udisks-glue
```
sudo apt-get install udisks-glue
```[] Create a file in your home directory:
```
mkdir $HOME/.udisks-glue.conf
```[] Add this content:
```
filter vfat {
    partition_table = false
    usage = filesystem
    type = vfat
}

match vfat {
    automount = true
    automount_options = { sync, 'umask=0000' }
    post_mount_command = "notify-send '%device_file\nhas been mounted at\n%mount_point' --icon=gnome-dev-harddisk-usb | nautilus  %mount_point"
    post_unmount_command = "notify-send '%device_file\nhas been unmounted' --icon=gnome-dev-harddisk-usb"
```[] Run the following command:
```
udisks-glue
```[] Insert the fat32 formatted usb device. 

It should mount with everything set to 777. If it does then add the udisks-glue command to your startup applications and all your fat32 usb devices will mount that way.

Note: to kill the udisks-glue process:
```
pkill udisks-glue
```

---

### Post by JKyleOKC on 2012-11-05
Note that this isn't available for Lucid; it didn't get into the repositories until Oneric...

---

