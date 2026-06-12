---
title: "Recommendations for a Virtual Machine?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-26
i have a dual boot set up with ubuntu/xp. (pentium 4, 2.5GB RAM, 1TB HDD, 128MB Nvidia Quadro NVS)  i have few apps i need in XP, but i would like to avoid booting in xp as much as possible, so i am trying to decide on a VM.

i'm leaning towards installing sun's virtualBox over the virtualBox-OSE. 

are there other good VMs that i should consider?

thanks for any recommendations.

---

### Post by MrWES on 2009-02-26
> **nachos99 said:**
> i have a dual boot set up with ubuntu/xp. (pentium 4, 2.5GB RAM, 1TB HDD, 128MB Nvidia Quadro NVS)  i have few apps i need in XP, but i would like to avoid booting in xp as much as possible, so i am trying to decide on a VM.

i'm leaning towards installing sun's virtualBox over the virtualBox-OSE. 

are there other good VMs that i should consider?

thanks for any recommendations.

I believe only Virtualbox-OSE has USB support. Maybe it's the other way around. The OSE lack USB support -- sorry for the confusion.


Bill

---

### Post by Demiurgo_linux on 2009-02-26
I Think that virtualbox is the best for OS virtualization...

Remember to set a dynamic Hd Site to avoid problem in space ;)

---

### Post by scouser73 on 2009-02-26
> **nachos99 said:**
> i have a dual boot set up with ubuntu/xp. (pentium 4, 2.5GB RAM, 1TB HDD, 128MB Nvidia Quadro NVS)  i have few apps i need in XP, but i would like to avoid booting in xp as much as possible, so i am trying to decide on a VM.

i'm leaning towards installing sun's virtualBox over the virtualBox-OSE. 

are there other good VMs that i should consider?

thanks for any recommendations.

Try this tutorial; [http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/]("http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/")

---

### Post by jespdj on 2009-02-26
One feature that VirtualBox misses is that it doesn't support multi-core processors inside the virtual machines. So if you have a dual- or quad-core processor, then a guest OS will only be able to use one of your cores. Support for multi-core has been promised for a future version.

---

