---
title: "mint4win to install linux mint alongside already existent full Ubuntu install?"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by chick_turk on 2011-05-24
So I have a Windows 7 computer dual booting Ubuntu 11.04. That install has also replaced my default Windows boot loader with grub:(. That being said, it seems that when you use wubi or mint4win to install linux, you need to use the Windows boot loader to go into the wubi/mint4win install's built in grub loader. Is that truly the case, or will my main grub be able to see the mint4win install?  So basically, would it hurt my Ubuntu install to install linux mint through mint4win. I know that it installs within Windows, but I knew it wouldn't hurt to be sure.

---

### Post by Megaptera on 2011-05-25
some time ago I had a dual boot Ubuntu/Vista & within Vista I installed Mint using Mint4Win. (I've no idea why I did that! Probably made sense at the time!!)
I can't remember the version numbers, but at first boot when switching the laptop on, I got to choose between Ubuntu & Windows.
If I chose Windows I got a second grub menu that gave me a choice between Windows and Mint. Choosing Windows here took me to Vista.

---

### Post by bcbc on 2011-05-25
Wubi boots via the Windows boot manager, not the Windows bootloader. So yes it's possible to install mint4win.

Grub from your 11.04 will not pick up mint4win (or wubi for that matter). But you can add a custom entry to boot it directly if you wish.

Note that wubi uses grub4dos and it hangs up on ext4 partitions, so if you have a dual boot with linux on /dev/sda1 (with ext4) and windows on /dev/sda2 - it won't work. That's about the only problem you might have.

---

### Post by chick_turk on 2011-05-25
> **Megaptera said:**
> some time ago I had a dual boot Ubuntu/Vista & within Vista I installed Mint using Mint4Win. (I've no idea why I did that! Probably made sense at the time!!)
I can't remember the version numbers, but at first boot when switching the laptop on, I got to choose between Ubuntu & Windows.
If I chose Windows I got a second grub menu that gave me a choice between Windows and Mint. Choosing Windows here took me to Vista.

So I'm confused. If I choose Windows 7 from grub on startup, it will give me the windows boot manager, where I could then select my Mint install? If it ends up too confusing, I may just not even try for my computer's sake.

---

