---
title: "GRUB: No File Found Rescue Prompt"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Ranemills on 2010-03-31
Hey all,
 
I've just gone to restart my laptop and I get GRUB2 telling me that there is no file found and it sends me to the rescue prompt. I had just deleted a partition that had held another version of ubuntu that I had tried and also it's swap file, well, I think it was its swap file. I didn't think at the time though I don't know whether this is the cause.
 
I also went to Synaptic and uninstalled a previous kernel version which I didn't want any more. When I ran update-grub after it still thought that was still there.
 
I've been on google and I found the community documentation about it. I came across this:
> 
**Grub shows rescue promt (and does not continue to boot)**
 
You may have bugy bios and location of your /boot/* files is not under the 1024 cylinder boundary. Create a small partition on the beginnig of the disk, mount it as /mnt/b, cp -av /boot/* /mnt/b; umount /mnt/b; mount /dev/small_partition /boot; grub-install /dev/<device>. 
 
How do I do what it says? I have loaded into a LiveCD and tried to make a partition but I've run out of primary partitions apparently. 
 
If you need any other information, please ask. I'm more than willing to do anything to get my laptop back.
 
Edit: I'm now getting a no such partition message. I'm going to stop messing around now.
 
Any help would be greatly appreciated.
Thanks

---

### Post by undecim on 2010-03-31
Grub is configured to use the partition you deleted. It's looking there for files to boot.

What you need to do is reinstall and reconfigure grub. We can do this from a live CD.

I helped someone else with this earlier today. Post #2 at [http://ubuntuforums.org/showthread.php?t=1443642](http://ubuntuforums.org/showthread.php?t=1443642) were the instructions I gave him. You need to do the same, but make sure that you replace "/dev/sda5" with your / partition and "/dev/sda" with the hard drive that your bios is set to boot from (i.e. your first hard drive, which is usally /dev/sda anyways.)

If you are unsure exactly what to do, open a terminal and run "sudo fdisk -l" and post the output of that here, then I can give you a specific command list.

---

### Post by Ranemills on 2010-03-31
That worked as far as getting GRUB to work.
 
Now I've got a message when Ubuntu tries to load saying > One or more of the mounts listed in /etc/fstab cannot yet be mounted: 
swap: waiting for *a long code*
Press ESC to enter a recovery shell
 
I'm guessing this is because I deleted the wrong swap partition?
 
Could you help with this as well please?
 
Thanks

---

### Post by undecim on 2010-03-31
> **Ranemills said:**
> That worked as far as getting GRUB to work.
 
Now I've got a message when Ubuntu tries to load saying 
 
I'm guessing this is because I deleted the wrong swap partition?
 
Could you help with this as well please?
 
Thanks

Yeah, that would do it. Multiple Ubuntu Installations can share swap partitions.

What you need to do is start the livecd again and create a new swap partition with GParted. If there is already a swap partition there, you don't need to create a new one.

Next, open a terminal and type "blkid | grep swap". You should see something like  ```
/dev/sdaX UUID="*a new long code*" TYPE="swap"
```

Then press ALT+F2 and type "gksu gedit". Once the text editor loads, open up /etc/fstab on the hard drive and find a line that looks like 
```
UUID=*a long code* none            swap    sw              0       0
```
And replace *a long code* with the *a new long code* from the blkid command you ran earlier. Save and exit.

Once you are all done, reboot and it should be working.

---

### Post by Ranemills on 2010-04-01
Hey there,

That solved it, thanks a lot!

I didn't use your exact method, but I got there in the end.

For reference I made a new swap partition and because "blkid | grep swap" didn't do anything for me (don't know whether that's my fault or not) I opened information in gparted for the partition. I copied the code from there into /etc/fstab on my ubuntu partition, saved and rebooted.

Thanks again, and sorry for replying so late, I had to go as soon as I fixed it.

---

