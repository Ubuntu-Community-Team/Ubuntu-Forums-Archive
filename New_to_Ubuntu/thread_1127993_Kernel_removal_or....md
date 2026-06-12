---
title: "Kernel removal or..."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Orlsend on 2009-04-17
Hi I have Ubuntu with  the array kernel (For eeepc's) anyways I installed virtualbox and the it came with a kernel packaging module and to get my Virtualbox going it installed the default ubuntu kernel. Thankfully my older kernel is there its just not the default one. Is there anyway I could remove the generic kernel or make my eeepc kernel the default one?

---

### Post by kpkeerthi on 2009-04-17
Yes, you can.

See [http://ubuntuforums.org/showpost.php?p=7087659&postcount=2](http://ubuntuforums.org/showpost.php?p=7087659&postcount=2) Follow steps 1 through 4.

---

### Post by Orlsend on 2009-04-17
Thanks it just what I needed, I was in the rigth way... though I was searching with the wrong keywords. The "Linux-image" was the one I needed.

---

### Post by Orlsend on 2009-04-17
Hey I think the entry still on the grub, is there anyway to update my grub or remove the entry my self?

---

### Post by kpkeerthi on 2009-04-17
It should have updated your GRUB. I wonder why it didn't. May be the GRUB entries were added manually.

You can use [startup-manager]("http://www.downloadsquad.com/2008/10/10/ubuntu-tip-use-startup-manager-to-edit-your-boot-menu/") or edit /boot/grub/menu.lst manually to edit the boot entries.

---

### Post by Orlsend on 2009-04-17
Thanks! I forgot how **nifty** the startup manager was. I think I am done here.

---

