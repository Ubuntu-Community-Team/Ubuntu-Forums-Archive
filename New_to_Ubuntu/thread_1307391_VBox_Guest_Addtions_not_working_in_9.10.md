---
title: "VBox Guest Addtions not working in 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by longtom on 2009-10-31
Hi,

the guest additions for VirtualBox do not seem to work in Ubuntu 9.10.  I saw when I googled, that I am not the only one having this problem.

Has anybody managed to find a work around yet?

Any suggestions welcome.

---

### Post by longtom on 2009-10-31
Got it going.  For the googlers:

I downloaded the newest  VB GuestAdditions iso (in my case 3.08).  That can be hard to find.  I finally got it here:

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

Go to settings for your Virtual Machine and choose CD/DVD-ROM.
Check "Mount CD/DVD Drive"
Check "Enable Passthrough"
Choose the iso file you just downloaded.

Fire up Karmic (or whatever Ubuntu you have in your Virtual Setup).

Than, in the terminal I do this:

```

$ cd /media/cdrom
$ sudo sh VBoxLinuxAdditions-x86.run

```

Restart your virtual machine - done.

Good luck.

---

### Post by matthew on 2009-11-11
That was very helpful. Thank you.

---

### Post by longtom on 2009-11-11
> **matthew said:**
> That was very helpful. Thank you.

You are welcome!:)

---

### Post by engeslsmann on 2010-02-05
> **longtom said:**
>   That can be hard to find.  I finally got it here:

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

Indeed! Thank you for the link!

---

