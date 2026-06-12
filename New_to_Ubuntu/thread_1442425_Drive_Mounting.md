---
title: "Drive Mounting?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by swan14 on 2010-03-30
Hi guys,

I just set up Ubuntu 9.10 to trial as a home server.  I wish to run this headless and control it via VNC.  I'm a complete ubuntu noob so bare with me.

So I managed to set up software raid 5 using the alt disk install.  It seems to be running fine giving me total usable space of around 1.8GB (I'm using 3x 1TB disks).

Every time I log in i need to re-mount my raid array.  Is there anyway of setting it up so this array is mounted automatically. If its not mounted obviously I can't access any files etc through the network.

I think it may have something to do with how I setup the array?  Under the disk utility it says 'Not Partitioned'.  When I did the install was I meant to give it a /home partition?  From memory all I did was set them as software raid.  Once its mounted however, I can access it and copy/paste files from my W7 machine.

tl;dr


[LIST]
[*]why do I need to mount my software raid-5 array each time I log in/resart the pc.?
[*]Is it because I didn't partition it correctly during the install process.?
[/LIST]

Thanks in advance,

Sam

---

### Post by undecim on 2010-03-30
can you post the contents of /etc/fstab? (from a terminal, you can run "cat /etc/fstab" to do that)

What steps do you take to mount the raid volume?

Also, SSH is the best way to administer a server, IMHO. It just takes little longer to learn than VNC.

---

### Post by swan14 on 2010-03-30
Thanks for replying.

Is this what you are after?

sam@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=07833ba9-ebff-47b5-8570-efdbcb6a02c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=64415eaa-44ce-42fc-b58f-ea8abe5b8d8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
sam@ubuntu:~$ 


As for the steps I take lets say I have just rebooted (my raid volume is named "Raid5").

So if I click on "Places" I can see a button called Raid5 below the Computer button.  I click on raid5 and a authentication window pops up which says "Authentication is required to mount the device".

Once I enter the password a browser pops up with the files I have stored on the array.  So thats all I need to do to mount it.  I know its not much but as I plan to run it headless it would be nice if I didn't have to remote into ubuntu to mount the array  each time a reboot is required etc..

As for SSH I will look into it.  I've been a windows man forever but I'm willing to try new things!

Cheers,

Sam

---

### Post by swan14 on 2010-03-30
FYI that terminal read-out I posted was BEFORE I mounted the raid5 array.  Let me know if you need another one post mounting!

Sam

---

### Post by undecim on 2010-03-30
okay, in my /etc/mdadm/mdadm.conf, I have a line like this:

```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e9147578:3dd0b9fd:e30fb7aa:a85ba8f7
```

That is for my RAID 1 setup (hence the level=raid1). You should see a similar line but with different parameters. The /dev/md0 part should be the same.

That /dev/md0 part is the device and acts just like any hardware device

If that's all fine and dandy, that means that your raid is configured to setup on boot, and just isn't set to mount.

What we want to do is add an fstab line to mount it on boot.

This command should do just that:
```
echo "/dev/md0 /mnt/raid5 ext4 defaults 0 0" | sudo tee -a /etc/fstab 
```

Make sure to replace /dev/md0 with your raid device, /mnt/raid5 with where you would like it to be mounted, and ext4 with the filesystem type of the device. 

Then, make sure that the mount point you chose exists. Remember that if it's currently mounted with device-kit (like you would do when using the GUI to mount it) then it's current mount point in /media/ will disappear when device-kit unmounts it. If you want to use the same folder in /media/, then unmount the device via the GUI and create the new folder as explained below

If the mount point doesn't exist, you can create the folder with "sudo mkdir /media/raid" (where /media/raid is the mount point you chose)

Then, mount the device with "sudo mount /dev/md0"

---

### Post by swan14 on 2010-03-30
ok I got this :

ARRAY /dev/md0 level=raid5 num-devices=3 UUID=[B]2632e3cd:d266b49a:b1ba91d9:9b88b437
[/B]
So that seems to be fine.

When entering the command to mount the device, when you say to use the /dev/md0 are you refering to the UUID number  bolded above?

---

### Post by undecim on 2010-03-30
[s]You can use UUID if you want. It's a litte more flexible in most cases, but doesn't make much of a difference with raid devices.

The UUID of the filesystem on the raid will be different though. you can find it with
```
ls -l /dev/disk/by-uuid/ | awk "/md0$/ {print \$8}"
```

then use UUID=[UUID from the filesystem] instead of /dev/md0

or better yet, all in one line:
```
echo "UUID=`ls -l /dev/disk/by-uuid/ | awk '/md0$/ {print \$8}'` /mnt/raid5 ext4 defaults 0 0" | sudo tee -a /etc/fstab
```

Just make sure the first command returns a UUID before running the one-liner. Just to double-check.[/s]

EDIT: nevermind, I missed a bit of your post. You are on the part where you are mounting it. When using the command to mount it, use /dev/md0. You could also use the mount point

---

### Post by swan14 on 2010-04-02
Finally manged to get the drive mounting automatically.

Thanks for your help dude.

I know this is OT but when you mentioned using SSH would this be just when I'm away from my home network and wanna do stuff to my server over the net?  I assume VNC is fine for use while I'm just using my home network?

Cheers,

Sam

---

### Post by undecim on 2010-04-02
You can use SSH on your local network or from the internet (if you configure port forwarding on your router.)

You don't have to use SSH if you don't want to though. If you find VNC easier, then by all means keep using it. I would still recommend setting up SSH, because it's more secure and you can tunnel connections to your computer (like the one you would use for VNC) over the internet when you are not on your local network.

grdc even has a feature that will handle all of that automatically. 

Of couse, you can also set up X11 forwarding for SSH which will allow you to run GUI commands. Just make sure the on your server the "X11Forwarding" option in /etc/ssh/sshd_config is set to "yes" and uncommented. The on any client that you want to use X11 forwarding, you can either use the -X flag every time you connect, or make sure "X11Fowarding" in /etc/ssh/ssh_config is set to "yes" and uncommented.

Then, from the SSH shell type "gnome-control-center" for exampleto get the Gnome Control Center opened on your desktop.

---

