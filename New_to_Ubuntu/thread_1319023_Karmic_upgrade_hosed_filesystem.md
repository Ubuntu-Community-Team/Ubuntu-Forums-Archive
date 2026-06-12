---
title: "Karmic upgrade hosed filesystem"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ofb on 2009-11-08
I've got an unhappy upgrade here. It seems to have destroyed the existing /home partition.

The upgrade process took about 2 hours and appeared to proceeded normally.

On reboot, I got the little white Ubuntu logo, followed by this:

```

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for UUID=2500e823[etc]
/home/o/Thorax_B: waiting for /dev/disk/by-uuid/f7e6f[etc]
/home/o/Thorax_A: waiting for /dev/disk/by-uuid/500ae[etc]
Press ESC to enter a recovery shell

```

I put in the 9.10 LiveCD and took the two attached screenshots.

In these, Palimpsest shows the partition as "Unrecognized", GParted shows the partition as normal, although without a mount point listed, and Nautilus shows /home as empty.

This is very worrying. I don't know where to start to access the partition for recovery, or to fix this install.

Here's the fstab:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=a53ac1fd-b24e-4de4-9328-eba25c6cf59b /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=2500e823-24dc-4a8c-8a55-2054e4d6c144 /home           ext3    relatime        0       2
# /home/o/NewDrive was on /dev/sdc1 during installation
UUID=f7e6f14b-a76e-4329-9d60-d50c0580a1f1 /home/o/Thorax_B ext3    relatime        0       2
# /home/o/Thorax was on /dev/sdb1 during installation
UUID=500ae9f4-7cbb-4657-807d-fbc48385eb5b /home/o/Thorax_A  ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=626a140e-b774-4695-978b-8f01d8ea984e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# renamed NewDrive to Thorax_B
# renamed Thorax to Thorax_A

```



Oh... I just had an idea and tried the ever-reliable Knoppix LiveCD. And I can access that partition just fine with it.

That's encouraging, but I still don't know what to make of this.

... possibly irrelevant? Knoppix uses the old hda, hdb, etc system for partitions. Not the sda, sdb, etc system Ubuntu changed to around 8.04.

---

### Post by jbrown96 on 2009-11-08
Your UUIDs are conflicting. That's really, really odd; let me explain UUIDs. They are supposed to be an ideally globally (world-wide) unique identifier for a hard drive partition; however, they may not be, but are supposed to be guaranteed to be unique on a single system. 

Let's try to fix your UUID. Boot the 9.10 LiveCD. Open a terminal and do the following:
[LIST=1]
[*]mount your /. ```
sudo mkdir /media/root && sudo mount /dev/sda3 /media/root
```
[*]cat your /etc/fstab to compare your UUID. ```
cat /etc/fstab
```
[*]check your UUIDs ```
ls /dev/disk/by-uuid/
```
[*]compare your UUIDs. Hopefully they won't all be messed up, so you should be able to find one that doesn't match; that will be /home and change the UUID in /etc/fstab to match it. 
[*]If you have multiple unknown UUIDS, then we need to mount each of them and see if they are /home
[*] ```
sudo mkdir /media/home && sudo mount /dev/disk/by-uuid/...
``` You will need to enter the UUID of the unknown UUID. You can press tab twice to get the possible choices, then type a few characters and press tab to fill in the entire UUID. Then ```
cat /media/home
``` If that has your user folder, then we have found /home and update /etc/fstab accordingly. If not, then ```
sudo umount /media/home
``` and proceed through the other UUIDs
[/LIST]

---

### Post by ofb on 2009-11-08
_Thank you_. But I'm afraid my output isn't what you're expecting.

> cat your /etc/fstab to compare your UUID.

```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

Perhaps you mean the fstab on my physical drive, not the LiveCD session one? If so, that's in the first post.

> check your UUIDs

```
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/
500ae9f4-7cbb-4657-807d-fbc48385eb5b  a53ac1fd-b24e-4de4-9328-eba25c6cf59b
626a140e-b774-4695-978b-8f01d8ea984e  f7e6f14b-a76e-4329-9d60-d50c0580a1f1

```

> compare your UUIDs. Hopefully they won't all be messed up, so you should be able to find one that doesn't match; that will be /home and change the UUID in /etc/fstab to match it.

What's wrong is the UUID for /home is missing from that list. There should be five. The four returned do match the rest in the fstab though.
 

