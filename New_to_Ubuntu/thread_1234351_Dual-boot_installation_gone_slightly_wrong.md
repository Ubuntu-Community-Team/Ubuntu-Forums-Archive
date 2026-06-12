---
title: "Dual-boot installation gone slightly wrong?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by germanix on 2009-08-07
I build a new pc with 2x HDD. On the first drive I installed windows xp professional 64 bit and on the second drive Linux 9.04. 64 bit version.  Both OS runs well. The problem is that when the computer boots it does not give me the choice to chose between windows and linux by name, instead it shows a whole list of HDD`s with like serial numbers behind it. I figured out that by choosing the first HDD on the list it starts windows and choosing the second last HDD on the list boots linux. I have had dual boot systems before and it always showed windows and linux by name at the boot. I dont know why it does not happen here and how to change/fix it. Any ideas?

---

### Post by synapsys on 2009-08-07
You need to use a boot loader. You can use either windows or ubuntu's boot loader. I suggest using ubuntu's bootloader 'grub' (because it's better.) Just pop in a ubuntu live cd and install grub to the primary hard drive. Here's a tutorial.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by germanix on 2009-08-07
Thank you very much synapsys. This was exactly what I was looking for. I wish you well.

---

