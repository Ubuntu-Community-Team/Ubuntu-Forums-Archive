---
title: "Adding Windows 7 to Grub"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by studentofphysics on 2010-06-06
Hi I'm fairly new to ubuntu and linux in general (I just installed ubuntu on my hard drive today)

I've been able to successfully install it (can't get internet on it though, so I'm on windows typing this) But my problem that' I'm seeking help for is that on the grub bootloader, I only see options to boot ubuntu and some other memory checking thing. In order to get back on to windows I've had to insert my windows 7 installation DVD and use the command prompt to fix the boot. I then tried to restore the grub thing and ended up in the same place it was before.

So is there a way to add windows 7 to the grub bootloader?

I appreciate any help!

---

### Post by yetiman64 on 2010-06-06
In an ubuntu terminal try

```
sudo update-grub
```unless something worse is going on that should find and put an entry in the menu for win 7. Give it a try 1st and post back if it fails.

---

