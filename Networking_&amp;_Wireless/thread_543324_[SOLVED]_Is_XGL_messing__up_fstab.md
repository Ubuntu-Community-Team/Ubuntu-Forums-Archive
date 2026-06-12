---
title: "[SOLVED] Is XGL messing  up fstab?"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by maharbA on 2007-09-05
I can't pin down the cause of this problem. Maybe someone out there can help -- or at least corroborate the problem.

I followed this thread:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)
to get my network drives (shared under Windows) to mount as local drives. I even got them to mount automatically at login.

Then I set up Compiz Fusion using XGL (I have an ATI card -- bummer) and one of the drives no longer mounts automatically. I can, however, mount it using "sudo mount -a" which, as far as I know, just remounts the drives that should be mounted automatically. 

(there is an issue with Windows-shared drives that prevents them from being mounted automatically without a username and pasword. The symptoms are similar to my problem, but I don't think that's the case here because: A-it was working before, and B-there is another drive with the EXACT same fstab settings which DOES mount automatically.)

Which brings me to my big question:
IS XGL MESSING UP MY DRIVE MOUNTING?

Here's the relevant part of my fstab:
```
# The following line will mount the drive named "EXTERNAL (G)", which is on the computer named "new_dell" to the folder /home/ganco/G_Drive (ADDED ON JULY 28, 2007)
//new_dell/EXTERNAL\040(G) /home/ganco/G_Drive   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0

# The following line will mount the drive named "C", which is on the computer named "new_dell" to the folder /home/ganco/NewDell_C (ADDED ON JULY 28, 2007)
//new_dell/C /home/ganco/NewDell_C   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0
```

PS: "G_Drive" is not mounting automatically, "NewDell_C" is. "/home/ganco/.smbpasswd" contains the username and password info for the drives (as you can see, they both drives are linked to the same credentials file.

---

### Post by noob12 on 2007-09-05
I don't think XGL is messing up your fstab.

More likely things to check:
- If you have /home on a separate partition, make sure it gets mounted in a cycle before the cifs/smbfs mounts.
- Try putting the credentials under root's home (/root) and make it owned by root and mode 600.
```

sudo mv /home/ganco/.smbpasswd /root/smbcredentials
sudo chown root:root /root/smbcredentials
sudo chmod 600 /root/smbcredentials

```

---

### Post by maharbA on 2007-09-05
Thanks, noob12

Before I do that, though, I want to make sure -- once I run those commands I won't have to log in as root to have these drives mounted automatically, will I? I'd like to keep the final setup as simple as possible.

Also, why does one drive mount and the other not? It's so weird.

---

### Post by noob12 on 2007-09-05
No the automatic mount at boot time runs as root and when you do **sudo mount -a** you're also running as root.

However, I had not understood that only the first drive isn't mounting.  I don't have a good explanation for that unless you have /home on a separate partition and it just happens to mount in time for the second one to work.

---

### Post by maharbA on 2007-09-06
> unless you have /home on a separate partition and it just happens to mount in time for the second one to work.

That's what it seems like to me, but there's no 2nd partition. That's kinda why I though it was XGL. If the XGL session delayed NetworkManager from connecting until fstab had already passed the first drive ...

I suppose I could switch the order of the two drives in fstab to see -- BUT WAIT
After a kernel update, they both mount (at least for now).

**Thanks for all your help, noob12.** And if anybody can think of any other reason (wild guesses?) I'd like to hear them -- in case this happens again.

UPDATE: It happened again :(
I ... just ... don't ... get ... it

---

### Post by maharbA on 2007-09-15
I switched the order of the two drives in fstab. So now it looks like this:
```
# The following line will mount the drive named "C", which is on the computer named "new_dell" to the folder /home/ganco/NewDell_C (ADDED ON JULY 28, 2007)
//new_dell/C /home/ganco/NewDell_C   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0

# The following line will mount the drive named "EXTERNAL (G)", which is on the computer named "new_dell" to the folder /home/ganco/G_Drive (ADDED ON JULY 28, 2007)
//new_dell/EXTERNAL\040(G) /home/ganco/G_Drive   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0
```

Now It mounts G_Drive instead of NewDell_C. 
Is there a way to pause fstab so that it doesn't skip the first drive?

PS: there is a Windows partition on the laptop itself (remember the two drives listed above are share over the network) which is listed in fstab above these two drives. It mounts correctly with no problems.

---

### Post by noob12 on 2007-09-16
Do you mind posting the whole file?  Maybe there's something just before that line that is messing things up?  Or there's a condition where the network mount is depending on some service starting that hasn't yet started when the first one gets processed?

---

### Post by maharbA on 2007-09-16
On a hunch, I changed /etc/fstab once again. I duplicated the entry for the first drive (the one that won't mount). Here's the whole file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b7a7bce4-09c2-40ae-9ca7-ba30c4d81b00 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c392e319-947a-48e6-9e92-fa87f0f40d04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Generated by Automatix
/dev/sda1   /media/WinDrive   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

# The following line will mount the drive named "C", which is on the computer named "new_dell" to the folder /home/ganco/NewDell_C (ADDED ON JULY 28, 2007)
//new_dell/C /home/ganco/NewDell_C   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0

# The following line will mount the drive named "EXTERNAL (G)", which is on the computer named "new_dell" to the folder /home/ganco/G_Drive (ADDED ON JULY 28, 2007)
//new_dell/EXTERNAL\040(G) /home/ganco/G_Drive   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0

# DUPLICATE -- The following line will mount the drive named "C", which is on the computer named "new_dell" to the folder /home/ganco/NewDell_C (ADDED ON SEPTEMBER 16, 2007) IT IS DUPLICATED TO ALLOW PROPER TIMING OF MOUNT COMMANDS
//new_dell/C /home/ganco/NewDell_C   smbfs  auto,credentials=/home/ganco/.smbpasswd,user,uid=ganco   0 0
```

As you can see, the drive "NewDell_C" is duplicated because whichever drive is listed in that place will not get mounted. I had "G_Drive" listed first and it wouldn't mount, so I switched them and "NewDell_C" wouldn't mount. So I got the idea to put "NewDell_C" in there again and ...
IT WORKS! (at least for now -- I've been fooled before).

REMEMBER: this file (without the duplicated entry) worked swimmingly for months before I got the bright idea to but Compiz Fusion (with XGL -- damn you ATI) on there.

Maybe with the promised open-sourced ATI drivers, I can go back to that first fstab file, as I would no longer need XGL. In the meantime, if anyone is having this problem, try duplicating the drive that won't mount farther down the list.

It's not pretty, but it seems to work.

---

