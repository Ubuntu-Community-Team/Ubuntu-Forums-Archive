---
title: "Permission Denied after Pysdm automount"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by mugen812 on 2010-02-01
Hi, I just installed Ubuntu Netbook Remix 9.10 on a Asus EEE 900 and ran into some trouble with auto mounting the 16gb drive. I've searched the forums and decided that I would do it with pysdm. Using the program was simple enough and it does automount, but I ran into trouble when I tried using rhythmbox. When ever I try to download a podcast to the drive, it gives me a permission denied message. I've played with the assistance tab in pysdm, and nothing seems to fix it. If anyone has any suggestions, I would greatly appreciate it.

p.s. first time Linux user and so far it's a lot easier than I thought!

---

### Post by Morbius1 on 2010-02-01
When in doubt it's better to go back to the Jedi way. Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type [B]mount
[/B]

---

### Post by warfacegod on 2010-02-01
Open a Terminal:

```
sudo chown -R username:usergroup /media/drivename
```

That will make you the owner of the drive. Look in the /media folder for drive name. username/group will need to be changed to your info (obviously).

Warning: If there is an Operating System on the drive then doing this is not a good idea.

---

### Post by drs305 on 2010-02-01
I wrote a [guide]("http://ubuntuforums.org/showthread.php?t=872197") in these forums about using pysdm but the app is old and a bit dated. 

The problems you are having are most likely due to the fstab settings. Permissions for non-linux filesystems such as vfat and ntfs are set at the time of mounting and can't be changed. 

Once you post the information Morbius1 requested we will be able to tell you how to alter your /etc/fstab setting to make you the owner of the mounted folders. That should solve your problem.

You can also learn more about fstab by visiting bodhi.zazen's fstab page:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by mugen812 on 2010-02-01
Thanks for everyone's help so far. I will post my findings today when I get home.

---

### Post by mugen812 on 2010-02-01
> **Morbius1 said:**
> When in doubt it's better to go back to the Jedi way. Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type [B]mount
[/B]
OK, here are the results. Now bear in mind I decided to reinstall Ubuntu last night, so this is without pysdm mounting it.

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thikun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thikun)
/dev/sdb1 on /media/FILES type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush

---

### Post by Morbius1 on 2010-02-01
That looks like the output of **mount**. 

What about the rest of the commands?

Is this the partition you are having trouble with:
> /dev/sdb1 on /media/FILES type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,  shortname=mixed,dmask=0077,utf8=1,flush If it is, does rhythmbox still have a problem with it?

[COLOR=Blue]EDIT: I'm guessing that this is an external usb drive, is that correct?[/COLOR]

---

### Post by drs305 on 2010-02-01
Assuming you are trying to mount sdb1 *and*: you want it in fstab (which is what pysdm was going to do).

Unmount sdb1:
```
sudo umount /dev/sdb1
```

Make a mountpoint. If the mountpoint is in /media, it will show on the Desktop. If it's in /mnt, it won't. For this example, we'll put it in /media and call it "files". Change the name as you wish.

```
sudo mkdir /media/files
```

Next, change the ownership of the mountpoint/folder to yourself. This isn't necessary for mounting vfat/ntfs partitions, but it will probably be useful later on to own it yourself.

```
sudo chown -R *yourusername:* /media/files
```

Find the UUID for sdb1:
```
sudo blkid -c /dev/null | grep sdb1
```

Next open /etc/fstab for editing:
```
gksu gedit /etc/fstab
```

Add this line **with the actual UUID**:
> UUID=**04E1-CB70** /media/files vfat user,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0

Save the file, then mount the new entry:
```
sudo mount -a
```
This will mount all listings in fstab. If you get no error message (i.e. nothing appears to have happened), your sdb1 is now mounted properly on /media/files.

---

### Post by Morbius1 on 2010-02-01
That's all very impressive unless of course it's an external usb device. Then , for one thing, it will only work if the usb device is plugged in or turned on when the box is booted.

Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**

---

### Post by mugen812 on 2010-02-01
> **Morbius1 said:**
> That looks like the output of **mount**. 

What about the rest of the commands?

Is this the partition you are having trouble with:
If it is, does rhythmbox still have a problem with it?

[COLOR=Blue]EDIT: I'm guessing that this is an external usb drive, is that correct?[/COLOR]
Actually, it's the second ssd that is on the netbook. It came with a 20 gb, but ubuntu gets installed onto the onboard SSD that is 4gb

---

### Post by mugen812 on 2010-02-01
Drs305, i tried using your steps, but i think i might have gotten an error towards the end. here is the output of my terminal

thikun@thikun-Linux:~$ sudo unmount /dev/sdb1
sudo: unmount: command not found
thikun@thikun-Linux:~$ sudo umount /dev/sdb1
thikun@thikun-Linux:~$ sudo mkdir /media/files
thikun@thikun-Linux:~$ sudo chown -R thikun: /media/files
thikun@thikun-Linux:~$ sudo blkid -c /dev/null | grep sdb1
/dev/sdb1: LABEL="FILES" UUID="04E1-CB70" TYPE="vfat" 
thikun@thikun-Linux:~$ gksu gedit /etc/fstab
thikun@thikun-Linux:~$ sudo mount -a
mount: special device UUID=2c8a15c5-ee8f-4092-8dec-b97ab8d0e6ea does not exist
thikun@thikun-Linux:~$ 

I tried adding the line and this is what it looks like in my fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1ed75297-cdd8-49e2-a8a7-e95897669420 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=90674e03-b86f-4536-b0d3-872c46797e1b none            swap    sw              0       0
UUID=2c8a15c5-ee8f-4092-8dec-b97ab8d0e6ea /media/files vfat user,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0

---

### Post by drs305 on 2010-02-01
Sorry I wasn't clear enough. You must substitute the UUID value you got for the one in the example. Since we now have the UUID, I've put the actual value in my example.

---

### Post by mugen812 on 2010-02-01
> **drs305 said:**
> Sorry I wasn't clear enough. You must substitute the UUID value you got for the one in the example. Since we now have the UUID, I've put the actual value in my example.
Thanks so much for your help. I really appreciate it! I think i finally got it to work using your instructions. I rebootted it, it mounted automatically, and my podcasts feed now download to it. My ONLY other minor gripe is that there is now another image or mount that is showing up (called "files")
[IMG]http://i40.photobucket.com/albums/e246/mugen812/Screenshot.png[/IMG]

As you can see to there, is a second drive or image there under "Volume". Is that supposed to be there and if not can i remove it?

---

