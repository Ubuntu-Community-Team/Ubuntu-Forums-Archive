---
title: "2 boot loaders?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Coopa on 2010-02-03
I installed 9.04 last night using Wubi as I'm having some separate issues with my hdd (due to partitioning, another story...)

I now have 2 bootloaders. One looks like a Windows one which gives Windows/Ubuntu and then when i pick Ubuntu i get the Grub loader.


A few questions,
1 - can i/should i disable one? ie. get it to primary boot to Ubuntu with just one click
2 - if i wanted to make this into a proper, dedicated partition how do i go about that?

---

### Post by garvinrick4 on 2010-02-03
> **Coopa said:**
> I installed 9.04 last night using Wubi as I'm having some separate issues with my hdd (due to partitioning, another story...)

I now have 2 bootloaders. One looks like a Windows one which gives Windows/Ubuntu and then when i pick Ubuntu i get the Grub loader.


A few questions,
1 - can i/should i disable one? ie. get it to primary boot to Ubuntu with just one click
2 - if i wanted to make this into a proper, dedicated partition how do i go about that?
So you have grub2 or grub legacy trying loading after you choose ubuntu? When you choose
Windows it boots into windows?
Wubi attaches itself to the grub4dos I think it is called. Anyway the Windows bootloader.
Need more info like version of Windows. After you pick ubuntu are you able to boot into Ubuntu
when you get the linux grub? Do you just want to make a partition and install Linux and remove the Wubi?

---

### Post by Coopa on 2010-02-03
> **garvinrick4 said:**
> So you have grub2 or grub legacy trying loading after you choose ubuntu? When you choose
Windows it boots into windows?
Wubi attaches itself to the grub4dos I think it is called. Anyway the Windows bootloader.
Need more info like version of Windows. After you pick ubuntu are you able to boot into Ubuntu
when you get the linux grub? Do you just want to make a partition and install Linux and remove the Wubi?

Thanks for the reply.

Ok, my boot sequence is:

Windows boot loader:
Windows XP Pro (default)
Ubuntu

If i pick Windows, it loads straight away

If i pick Ubuntu, it then loads Grub where i get a choice of Ubuntu, and a few recovery options. 

I only ask because i've tried dual-booting many times in the past (i've had issues with hardware) and i've never had 2 bootloaders. 

And yes, i would like to transfer my wubi install to a dedicated partition. Since posting i have properly read the Wubi Guide and found the annotated guide to doing this :)

---

### Post by corncob on 2010-02-03
> **Coopa said:**
> Thanks for the reply.

Ok, my boot sequence is:

Windows boot loader:
Windows XP Pro (default)
Ubuntu

If i pick Windows, it loads straight away

If i pick Ubuntu, it then loads Grub where i get a choice of Ubuntu, and a few recovery options. 

I only ask because i've tried dual-booting many times in the past (i've had issues with hardware) and i've never had 2 bootloaders. 

And yes, i would like to transfer my wubi install to a dedicated partition. Since posting i have properly read the Wubi Guide and found the annotated guide to doing this :)

I'm not familiar with Wubi but do have a thought on this.  I don't have the 9.04 GRUB any more so I can't check it out but it seems you can keep it from appearing on the screen and reduce the time it waits from 10 seconds to 0.  You can edit it by typing
```
gksudo gedit /boot/grub/menu.lst
```
into the Ubuntu terminal (Somebody correct me if I'm wrong.)  Actually, they tell me, you can't reduce the wait time to zero even if you set it so but it will go to one second or so -- a help.

---

### Post by garvinrick4 on 2010-02-03
I have had a Wubi install on a Vista machine that had this happen and I found two wubi entries
in bcd which is the Vista and 7 boot loader but I know nothing about editing XP boot manager.

It was chainloading when it did not need to. Need some help from someone who know XP.

It happens usually when you uninstall Wubi from add and remove programs in Windows instead of uninstall in Ubuntu Wubi folder in C:

I will tell you I learned on Wubi and it was great for that purpose. Once you just use the gparted software in Ubuntu install to partition you will get more enjoyment out of Linux.
gparted will just about do it on its own if you stay focused while in use. 

What kind of hardware do you have that you believe Linux will find difficult? Lots of people in
these forums that have been there done that, just use them and Google and you will be fine.

---

