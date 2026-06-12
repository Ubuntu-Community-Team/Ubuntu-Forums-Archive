---
title: "How to mount a NTFS partition from terminal."
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Jetso on 2010-11-20
This is all part of me trying to learn more about Linux and the terminal. I want to be able to mount my NTFS Windows (sda3) drive from terminal. I keep alot of my data on there to save room on my file system since it's small. I saw that it should be ```
sudo mount /dev/sda3/ /media/OS
``` but that doesn't work. Any help?

---

### Post by Verbeck on 2010-11-20
[s]there shouldn't be a trailing / in /dev/sda3  i think..[/s]
edit: worked with the / for me

if that fails
sudo mount -t ntfs /dev/sda3 /media/OS

---

### Post by northern lights on 2010-11-20
```
sudo mount /dev/sda3 /media/OS
```
is theoretically correct syntax, leave the /.
It would have been helpful had you also posted the error it results in.

Does the folder /media/OS exist in the first place? If not, run```
sudo mkdir /media/OS && sudo mount /dev/sda3 /media/OS
```(required once only)

Should the folder exist and the problem be rooted elsewhere,
are you certain its sda3?
Please post the output of```
sudo fdisk -l
```(lower case L)

---

### Post by Jetso on 2010-11-20
Error: ```
fuse: failed to access mountpoint /media/OS: No such file or directory
``` Even when I take out the last / in dev/sda3 . Maybe I'm confused, but the actual drive's name is OS. In Computer it calls it "160 GB Hard Disc: OS" There is no folder.

---

### Post by Verbeck on 2010-11-20
first make the mount point
```

sudo mkdir /media/OS
sudo chown -R yourusername:usergroup /media/OS
sudo mount /dev/sda3 /media/OS

```

---

### Post by northern lights on 2010-11-20
> **northern lights said:**
> ```
Does the folder /media/OS exist in the first place? If not, run[CODE]sudo mkdir /media/OS && sudo mount /dev/sda3 /media/OS
```(required once only)

That's exactly what the problem lies in now.

Create the folder, either by the quoted command or manually in nautilus.

---

### Post by Jetso on 2010-11-20
Aha! That worked! Thank you very much.

---

