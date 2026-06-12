---
title: "Trouble booting: AppArmor permission denied."
date: 2010-03-04
forum: New to Ubuntu
---

### Post by archron on 2010-03-04
I have trouble booting Ubuntu. When I boot it, the white Ubuntu logo shows up, then after a few screen flashes, this text shows up:

chroot: cannot execute /etc/apparmor/initramfs/: Permission denied.

And then, it's stuck there. :confused:

Please help. Thank you.

---

### Post by spiderbatdad on 2010-03-04
did you do anything to cause this error...install SElinux, or anything else you can think of before it started happening?

---

### Post by spiderbatdad on 2010-03-04
i would start by running :
```
sudo apt-get update && sudo apt-get upgrade
```
Then install:
```
sudo apt-get install apparmor-profiles
```
Check the status of apparmor:
```
sudo apparmor_status
```

---

### Post by archron on 2010-03-04
I was having trouble starting Synaptic Package Manager then and I typed

chroot -r 0440 /etc

as a solution from one of the forums I found.

---

### Post by kanikilu on 2010-03-04
> **archron said:**
> chroot -r 0440 /etc

Are you sure? That doesn't even look like a valid command (although admittedly I don't often need to use chroot).

Can you point us to the post you followed?

You didn't **chmod** did you? I will fully admit that I'm by no means an expert, but I do know using "chmod -R" on a system directory like that, epecially /etc, is bad news and anyone who recommends it to "fix" a problem probably doesn't know what they are talking about...

---

### Post by lykwydchykyn on 2010-03-04
> **kanikilu said:**
> 
You didn't **chmod** did you? I will fully admit that I'm by no means an expert, but I do know using "chmod -R" on a system directory like that, epecially /etc, is bad news and anyone who recommends it to "fix" a problem probably doesn't know what they are talking about...

I'm guessing that's what happened, because that would produce the error shown.  

Recursively altering permissions on system folders is always a BAD idea.  Lesson learned.

This might be fixable, though, by the following method.

 - Boot to liveCD
 - Mount your / partition
 - Open a terminal and cd to where you mounted the partition.
 - execute "chmod -R 755 etc"

Most things in /etc have default permissions of 755, though a few things might have special permissions that might be messed up (in particular, I know there are some services that only work if their configs are properly secured, but offhand I can't remember what they are).

---

### Post by kanikilu on 2010-03-04
I've attached the output of ```
ls -la /etc
``` from my system which is a recently clean-installed version of 9.10. That might get you started in fixing the permissions, though doing them all by hand would be a PITA to be sure...

---

### Post by hardtke on 2010-05-07
I've had this error intermittently for a year.  It almost makes me want to get a mac.  I often need to reboot several times before Ubuntu boots cleanly.

This error is very common, but I've never found the simple solution.

---

### Post by lykwydchykyn on 2010-05-07
Which error?  Did you do the same chmod thing the OP did?

---

