---
title: "Boot failing after new install-missing modules"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by GCDB on 2008-12-22
Hi,
Decided to wipe windows once and for all.
I had ubuntu version 6.06 which worked. Ubuntu 8.10 works from cd, but has given me problems on install.
Boot fails with
Gave up waiting for root devices
Boot args (cat /proc/modules; ls /dev)
Alert /dev/disk/by-uuid/c47.........does not exist
dropping to shell

(initramfs)

initially i think i had two problems as my realtek 8139 nic was loading driver cp instead of too. i eventually fixed this by blacklisting the cp and also rmmod -v 8139cp and update-initramfs -v

now i am just left with the above output.
I have found similar errors but i am running out of ideas.
Anyone got a systematic approach(simple) to help me?
Just before the errors above it indicates its booting from hd0,0 and also the menu.lst says boot from this partition.
Any help please
Gavin

---

### Post by IamReck on 2008-12-22
Could you more clearly state your problem and the error messages you are getting?

Thanks.

---

### Post by GCDB on 2008-12-22
Ive done too many changes and will re-install again and then post messages as wont boot at all now for some reason.
Sorry will re-post back with original error messages.
Thanks Gav

---

### Post by GCDB on 2008-12-23
Hi,
I have re-installed Ubuntu 8.10
On booting up, after grub loader, boots from (hd0,0) then Ubuntu screen comes up then a blank screen and drops to shell and busybox.
Messages are:

Boot from (hd0,0) ext 3  612c6d7e-82ee-4cd7-a505-206d7a585b28
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/612c6d7e-82ee-4cd7-a505-206d7a585b28 does not exist. Dropping to a shell!

Busybox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter 'help' for a list of commands

(initramfs)
If i type exit now it loads up ok
If i type cat /proc/modules it shows a lot of items(Dont say you need this please) and also if i type ls /dev it shows a load of items as well.
What can i try next?
Many thanks
Gavin

---

### Post by GCDB on 2008-12-23
Please any help?

---

### Post by markbuntu on 2008-12-23
It looks like the uuid is wrong.

---

### Post by bruce leroy on 2009-10-01
I have this same problem.  What is UUID?  How do I fix this?

---

### Post by aljoriz on 2009-10-01
what is the system specifications?  

Try using ubuntu 8.0 LTS.  My friend pc has a hard time installing jaunty and 8.10 but 8.04 worked like a charm.

---

### Post by LewRockwell on 2009-10-01
> **bruce leroy said:**
> I have this same problem.  What is UUID?  How do I fix this?

please start a NEW thread for a new trouble-call

mixing multiple trouble-calls in one thread is a recipe for DISASTER!

.

---

