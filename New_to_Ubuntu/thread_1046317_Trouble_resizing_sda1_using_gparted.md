---
title: "Trouble resizing sda1 using gparted"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Jeconti on 2009-01-21
I'm running 8.10 on a Dell Mini 9 with the 8 gig SSD. I split up the drive so that half was partitioned to / and the other half went to /home.  I'm seeing now just how little I actually save on a netbook, so I want to change it up.

I set up a Live USB disk also running 8.10 and resized the /home partition to 1.5 using gparted. That went fine, but now it won't let me resize the / partition to fill up the unallocated space.

[IMG]http://i39.tinypic.com/fk5cw3.png[/IMG]

Suggestions?
Thanks in advance.

---

### Post by drs305 on 2009-01-21
You can't take the space directly from the extended partition (light blue border) and put it into sda1. First you will have to shrink the extended partition (sda2) and with the free space displaying *outside* the blue borders you will be able to expand sda1. As you mention, you have to do this outside of ubuntu with a LiveCD, LiveUSB, gparted CD, etc since sda1 must be unmounted to change it.

---

### Post by vanadium on 2009-01-21
This will be somewhat more complicated than that. You will need to delete your swap space and (eventually) recreate it afterwards. This will involve editing /etc/fstab.

---

