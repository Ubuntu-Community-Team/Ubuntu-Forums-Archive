---
title: "File/Folder constantly revert to read-only"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by wind_dragon on 2009-01-02
As is described in the title my folders and files keep reverting to read-only a few minutes after the computer has been booted. Is there anyway to fix this and permanently keep my files read-write only without the terminal(i'm having trouble with that as well)?

---

### Post by cmnorton on 2009-01-03
Offhand this sounds like your file system was remounted read-only after a failure on the drive.

What Linux distro is this?

Does this happen to any other user on the system?

Do your logs indicated anything interesting? (/var/log/messages for starters).

What's the output of df?

---

### Post by scorp123 on 2009-01-03
> **wind_dragon said:**
> As is described in the title my folders and files keep reverting to read-only  Which files precisely?? Can you please give us their exact names and locations? e.g. /usr/bin/something, /home/yourusername/something, and so on?

---

### Post by wind_dragon on 2009-01-03
> **cmnorton said:**
> Offhand this sounds like your file system was remounted read-only after a failure on the drive.

What Linux distro is this?

Does this happen to any other user on the system?

Do your logs indicated anything interesting? (/var/log/messages for starters).

What's the output of df?

ubuntu 8.04
I am the only user, so i'm the admin(i think)

when i boot, Ubuntu does a disk scan and fails. I normally skip it because it can't continue due to various failures. I think my HDD might be dying.

Don't know what the "output of df" is, sorry.:(

---

### Post by wind_dragon on 2009-01-03
> **scorp123 said:**
> Which files precisely?? Can you please give us their exact names and locations? e.g. /usr/bin/something, /home/yourusername/something, and so on?

Its everything in the home and sys folders. (docs, music, pics, desktop,etc. even the hidden files are all locked)](*,)

---

### Post by taurus on 2009-01-03
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by wind_dragon on 2009-01-03
> **taurus said:**
> What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

I cannot access terminal.

---

### Post by handydan918 on 2009-01-03
Well, if you don't have another computer to use, write those commands down and hit ctrl+alt+f2 to cet to a console, and run them from there.

---

### Post by scorp123 on 2009-01-04
> **wind_dragon said:**
> when i boot, Ubuntu does a disk scan and fails.  Boot from the Live CD and then check the filesystem from there.

How to determine which HD partition to check:
```
sudo fdisk -l
```

This should spit out a list of all partitions and their type. Check those which are marked as being "Linux". Example:
```
> sudo fdisk -l
[sudo] password for sysadm: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00061ad7

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Purple"]/dev/sda1[/COLOR]**   *           1       60770   488134993+  83  **[COLOR="Purple"]Linux[/COLOR]**
/dev/sda2           60771       60801      249007+   5  Extended
**[COLOR="Purple"]/dev/sda5[/COLOR]**           60771       60801      248976   83  **[COLOR="Purple"]Linux[/COLOR]**

```

So I'd have to check the partitions **/dev/sda1**  and  **/dev/sda5**. Command:
```
sudo fsck /dev/sda1
``` ... depending on the damages it finds it will ask you a few questions. Usually it's best to reply "y" (=yes) and to let fsck repair the damages it encounters.

Repeat this step for each of your Linux data partitions; skip swap.

Once you're finished you should reboot. Your PC should now start without any complaints about damaged filesystems and the permissions should remain the way you set them, there should be no more unexpected changes.

---

### Post by wind_dragon on 2009-01-04
My sda5 says Linux+Solaris
run the code on this as well?

Edit:
Whoops. nevermind it says swap next to it

---

### Post by wind_dragon on 2009-01-05
so everything worked out ok on the reboot. On the next boot it reverted back to the old problem(the disk checks and a bunch of inode/orphan errors). OMG! this is so irritating!

---

### Post by Carl Hamlin on 2009-01-05
> **wind_dragon said:**
> so everything worked out ok on the reboot. On the next boot it reverted back to the old problem(the disk checks and a bunch of inode/orphan errors). OMG! this is so irritating!

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Yep - your initial impression is probably correct, and this drive is toasting. I'd recommend backing up your important data as soon as possible and replacing the drive.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklhpIoACgkQyLm4ydrABvfI0ACgxs3xQ7qsMd7I3ku6HOK+A2GB
bI8An0U+sHIiIQG79gqvY3Kc0J7iAwlg
=6Tpj
-----END PGP SIGNATURE-----

---

### Post by wind_dragon on 2009-01-06
As i thought. I'll just reinstall ubuntu on a different hard drive then.

---

