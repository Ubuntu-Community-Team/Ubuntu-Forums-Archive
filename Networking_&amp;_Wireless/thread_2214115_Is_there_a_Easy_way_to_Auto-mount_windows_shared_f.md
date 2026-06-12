---
title: "Is there a Easy way to Auto-mount windows shared folders?"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by Wtdtexas on 2014-03-30
Is there a Easy way to Auto-mount windows shared folders?

Most solutions I have Seen require risky "file edits" of system config files. 

Is there a GUI way to Auto-mout Windows shared folders?

I have tried SMB4k that works(you have to add smb4k to startup apps), but is there a way in the current samba GUI's?

---

### Post by houstonbofh on 2014-03-30
> **Wtdtexas said:**
> Most solutions I have Seen require risky "file edits" of system config files.
Why do you feel that editing files is "risky?"  It is the way Linux is managed.  Most of those GUI tools just edit the file.  But if you use gedit to edit your config file, you have a backup right there if you need to revert.

To edit system files...
sudo gedit filename

The backup will be filename~ when you are done.  It only keeps one backup...

---

### Post by Wtdtexas on 2014-03-30
> **houstonbofh said:**
> Why do you feel that editing files is "risky?"  It is the way Linux is managed.  Most of those GUI tools just edit the file.  But if you use gedit to edit your config file, you have a backup right there if you need to revert.
The backup will be filename~ when you are done.  It only keeps one backup...

Yes, the video's stated to backup and if you did something wrong the system may not boot. That seemed risky, to me, but if the word was overstating the possible problems then I am sorry.

But the point was is there a GUI way of doing it, not thru SMB4k.

---

### Post by martijn6 on 2014-03-30
Wtdtexas

Good evening, dear sir, and may i wish you a welcome to the world of *nix. Where editing sysyem files is not only fun, but essential. It takes some getting used to, I know, and you *will* f$#^ up your system more than once. And after a while of this you will find you know a lot more about computers and programming in general than you knew. It's worth the effort, I think that's what I'm trying to say.

So let me hold your hand.

_**1 - Open the file**_ and just look at it. Go to a terminal and type
```
sudo gedit /etc/fstab/
```
which means
sudo = get root privileges
gedit = notepad-like text editor
/etc/ = direcory containing a lot of important system files
fstab = "filesystem table", the file describing your mount setup.

Now, you may know this. But you may not. No intent to patronize.

_**2 - The file will look something like**_
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6644f190-3cf4-49df-954b-b779604c6073 /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b92ea854-f2cb-4bb7-89b8-64dd7c676309 none            swap    sw              0       0
```

Things preceded by # are ignored. So the essential info is:
UUID=6644f190-3cf4-49df-954b-b779604c6073 **= UUID for my hard drive, sort of serial number**
 / = **root of the filesystem**
ext4 = **filesystem type**
noatime,errors=remount-ro 0       1 = options **(casually spoken!)**

Now, you're adding a Windows share over Samba of CIFS. So, you need to 

**_3 - DO_**
a) add a directory to your home folder, something like "server" (eg. /home/yourname/nas/)
b) REMEMBER TO ALWAYS MAKE A BACKUP FILE

**_4 - KNOW_**
a) the IP of your server
b) optionally, the location of your shared directory on it (eg ///192.168.0.10/share/)
c) the previously described directory (eg. /home/yourname/nas/)
d) also optionally but preferable, the share's username & password

_**5 - Make the backup copy**_
you're in a GUI now. Do save as... (eg fstab.old)

**_6 - Add_**

```
# Your comment here
//server-ip/server-share    /home/username/mount-dir/    cifs    username,password,options
```

or
```
# NAS share
//192.168.0.1/public /home/wtdtexas/share/ cifs username=wtdtexas,password=bigjuicysteaks,uid=1000,iocharset=utf8 0 0
```

_**7 - Save**_

_**8 - Open**_ the local share dir, then open a terminal and type
```
sudo mount -a
```
which will try to mount all entries in the fstab file.

_**9 - Check**_ the local share dir for contents.

Now, on a personal note: this is the way of *nix. Either this (and love it), or buy Apple. Better for your heart. :D

regards,
Martijn

---

### Post by Wtdtexas on 2014-03-30
I am a old burned out programmer, Linux has been a hobby for 10 years, I know the above way of doing the mount. 

I from time to time I re-learn, re-watch, to see what has changed. Hobby not job.

With SMB4K the prompt way is mostly no longer needed. 

Again, the point was is there a GUI way of doing it, not thru SMB4k.

To be told your way or leave is well so out of date.

---

### Post by houstonbofh on 2014-03-30
A) The program gedit is a gui app... ;)

B) Two people have now told you that is a way to go, and no one has said otherwise.

So I suspect that the answer is no, there is no purly GUI way to automount CIFS shares.  You could, however, have shortcuts in Nautilus, and it would seem like they are auto mounts.

---

### Post by bab1 on 2014-03-30
If you are just mounting Windows shares then you should be able to see them via the Nautilus file browser (smb://netbios_name/share).  The stand alone GUI share browser is Gigolo.  Both SMB4K and Gigolo use Samba libraries.

---

### Post by Wtdtexas on 2014-03-31
> **houstonbofh said:**
> A) The program gedit is a gui app... ;)

B) Two people have now told you that is a way to go, and no one has said otherwise.

So I suspect that the answer is no, there is no purly GUI way to automount CIFS shares.  You could, however, have shortcuts in Nautilus, and it would seem like they are auto mounts.


Thank you, lol that what I wanted, :P no, or yes and use this.

Trying to help a non-geek friend setup a unit, but he needs it to Auto-mount to his NAS. He would get lost in Gedit  or the prompt and drown, lol.

---

