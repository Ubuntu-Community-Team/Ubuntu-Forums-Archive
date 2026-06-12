---
title: "Uninstalling Ubuntu using Wubi"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by nightskii on 2011-03-03
Could I have some help here?:popcorn:

I used Wubi 10.10 to attempt to install Ubuntu on my Windows 7 laptop. When I rebooted and booted Ubuntu, I had a kernel panic. 

Thankfully, everything on Windows still works.

I have no intentions of touching Ubuntu again just in case. If I do, it will be when I have sufficient experience.

Will it now be safe to uninstall Ubuntu using Wubi/Add or Remove Programs? Which is better to use?

---

### Post by garvinrick4 on 2011-03-03
In C: drive in Ubuntu folder right next to Users. Open the Ubuntu folder choose uninstall
and that is it. Add and remove programs will sometime leave the wubildr as entry in boot files but not always. Better to use uninstall in Ubuntu folder using WUBI install. One mans opinion.

P.S. You are missing a fine experience by not looking into Ubuntu Linux.

---

### Post by nightskii on 2011-03-03
Thanks for the advice.

Believe me, I know I'm missing out on an amazing experience. I'm just too much of a technophobe to try to install it.

---

### Post by nightskii on 2011-03-05
Sorry, I completely forgot to say: I installed Ubuntu using Wubi. I heard of this guy on these forums who couldn't boot windows after uninstalling Ubuntu. It was something to do with the GRUB bootloader. Will Wubi uninstall Ubuntu with no problems? Will I be able to boot into Windows? My laptop came with Win7 built in so if I do mess my laptop up, I can't use an installation disc because I haven't got one.
:lolflag:

---

### Post by maqtanim on 2011-03-05
> **nightskii said:**
>  Will Wubi uninstall Ubuntu with no problems? Will I be able to boot into Windows? My laptop came with Win7 built in so if I do mess my laptop up, I can't use an installation disc because I haven't got one.

  Yes... it should be a painless process. Wubi is not a complete Ubuntu installation. It installs ubuntu just like a general software in windows, like Firefox or VLC. When you remove Ubuntu (installed with wubi), it actually removes a software of Windows. So you not to be worried! :)

---

### Post by nightskii on 2011-03-05
Thank you all so much for your help! It took about two seconds to uninstall painlessly.

Just one more thing: it says on my system properties in Win7 that my system type is 32 bit. When I installed ubuntu I made a shortcut and put in the argument --32bit

Do you reckon this is why I couldn't install? When I tried without the argument, it looked something like 'ubuntu-10.1064bit.iso' or something with 64/64bit in it.

---

### Post by nightskii on 2011-03-05
Also, I want to see where is grub supposed to be? If it's not on my system, I can have piece of mind to know I can just boot without a grub error message.

---

### Post by nightskii on 2011-03-05
Forget about the grub question, I've just booted.

---

### Post by Mark Phelps on 2011-03-05
> **nightskii said:**
> My laptop came with Win7 built in so if I do mess my laptop up, I can't use an installation disc because I haven't got one.:lolflag:

Then, do yourself a favor ...

Use the Win7 backup feature to create and burn a Win7 Reapair CD.

This won't reinstall Win7, but if you decide to take the plunge later and experiment with Linux, it will give you the ability to restore your original MBR and to do any needed Win7 boot loader repairs.

Much better than suddenly having a PC that won't boot -- and no tools around to fix that.

---

### Post by bcbc on 2011-03-05
> **nightskii said:**
> Thank you all so much for your help! It took about two seconds to uninstall painlessly.

Just one more thing: it says on my system properties in Win7 that my system type is 32 bit. When I installed ubuntu I made a shortcut and put in the argument --32bit

Do you reckon this is why I couldn't install? When I tried without the argument, it looked something like 'ubuntu-10.1064bit.iso' or something with 64/64bit in it.

No you can use 32 bit Ubuntu if you want. If wubi defaulted to 64 bit then it must have detected that your processor is 64-bit capable (many 64-bit computers are shipped with 32-bit windows). Either should work.

Not sure why you'd get kernel panic on the first reboot though. If you want to use wubi, you should run chkdsk and defrag (if nec) beforehand.

---

### Post by nightskii on 2011-03-06
Thanks. I have no idea if my laptop is 64bit capable or not. I've only got 3gb of ram and plus my processor is 2.2ghz single core. Not the best of computers.

---

