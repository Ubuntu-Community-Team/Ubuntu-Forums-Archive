---
title: "status 256 - cant log in to ubuntu and XP will not boot"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by rubytru on 2010-08-12
In my over enthusiasm for Ubuntu, I partitioned my sisters XP and installed 10.4, and this is the message i got --
 (usr/lib/libgconf2-4/gxonf-sanity-check 2 exited with status 256.

I can't log her on to Ubuntu, and XP does not boot. 

Thank you for any guidance you can give me. 

ruby

---

### Post by ghettobird on 2010-08-12
GRUB and Windoze MBR are fighting a turf war. here's a link that may help.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by rubytru on 2010-08-12
The information on the link is on how to restore or recover the boot-loader after installing Windows. I installed Ubuntu onto XP ... so does the information still apply?

Thank You ghettobird.

---

### Post by ghettobird on 2010-08-12
I would guess so. The problem is stemming from the repartitioning of the drive to make room for Ubuntu. Unfortunately there is a warning during the initial install phase that some data may be lost due to the file compression that takes place during drive partitioning. Best thing to do is boot from live cd and try to recover GRUB.

---

### Post by rubytru on 2010-08-12
Thank You again for your very helpful reply. Will print the info and try to navigate it.  I haven't really worked with the terminal and this is an intense way to learn.

ruby

---

