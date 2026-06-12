---
title: "Vista wants disk check after ubuntu install"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Unit225 on 2009-12-12
I dual-booted ubuntu 9.10 without incident, but when i went back to vista it asked to do a disk check. When it finished it just sat there, so the next time i booted i skipped it and vista works fine but it still asks me to the check every boot. How can I fix this?

---

### Post by nwadams on 2009-12-12
did you resize the vista partition during the install of ubuntu? If so that will explain why vista wants to check the file system, because it was changed. Let it check the file system again and wait a while, hopefully it doesn't hang this time.

---

### Post by sandyd on 2009-12-12
this is why you use vista to resize the partition, not ubuntu.
if the repair goes in a loop, use this
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

select repair when booting from it.

---

### Post by presence1960 on 2009-12-13
> **carlee said:**
> this is why you use vista to resize the partition, not ubuntu.
if the repair goes in a loop, use this
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

select repair when booting from it.

How to restore the Windows Vista or 7 bootloader

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download from the link Carlee gave.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
```
then
```
bootrec.exe /fixmbr
```

Now close the two windows and click "Restart."

---

### Post by lisati on 2009-12-13
> **Unit225 said:**
> I dual-booted ubuntu 9.10 without incident, but when i went back to vista it asked to do a disk check. When it finished it just sat there, so the next time i booted i skipped it and vista works fine but it still asks me to the check every boot. How can I fix this?

Windows wanting to do a chkdsk after installing Ubuntu is normal. If it runs to completion and you should be fine.

---

### Post by Unit225 on 2009-12-13
Thanks for all your help, but i've decided to move ubuntu to another machine that runs xp. Will this happen again on that machine.

---

