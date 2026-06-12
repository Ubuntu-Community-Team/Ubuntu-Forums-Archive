---
title: "2 start-up ubuntu options"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by Ronnicus on 2010-02-21
I recently installed ubuntu and everything was fine until I had to update it. Then, for some reason it starts giving me 2 startup options. They both work fine, but I'm not really sure why it's doing that. How do I get rid of one of them?

Btw, the options look like
Linux
Recovery
Linux (copy of 1st )
Recovery

---

### Post by tom.swartz07 on 2010-02-21
> **Ronnicus said:**
> I recently installed ubuntu and everything was fine until I had to update it. Then, for some reason it starts giving me 2 startup options. They both work fine, but I'm not really sure why it's doing that. How do I get rid of one of them?

Btw, the options look like
Linux
Recovery
Linux (copy of 1st )
Recovery

Theyre different kernels. Kernels are the underlying code to allow the OS to 'talk' to the hardware.

The general accepted rule is to keep at least 1 previous version of the kernel to fall back on, should something happen with the new version. 

If you REALLY REALLY dont want to see it in the list, you could remove it from Synaptic package manager. 

Write down the lowest number one (i.e. the last in the list) and then once youre booted up, search for linux-image in Synaptic. the version that you wrote down should be there, just uncheck it and apply.

---

### Post by mataug on 2010-02-21
> **Ronnicus said:**
> I recently installed ubuntu and everything was fine until I had to update it. Then, for some reason it starts giving me 2 startup options. They both work fine, but I'm not really sure why it's doing that. How do I get rid of one of them?

Btw, the options look like
Linux
Recovery
Linux (copy of 1st )
Recovery

Is it exactly the one as the older one ?
This usually happens with me when I update the kernel through the update manager and the menu.lst contains the older entry too.

You can read the menu.lst in /boot/grub/menu.lst

If you are using the newer grub(I think it is called grub2), I believe it will be /boot/grub/grub.cfg

---

### Post by byStanderone on 2010-02-21
...simply sudo update-grub after removing old kernels in synaptic, and the old grub configurations will update itself.

---

### Post by tom.swartz07 on 2010-02-22
> **byStanderone said:**
> ...simply sudo update-grub after removing old kernels in synaptic, and the old grub configurations will update itself.

When you remove them from synaptic, apt automatically updates grub for you.

Relevant on older systems, but not needed since 9.10
:D

---

