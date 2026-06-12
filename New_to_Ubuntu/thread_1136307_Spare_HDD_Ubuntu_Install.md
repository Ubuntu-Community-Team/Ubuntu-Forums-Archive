---
title: "Spare HDD Ubuntu Install"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by RandomP on 2009-04-24
I installed Ubuntu on a spare drive that is in my PC while my primary drive was not connected. Now after I have connected my primary drive which has Windows XP, it does not give me the option to boot Ubuntu. 
I have a few fairly simple questions:
1. Is there any way to make Ubuntu start while my Primary drive is connected?
2. If I delete Ubuntu from my spare drive and reinstall it when my primary drive is connected via live CD and be able to switch between os'?

Thanks!

---

### Post by nandemonai on 2009-04-24
You've installed the boot loader to the secondary drive. Either boot from the second drive in BIOS or reinstall GRUB to the MBR of the first drive.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by RandomP on 2009-04-24
How about if I delete ubuntu from the spare drive and reinstall it on the spare drive though this time having the primary drive be connected? Would I still need to go through that process?

---

### Post by nandemonai on 2009-04-24
> **RandomP said:**
> How about if I delete ubuntu from the spare drive and reinstall it on the spare drive though this time having the primary drive be connected? Would I still need to go through that process?

Nopes, it should detect it and put the boot loader on your primary drive.

That said it's not really necessary to reinstall but that's up to you ;)

---

### Post by RandomP on 2009-04-25
> **nandemonai said:**
> Nopes, it should detect it and put the boot loader on your primary drive.

That said it's not really necessary to reinstall but that's up to you ;)

Thanks, I think I will reinstall though since I am a total noob at all that computer tech. There is no data on there right now anyway. :P

---

