---
title: "No log-in box at splash screen after update"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by OisinT on 2010-02-01
I was attempting to upgrade ktorrent, after I had been having some trouble with an older version.  I had to install some other dependencies and the computer wanted to restart, so I let it.

As it restarted it went to a weird screen I hadn't seen before which said:

GNU GRUB version 1.97~beta4

Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)


If I choose any of the ones that don't say recovery mode it gets to the splash screen, and the Ubuntu loading bar starts.  Before the bar is finished I hear the sound and the bar keeps loading.
Then, the logo goes away and where there usually is the box to choose my user name, there is nothing.
So obviously now I can't figure out how to log in as I cannot click on my user name and enter my password.

There is an option to edit the command line which reads:
```
recordfail=1
if [ -n ${have_grubenv}  ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set a13d24e7-6456-4341-87e9-ad6c793c7\030
linux /boot/vmlinuz-2.6.31.17-generic root=UUID=a13d24e7-6456-4341-8\7e9-ad6c793c7030 ro  quiet splash initrd /boot/initrd.img-2.6.31-17-generic

```

I'm really wishing not to have to reinstall and lose everything on my main drive.  I usually back it up onto my secondary drive, but I hadn't had the chance to yet.

Any and all help is greatly appreciated.

---

### Post by OisinT on 2010-02-02
bump - any help?  Is there even any way to log into the system from the command line?

---

### Post by OisinT on 2010-02-03
I just reformatted :(  You can lock this thread

---

