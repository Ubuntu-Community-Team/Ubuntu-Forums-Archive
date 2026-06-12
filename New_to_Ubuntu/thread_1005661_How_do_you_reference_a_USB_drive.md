---
title: "How do you reference a USB drive?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Asteroid Al on 2008-12-08
Long-time Unix user, brand new Linux/Ubuntu user ...

I just started using Ubuntu 8.10 (installed by Wubi). When I mount a USB drive, I immediately get a desk-top icon showing me the drive. With this icon I can see the contents with no difficulty.

_However_ I'd really like to be able to directly reference the contents of this drive. I know I'm supposed to do a 
**sudo tail -n 20 /var/log/kern.log** to give me the name of the drive; for example
[INDENT]*Dec  8 14:18:23 ubuntu kernel: [10784.605582]  sdf: sdf1[/INDENT]*
What I'd like to know is: how do I reference the contents of this drive? When I try to do **ls -l /sdf1** I get
[INDENT]*ls: cannot access /sdf1: No such file or directory[/INDENT]*
Thank you in advance for any help you might be able to provide.

---

### Post by Songwind on 2008-12-08
Usually, Ubuntu will create a mount point in /media with the name of the USB drive.

For example, my Kingston USB drive become /media/Kingston.  My Amazon Kindle becomes /media/Kindle.

So, looking in /media should get you the info you need.

---

### Post by newbee70 on 2008-12-08
> **Asteroid Al said:**
> Long-time Unix user, brand new Linux/Ubuntu user ...

I just started using Ubuntu 8.10 (installed by Wubi). When I mount a USB drive, I immediately get a desk-top icon showing me the drive. With this icon I can see the contents with no difficulty.

_However_ I'd really like to be able to directly reference the contents of this drive. I know I'm supposed to do a 
**sudo tail -n 20 /var/log/kern.log** to give me the name of the drive; for example
[INDENT]*Dec  8 14:18:23 ubuntu kernel: [10784.605582]  sdf: sdf1[/INDENT]*
What I'd like to know is: how do I reference the contents of this drive? When I try to do **ls -l /sdf1** I get
[INDENT]*ls: cannot access /sdf1: No such file or directory[/INDENT]*
Thank you in advance for any help you might be able to provide.


make sure you have your drive plugged in and turned on.

enter this in terminal

mount

this will list your mount points

/dev/sdc1 on /media/E type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

the on tells you your mount point  mine is **/media/E**

use that to cd into your removable.

---

### Post by Asteroid Al on 2008-12-08
> **Songwind said:**
> My Amazon Kindle becomes /media/Kindle.

Thank you, thank you, thank you! You wouldn't believe the places I've searched without being able to find this out!

---

### Post by Asteroid Al on 2008-12-08
> **newbee70 said:**
> the on tells you your mount point  mine is **/media/E**

Many thanks!

---

### Post by Songwind on 2008-12-08
Glad to help!

If you run into similar issues in the future, you might notice that when you double click that desktop icon, it will show you the path to the folder you are in above the contents.  It's called "breadcrumbs" but each button amounts to a directory name.

---

