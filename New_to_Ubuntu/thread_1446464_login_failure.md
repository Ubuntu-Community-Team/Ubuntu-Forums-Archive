---
title: "login failure"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by antonio_ing on 2010-04-04
Hi guys

I got a problem since yesterday. I was working with my laptop with ubuntu 9.10 until it shutted down. When I Reboot then whatever linux version i choose at the grub list it starts to load the linux, starts the check of the filesystem and at 4% it stops and goes to an error in mounting the file system and i got just the prompt with root. I have been able to go through my files with the prompt and the live cd, but this problem remains.Every time i try to mount an external disk automatically, it says it is a read-only file system. Is there a solution to fix my laptop?

thanks in advance

---

### Post by laidback on 2010-04-04
The only thing that comes to mind is to check the BIOS settings to ensure that you have boot from external drive enabled as first hdd. (perhaps it got overwritten)

or

Check with Gparted via your Live CD that the boot flag on the drive you want to boot from is still set to boot (ticked). I had a problem the opposite way around where it wouldn't stop trying to boot from an external drive despite the fact that I'd wiped the OS from it. I had to remove the boot flag with Gparted, you want it the other way around.

Hope you have some success.

---

### Post by antonio_ing on 2010-04-04
well, actually the first boot is on the actual hard disk since from the grub i can choose windows XP and it works perfectly (but only windows)

---

### Post by ibuclaw on 2010-04-04
What filesystem is the Linux root?

Chances am the automatic filesystem check failed, and you are required to run a manual one.

Regards

---

### Post by antonio_ing on 2010-04-04
thanks very much. fsck solved the problem by checng MANUALLY the disk in few minutes

thanks again and good easter

---

### Post by ibuclaw on 2010-04-04
No probs, have a good easter too. :)

---

