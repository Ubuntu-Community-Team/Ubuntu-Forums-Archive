---
title: "Only root can unmount"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-05-02
I used Ntfs Configuration Tool to automatically mount my windows partition, but when I try to unmount it, I get an error: 

"Error unmounting: unmount exited with exit code 1: helper failed with: unmount: only root can unmount UUID = A23C99163C98E97 from /media/5ABC1981BC195939"

Any ideas on how to fix this without changing my mount point or disabling automount?

Ubuntu version 10.04

EDIT: I can unmount it if I run gksu nautilus and unmount it from there, but then I can't mount it unless I reboot.

---

### Post by mikewhatever on 2010-05-02
Presumably, if one wants to automount a partition, one also wants it to stay mounted. In short, don't automount it at boot. After Ubuntu loads, you can open the file browser and click the Windows partition in the panel to mount it as user. You should also then be able to unmount it as user.

---

### Post by EnigmaticCoder on 2010-05-02
Now that it automounts the hard drive, how do I get it to not automount? Is it really so bad for it to automount?

---

### Post by WinterRain on 2010-05-02
> **EnigmaticCoder said:**
> Is it really so bad for it to automount?

No, not really. It's up to you if that's a bad thing. But in and of itself, it's not a bad thing.

---

### Post by mikewhatever on 2010-05-03
> **EnigmaticCoder said:**
> Now that it automounts the hard drive, how do I get it to not automount? Is it really so bad for it to automount?

Have you tried using NTFS-config again? It's not particularly bad to automount a drive, however, in the case of a Windows system partition, I'd think twice. It's so easy to accidentally delete half of Windows from Ubuntu, that I've seen discussions of hiding Windows partitions from the file browser to prevent accidental mounting.

---

### Post by egalvan on 2010-05-03
> **EnigmaticCoder said:**
> I used Ntfs Configuration Tool to automatically mount my windows partition, but when I try to unmount it, I get an error: 

EDIT: I can unmount it if I run gksu nautilus and unmount it from there, but then I can't mount it unless I reboot.

If you need root, then run umount with root permission (using "sudo")


```
sudo umount
```

read the man pages for exact usuage of 'umount'

My question would be "WHY do you need to un-mount the partition?"

The NTFS layer is very stable under Ubuntu.

---

### Post by agnes on 2010-05-03
Would you still want to disable automounting the internal drive/partition, editing *[/etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")* is how that is usually done. /etc/fstab is where the automount settings for internal volumes are keeped. Delete, or comment out the line (put a # before it) that automounts your windows (ntfs) volume, and it won't automount anymore.

Also from that site linked > *user *and* nouser*
These are very useful options. The user option allows normal users to mount the device, whereas nouser lets only the root to mount the device. nouser is the default, which is a major cause of headache for new Linux users. If you're not able to mount your cdrom, floppy, Windows partition, or something else as a normal user, add the user option into /etc/fstab.
^ Goes also for unmounting. You could theoretically also use 'users' instead of 'user'; 'user' is for any user, 'users' for those belonging to the group 'users'.

---

### Post by EnigmaticCoder on 2010-05-04
I appreciate the discussion, but I'm still curious why I have to be root to mount/unmount the drive and why there is no password prompt.

---

### Post by Odd_sam on 2010-05-04
Because when your mounting it at the start up using ntfs-config you are root. The root user mounted the drive and unless you become root you can't unmount it. You could have it auto mount using a start up script and this could fix the problem. It would take some testing.

---

### Post by paulochf on 2010-09-27
> **EnigmaticCoder said:**
> I used Ntfs Configuration Tool to automatically mount my windows partition, but when I try to unmount it, I get an error: 

"Error unmounting: unmount exited with exit code 1: helper failed with: unmount: only root can unmount UUID = A23C99163C98E97 from /media/5ABC1981BC195939"

Any ideas on how to fix this without changing my mount point or disabling automount?

Ubuntu version 10.04

EDIT: I can unmount it if I run gksu nautilus and unmount it from there, but then I can't mount it unless I reboot.

I have just messed with ntfs-config and didn't find any real solution, but one tip: ntfs-config backs up /etc/fstab at /etc/fstab-ntfs-config-save before changing it.

In other words, to get this fixed you just need to:
- remove your current /etc/fstab
- rename /etc/fstab-ntfs-config-save to /etc/fstab

;)

---

### Post by jtarin on 2010-09-27
You need to change your [/etc/fstab ]("https://help.ubuntu.com/community/Fstab")to define how you want to mount anything.

---

