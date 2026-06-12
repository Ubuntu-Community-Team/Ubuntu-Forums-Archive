---
title: "Dual booting Windows and Ubuntu"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by sideffects on 2009-11-06
Okay, I have Ubuntu installed on a 320 GB HDD. Then, I decided I still need Windows sometimes, so I booted from the Live CD and used GParted to create a new NTFS partition on the 320 GB HDD for Windows. Then I booted up using the Windows DVD and I try to tell it to install on the Windows partition that I made (Yes, it is in the list.) But, it tells me that it can't find what it needs to be able to install there. Is this a problem that is caused by my previous installation of Ubuntu, or what? And...is there a fix?

NOTE: I'm not sure this is even caused by Ubuntu, in which case...this probably shouldn't be in this forum.

---

### Post by ranch hand on 2009-11-06
Are you trying to install MS on an extended partition?

That will not work.

MS is kind of cranky about being anywhere but on the first Primary partition.

---

### Post by Fire_Chief on 2009-11-06
Windows generally does not like to be fresh installed into an already formatted partition. Also, be sure it's a primary partition and not a logical one. Be warned though, installing Windows ***after*** Ubuntu is already installed will overwrite the MBR and the computer will boot Windows only. You'll have to use the Ubuntu LiveCD to reinstall Grub and then add the Windows option in the boot menu.

A better option may be to create a virtual machine (a la VirtualBox) and install XP inside there. That would keep you from having to dual boot as well.

Cheers!

---

### Post by sideffects on 2009-11-06
> **ranch hand said:**
> Are you trying to install MS on an extended partition?

That will not work.

MS is kind of cranky about being anywhere but on the first Primary partition.
I hate MS! Thanks for the info though, guess I'll have to start from scratch.

---

### Post by CJ Master on 2009-11-06
I would recommend you to install Windows, and then you can install Ubuntu on a separate partition. Be sure to backup all your files before you do so!

---

### Post by sideffects on 2009-11-06
> **Fire_Chief said:**
> Windows generally does not like to be fresh installed into an already formatted partition. Also, be sure it's a primary partition and not a logical one. Be warned though, installing Windows ***after*** Ubuntu is already installed will overwrite the MBR and the computer will boot Windows only. You'll have to use the Ubuntu LiveCD to reinstall Grub and then add the Windows option in the boot menu.

A better option may be to create a virtual machine (a la VirtualBox) and install XP inside there. That would keep you from having to dual boot as well.

Cheers!

It says it's a Primary partition on the Windows boot CD. But I try to select it and it says, "Windows can not find a [hard drive] that meets it's minimum installation requirement." But I do have the option to load a Driver...not sure if that would help.

Do you think I'd have better luck starting from scratch?

---

### Post by sideffects on 2009-11-06
> **CJ Master said:**
> I would recommend you to install Windows, and then you can install Ubuntu on a separate partition. Be sure to backup all your files before you do so!

Is there a way I can backup my entire Ubuntu Installation, so I can restore it once I have Ubuntu reinstalled?

---

### Post by CJ Master on 2009-11-06
> **sideffects said:**
> Is there a way I can backup my entire Ubuntu Installation, so I can restore it once I have Ubuntu reinstalled?

I no longer use Ubuntu, so I can't tell you any specific programs, but I'm sure you could find one after doing a little searching in Add/Remove or Synaptic.

---

### Post by ranch hand on 2009-11-06
The VB idea is a great one.  I have tried VB for testing other Linux distros and do not really like it.

For an MS product it would be ideal as it will isolate that security hole in a safe environment.

VB is in the repo and does work well and is pretty easy to set up.

That way you could expand your Ubuntu partition to the whole drive or reformat the partiton you made fo MS as a backup container.  Ar dual boot with another real OS.

---

### Post by CJ Master on 2009-11-06
If you do decide to go the VB rout here's a guide on how to get started with VB: [http://klikit.pbworks.com/How+to+install+Windows+in+VirtualBox](http://klikit.pbworks.com/How+to+install+Windows+in+VirtualBox)

---

### Post by Jimmynemo2 on 2009-11-06
Not nessasarily- Vista and Win7's boot manager will see ubuntu and add them to the windows bootloader- letting you dual boot windows and ubuntu just fine. Sure, grub will be gone, but grub isnt ubuntu. 

> **Fire_Chief said:**
> Windows generally does not like to be fresh installed into an already formatted partition. Also, be sure it's a primary partition and not a logical one. Be warned though, installing Windows ***after*** Ubuntu is already installed will overwrite the MBR and the computer will boot Windows only. You'll have to use the Ubuntu LiveCD to reinstall Grub and then add the Windows option in the boot menu.

A better option may be to create a virtual machine (a la VirtualBox) and install XP inside there. That would keep you from having to dual boot as well.

Cheers!

---

