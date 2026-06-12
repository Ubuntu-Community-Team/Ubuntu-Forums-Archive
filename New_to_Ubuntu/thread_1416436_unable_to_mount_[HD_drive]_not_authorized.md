---
title: "unable to mount [HD drive] not authorized"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by ahmade_puck on 2010-02-26
i fail to open Drive with NTFS partition ... 

massage like the title 
[UNABLE TO MOUNT DRIVE D]
not authorize

[UNABLE TO MOUNT DRIVE E]
not authorize

im using dual OS win xp and ubuntu 9.10

how to solve that ? 
help me please im newby ...

---

### Post by Sef on 2010-02-26
Have you installed NTFS configuration too?  If not, then Applications > Ubuntu Software Center > Search: NTFS > Click install on top option (NTFS Configuration Tool)

---

### Post by chaanakya_chiraag on 2010-02-26
I've had this problem too...go to a Terminal (Applications->Accessories->Terminal) and type in ```
gksu nautilus
``` and try the mounting again.  It should work.

---

### Post by chaanakya_chiraag on 2010-02-26
I think it's a problem with PolicyKit, as I can't do it either.  I have to use this workaround.

---

### Post by chaanakya_chiraag on 2010-03-15
I fixed this by starting a certain program (I don't remember what) at login.  I'll post later today with the actual program.

---

### Post by Easy Limits on 2010-03-15
You may want to check your System > Administration > Users and Groups > Your Name > Properties > User Privileges and see what you have check marked.

---

### Post by chaanakya_chiraag on 2010-03-16
It basically occurs if the gnome authentication service hasn't been started, which is what happened to me (I'm using Fluxbox atm).  Sorry I didn't post it yesterday...I'll post it today (I promise!!)

---

