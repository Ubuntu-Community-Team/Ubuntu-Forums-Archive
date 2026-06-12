---
title: "Mounting NTFS partition errors"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Pas_sa on 2011-06-06
Trying to mount my NTFS hard drive, it fails with this error:

```
andrew@andrewpc:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
```

This is the contents of my fstab:

```
/etc/sda1	/media/Windows HD	ntfs-3g	users	0	0
```

Help please! :)

---

### Post by drs305 on 2011-06-06
> [COLOR="Red"]/etc[/COLOR]/sda1 /media/[COLOR="Red"]Windows HD[/COLOR]
Should be
> /dev/sda1 /media/Windows\ HD
Note how you designate a space in linux...
However, you may also want to consider using UUIDs and expand the options to more than 'users'.

Here is a good link on fstab settings:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by lmarmisa on 2011-06-06
> **Pas_sa said:**
> Trying to mount my NTFS hard drive, it fails with this error:

```
andrew@andrewpc:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
```

This is the contents of my fstab:

```
/etc/sda1	/media/Windows HD	ntfs-3g	users	0	0
```

Help please! :)

There is a problem with the blank character of the label 'Windows HD'.

You have two options:

1) Rename the directory to WindowsHD (no blank character).

2) Escape the blank character using \040:

```

/etc/sda1	/media/Windows\040HD	ntfs-3g	users	0	0

```

---

### Post by Pas_sa on 2011-06-06
Thanks for the help - unfortunately I still get the error even with your change :( any other ideas?

I've tried with UUID but get the same error.

---

### Post by drs305 on 2011-06-06
> **Pas_sa said:**
> Thanks for the help - unfortunately I still get the error even with your change :( any other ideas?

I've tried with UUID but get the same error.

Did you try lmarmisa's entry for the space. He is correct on how to enter the space in an fstab entry (I dropped the '040'). So you should be using *my* "/dev/sda1" but *his* 'Windows\040HD'

> /dev/sda1	/media/Windows\040HD	ntfs-3g	users	0	0

Added: If you didn't know, you can test your fstab entries by running "sudo mount -a" . If you get no error messages, everything in fstab is correct.

---

### Post by lmarmisa on 2011-06-06
Type this command in order to verify that the package ntfs-3g is installed:

```

sudo apt-get install ntfs-3g

```

Change the line to something similar to this (I have selected here the option of deleting the blank char of the mount point):

```

/etc/sda1 /media/WindowsHD ntfs-3g defaults,uid=1000,gid=1000 0 0

```

If you wish to use the UUID, type this command:

```

sudo blkid

```

The line would be similar to this (change UUID according the result of the previous command blkid):

```

UUID=0E18C84318C82C11 /media/WindowsHD ntfs-3g	defaults,uid=1000,gid=1000 0 0

```

An additional comment: I recommend to add this line at the end of the file /etc/fstab. I see that, in your case, this is the first line. So, consider to move it to the last line.

---

### Post by Pas_sa on 2011-06-06
You are all gentlemen and/or scholars. That fixed it nicely. Thankyou!

---

