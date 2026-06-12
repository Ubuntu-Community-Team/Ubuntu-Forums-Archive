---
title: "I've broken something - can't boot"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by floatingpoint on 2009-01-20
It was a matter of time, I suppose, until something went horribly wrong!

I turned on my PC today, and when the Ubuntu loading bar appeared, it stopped about 1/5th of the way, and a message appeared below saying something like,

"Unclean shutdown, filesystem check started
"/dev/sda1      0%  (1/5, 1/591)"

It sat at this for a while and then the screen went black. Then, looooads of text scrolling through, seemingly performing various checks. Too fast to read, however when it stopped this was what was left on the screen:

```
fsck 1.41.3 (12-Oct-2008)
/dev/sda1 contains a filesystem with errors, check forced.
Checking drive /dev/sda1: 0% (stage 1/5, 1/591)
Checking drive /dev/sda1: 0% (stage 1/5, 1/591)
Error reading block 262327 (attempt to read bloack from filesystem resulted in short read) while getting next inode from scan.


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
           (i.e. without -a or -p options)

fsck died with exit status 4.


*An automaric file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in the maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
**root**@kevin_desktop:~#
```

So. I was placated by President Obama's inaugural speech, and the images of Bush & Cheney's departure - this stopped me from pulling my hair out. I waited until the new administration and their guests went off to lunch and then decided to come over here and ask for help.

All of my important files are (or should be) on a second HDD with no OS on it. Are they safe?

Also, I just bought a new sound card. I want to install Ubuntu Studio. If this install is humped, can I make a live disk of that and just boot from CD?

---

### Post by taurus on 2009-01-20
At the prompt, run

```
fsck /dev/sda1
```

---

### Post by fuser312 on 2009-01-20
simple fsck will work too
or from the boot menu, list choose recovery mode, and you will know what to do

---

### Post by floatingpoint on 2009-01-20
```
root@kevin_desktop:~# fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 contains a filesystem with errors, check forced
Pass 1: Check inodes, blocks, and sizes
Error reading block 262333 (Attempt to read block from filesystem resulted in
 short read) while getting next inode from scan. Ignore error <y>?
```

Recovery mode threw up the same as my first boot iirc.

---

### Post by taurus on 2009-01-20
Answer **y** to that question.

---

### Post by floatingpoint on 2009-01-20
```
Error reading block 262333 (Attempt to read block from filesystem resulted in
 short read) while getting next inode from scan. Ignore error <y>? yes

Error reading block 262334 (Attempt to read block from filesystem resulted in
 short read) while getting next inode from scan. Ignore error <y>?
```

262335, 262336, 262337... I continued answering Y until it changed. Do you want to know what it changed to? I'm gonna go write it down, so I can bring it through here, and type it out...


It ended in ```
Force rewrite <y>?
```

---

### Post by floatingpoint on 2009-01-20
After going through that, I seem to be logged in as me again, but the GUI wont start.

```
Ubuntu 8.10 tty1
kevin-desktop login:
Password:
-bash: no job control on this shell
kevin@kevin-desktop:~$
```

Where to now?

---

### Post by taurus on 2009-01-20
What happens when you run

```
startx
```

Did the power go out when you were using Ubuntu?

---

### Post by floatingpoint on 2009-01-20
Nah, I understand where you're coming from obviously, I had to think back when I first saw the 'Unclean shutdown' message, but I just turned my PC off and went to bed last night. I had been doing stuff to try and get my soundcard/audio interface recognised, but it seemed to work fine, and I restarted a couple times to check it was still working.

Anyway, 

```
kevin@kevin-desktop:~$ mktemp: cannot create temp file /tmp/serverauth.QeLCnR5612: Read-only file system
/usr/bin/startx: line 158: cannot create temp file for here document: Read only file system
xauth: error in locking authority file /home/kevin/.Xauthority
/usr/bin/startx: line 170: cannot create temp file for here document: Read-only file system
xauth: error in locking authority fle /home/kevin/.Xauthority
/usr/bin/startx: line 170: cannot create temp file for here document: Read-only file system


Fatal server error:
Could not create lock file in /tmp/.tX0-lock


giving up.
xinit: Connection refused (errno 111): unable to connect to Xserver
xinit: no such process (errno 3): Server error
xauth: error in locking authority file /home/kevin/.Xauthority
kevin@kevin-desktop:~$
```

---

### Post by taurus on 2009-01-20
Okay, I need to see some outputs from a prompt regarding permissions of your harddrive & $HOME.

```
cat /etc/fstab
mount
ls -la /tmp
ls -la ~
```

---

### Post by Ptero-4 on 2009-01-20
You need to run "fsck -p" on your problem volume from a LiveCD. That way it will be marked clean and booted read-write (from the log you posted it seems that your partition got mounted read-only).

---

### Post by floatingpoint on 2009-01-20
My dad wants on (this *is* his PC I suppose), I'm gonna try to convince my sister to let me use her laptop though. Outputs to follow.

---

### Post by floatingpoint on 2009-01-20
Okay, /etc/fstab; the output is messy so I've tried to format it for you (it would be difficult for me to replicate since I need to write it down and then type it out on this pc):

**<file system>**proc **<mount points>**/proc **<type>**proc **<options>**defaults **<dump>**0 **<pass>**0

**<file system>**/dev/sda1 **<mount points>**UUID=89408c9a-51ad-40f9-a689-82c67b37549d / **<type>**ext3 **<options>**relatime,errors=remount -ro **<dump>**0 **<pass>**0

