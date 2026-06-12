---
title: "External HD error"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-10-18
Im trying to open my external HD and i got an error message... 

see the attachment!


thanks in advance!

---

### Post by TekMuzik on 2009-10-19
It's pretty well spelled out in the error message. Basically it's saying some other program marked the hard drive as in use, and Ubuntu does not want to mount a volume that is already in use somewhere else. It's usually cause by an improper shoutdown of Windows. If you do a dual boot with windows, then boot in to windows, and do a clean shutdown. That should release the hard drive to be used. If you don't do use any other OS on this system, you would want to try a force mount using the command given to you in the error message (although if you have important information on the external hard drive, you want to be careful with force mounting).

---

### Post by Konbuntu on 2009-10-19
sorry, newbie here.. i got it fixed , thanks! =)

---

### Post by TekMuzik on 2009-10-20
No problem, that's what this forum is for. :)

If you do check this again though, please mark your thread as [solved]. Thank you. :P

---

### Post by az on 2009-10-20
> **Konbuntu said:**
> Im trying to open my external HD and i got an error message... 

see the attachment!


thanks in advance!

Instead of rebooting, you can fix the problem in Ubuntu:
sudo ntfsfix /dev/sdb1

---