(Great reply, btw. 5 stars for clarity and directness.)

---

### Post by ofb on 2009-11-08
I just booted the 9.04 LiveCD, and it sees the partition fine.

```

ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/
2500e823-24dc-4a8c-8a55-2054e4d6c144  a53ac1fd-b24e-4de4-9328-eba25c6cf59b
500ae9f4-7cbb-4657-807d-fbc48385eb5b  f7e6f14b-a76e-4329-9d60-d50c0580a1f1
626a140e-b774-4695-978b-8f01d8ea984e

```

What could possibly be going on here? How can Karmic only see four of five partitions?

---

### Post by ofb on 2009-11-08
Crazy. "sudo lshw" shows the missing sda1 with the correct UUID.

---

### Post by jbrown96 on 2009-11-09
Oh, wow. I just re-read your /etc/fstab, and the problem is that /home is listed three times in there with different UUIDs (not sure how I missed that). My guess is that it tries to mount a partition that is already mounted. You need to boot the Ubuntu LiveCD and go through each of those UUIDS (25..., f7..., 50...) and mount them, then figure out which is the right one. 
Do the steps that I listed in an earlier post for each of the three possible /home UUIDs. Once you figure out the right one, do the following:
[LIST=1]
[*] backup your fstab ```
sudo cp /etc/fstab /etc/fstab.back
``` [*] delete the duplicates from /etc/fstab. Delete the two duplicate lines for /home in a text editor[/LIST]

---

### Post by running_rabbit07 on 2009-11-09
I would say reinstall Jaunty without formatting the /home. If everything turns out fine, you should back up you /home files, then use the 9.10 disk to do a clean install.

Best of luck.

---

### Post by ofb on 2009-11-09
Er, no, /home isn't listed 3 times in fstab. I think you are looking at the paths /home/o/Thorax_A and /home/o/Thorax_B. Those are mount points for two more drives.

There's nothing wrong with the fstab -- it's the one that's been in use with 9.04. Also note the different output for 'ls /dev/disk/by-uuid/' on the two LiveCDs; Karmic cannot see the /home partition. Something is wrong with Karmic other than my install.


running_rabbit07 - yeah, that's pretty much been my backup plan. My idea would be /only/ a reinstall of Jaunty, because the Karmic LiveCD cannot see /home through 'ls /dev/disk/by-uuid/'. Hence I've no reason to think a clean install of Karmic would turn out better.

(I should caution anyone who needs to revert like that. It might turn out a little messy. The half-install of Karmic has probably modified some of the 'dot-config' files under /home/[user name]. You might end up having to purge those, re-install fresh, and then re-assemble all your personal application prefs.)


Anyhow... I got fed up and tried something foolish.

In fstab I changed that UUID to the device path /dev/sda1.

On boot I got this error,
```

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for /dev/sda1
/home/o/Thorax_B: waiting for /dev/disk/by-uuid/f7e6f[etc]
/home/o/Thorax_A: waiting for /dev/disk/by-uuid/500ae[etc]
Press ESC to enter a recovery shell

```

And then that disappeared and the boot proceeded this time.

I checked 'ls /dev/disk/by-uuid/' and the stray UUID was still missing. I updated. (New kernel.) Rebooted. Same pause for error. Checked 'ls /dev/disk/by-uuid/' again, and yeah the stray UUID is still missing. The kernel update hasn't fixed it.

But it appears fine otherwise. I've been trying out apps and whatnot for about an hour.

I haven't checked Palimpsest. It's on the LiveCD but doesn't appear to be carried over with the install.

So I don't know. It's nice to have the box back up, but I'm using a kludge, not a solution. There's definitely something wrong with Karmic and UUIDs, but I haven't figured out what.

---

### Post by garvinrick4 on 2009-11-09
OFB what did you use to attach thumbnails. Very clear.

---

### Post by ofb on 2009-11-09
> **garvinrick4 said:**
> OFB what did you use to attach thumbnails. Very clear.

On the 'Reply' page, look under Addition Options. Click 'Manage Attachments', and you'll get a pop-up window to help upload files from your computer. The thumbnails are auto-generated.

---

### Post by ofb on 2009-11-22
Solved. See my bug report for links to solution and technical information.
[https://bugs.launchpad.net/ubuntu/+bug/479590](https://bugs.launchpad.net/ubuntu/+bug/479590)

---

