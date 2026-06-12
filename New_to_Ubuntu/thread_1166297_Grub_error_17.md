---
title: "Grub error 17"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by MadsRH on 2009-05-21
Hi
I get a Grub error 17 when booting. I'm dualbooting Ubuntu 8.10 and Vista.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000077fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1913       29644   222757290    7  HPFS/NTFS
/dev/sda2               1        1912    15358108+  83  Linux
/dev/sda3           29645       30401     6080602+  82  Linux swap / Solaris

```

I know there's a lot of threads on this topic, but I couldn't find any with the problem I have. I've booted into the live CD, but I don't know what to do now :-k
In one of the threads I read someone suggested reinstalling grub. It seemed a bit to techinal for me, but would that be my solution?

Thanks for reading my post and please write very non-geeky reply's ;)

---

### Post by lindsay7 on 2009-05-21
Try this 

in the terminal type.  Do not put in the quote marks

"sudo grub"

at the grub prompt, type

"find /boot/grub/stage2"

this will return something like (hd0,1)

still at the grub prompt type the results of what you get above
as such

"root (hdx,y)" where x and y are what you got in the above
"setup (hd0)"
"quit"

reboot

---

### Post by MadsRH on 2009-05-21
Fantastic!!! ):P

Grub has returned, although the entries doesn't work anymore. I will search the forum to find more answers.

Thanks for you fast reply **lindsay7** :D

(Sadly the 'Thank you' button is still deactivated)

---

### Post by Bodsda on 2009-05-21
> **MadsRH said:**
> Fantastic!!! ):P

Grub has returned, although the entries doesn't work anymore. I will search the forum to find more answers.

Thanks for you fast reply **lindsay7** :D

(Sadly the 'Thank you' button is still deactivated)

Can you paste the contents of /boot/grub/menu.lst so we can figure out whats wrong with the entry.

Also what error does it give (if any)

Regards,

Bodsda

---

### Post by MadsRH on 2009-05-21
Sorry for the slow reply.


I got it working ;)

Thanks **Bodsda** for taking the time to help out

---