**<file system>**/dev/sda5 **<mount points>**UUID=d91a3ded-4040-410f-b35c-74bde31cc503 none **<type>**swap **<options>**sw **<dump>**0 **<pass>**0

**<file system>**/dev/scd1 **<mount points>**/media/cdrom0 **<type>**udf,iso9660 **<options>**user,noauto, exec,utf8 **<dump>**0 **<pass>**0

**<file system>**/dev/sdb1 **<mount points>**/media/data **<type>**ntfs-3g **<options>**auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 **<dump>**0 **<pass>**0

Make sense?

Mount:

```
/dev/sda1 on / type ext3 (rw, relatime, errors=remount -ro
tmpfs on /lib/init/rw type tmpfs (rw, nosuid, mode=0755)
/proc on /proc type proc (rw, noexec, nosuid, nodev)
sysfs on /sys type sysfs (rw, noexec, nosuid, nodev)
varrun on /var/run type tmpfs (rw, nosuid, mode=0755)
varlock on /var/lock type tmpfs (rw, noexec, nosuid, nodev, mode=1777)
udev on /dev type tmpfs (rw, mode=0755)
tmpfs on /dev/shm type tmpfs (rw, nosuid, nodev)
devpts on /dev/pts type devpts (rw, noexec, nosuid, gid=5, mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw, mode=755)
/dev/sdb1 on /media/data type fuseblk (rw, noexec, nosuid, nodev, allow_other, default_permissions, blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw, noexec, nosuid, nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw, nosuid, nodev, user=kevin)
/dev/scd1 on /media/cdrom0 type iso9660 (ro, nosuid, nodev, utf8, user=kevin)
```

ls -la /tmp

```
total 60
drwxrwxrwt   14   root   root   4069   2009-01-20   .
drwxrwxrwt   21   root   root   4069   2009-01-15   ..
drwx------    2   kevin  kevin  4069   2009-01-20   .esd-1000
drwx------    2   kevin  kevin  4069   2009-01-20   .exchange-kevin
drwxrwxrwt    2   root   root   4069   2009-01-20   .ICE-unix
drwx------    2   kevin  kevin  4069   2009-01-20   kde-kevin
drwx------    2   kevin  kevin  4069   2009-01-20   keyring-Vid910
drwx------    3   kevin  kevin  4069   2009-01-20   ksocket-kevin
drwx------    2   kevin  kevin  4069   2009-01-20   orbit-kevin
drwx------    2   kevin  kevin  4069   2009-01-20   pulse-kevin
drwx------    2   kevin  kevin  4069   2009-01-20   seahorse-raZspf
drwx------    3   kevin  kevin  4069   2009-01-20   Tracker-kevin.5709
drwx------    2   kevin  kevin  4069   2009-01-20   virtual-kevin.GMJIrB
-r--r--r--    1   root   root   4069   2009-01-20   .X0-lock
drwxrwxrwt    2   root   root   4069   2009-01-20   .X11-unix
```


ls -la ~: the output was huge, and ran well over one screen. I don't seem to be able to scroll up or down with arrow keys or page up/down. Is there any particular file you're interested in? From P-Z?

Just about to try your idea, Ptero-4...

---

### Post by taurus on 2009-01-20
The last digit of the entry for root filesystem, /dev/sda1, should be 1.  Here's the way I have on my machine.

```

/dev/sda1 UUID=89408c9a-51ad-40f9-a689-82c67b37549d / ext3 relatime,errors=remount-ro 0 1

```
I guess you need to boot from a LiveCD.  Then, open a terminal and mount your harddrive where / is.

Applications -> Accessories -> Terminal
```
sudo mount /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```
Now, modify the entry for /dev/sda1 to look like the one above.  Save it and close down gedit editing window.  Unmount the harddrive and reboot.

```
sudo umount /media/ubuntu
```

---

### Post by floatingpoint on 2009-01-20
My mistake. It was already 1.

Anyway, having rebooted from hdd I'm back to square (or post) one.

---

### Post by taurus on 2009-01-20
I am not sure whether it's a typo or not but the entry for root filesystem, /dev/sda1, has an empty space between errors=remount & -ro.  There should not be a space between them.

```

/dev/sda1 UUID=89408c9a-51ad-40f9-a689-82c67b37549d / ext3 relatime,**errors=remount-ro** 0 1

```

---

### Post by floatingpoint on 2009-01-20
There's no space.

I'm sorry, like I said, I'm having to run between two rooms with this stuff written down. So there are a few typos.

---

### Post by floatingpoint on 2009-01-20
Is it time to reinstall? I don't mind if all reasonable solutions have been explored...



edit: I reinstalled. Thanks for the help folks.

---

### Post by rbolio on 2009-01-22
I'm having the same problem in a computer..... what about going through all the (yes's and no's)??? 

how about going hardy or gutsy?,i mean its kinda of an old pc....

---

### Post by genjuroSE on 2009-01-23
I have the same problem.

I think it was caused when I was messing with the resolution in Ubuntu. I was trying out what 720p looked like and when I tried switching back to 1080p something went wrong. So I rebooted and I get to the same screen as these guys. Xserver doesn't start (I think)

I can only access read-only mode it seems.. Doesn't matter if I try to boot in recovery mode or not.
I can not rewrite or add any files. With or without sudo.


I can access the grub-menu:
> Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+

And I get the options to: 
press 'c' for command-line (to grub)
press 'e' to edit the commands before booting

Maybe someone knows how I can get to terminal from this menu? So I can try to restore my files..

Any help would be greatly appriciated!

taurus:
I did try to change the /dev/sda1.. No success though :(
Thank you for trying though!

---

