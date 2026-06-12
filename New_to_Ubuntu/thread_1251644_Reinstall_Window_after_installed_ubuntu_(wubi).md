---
title: "Reinstall Window after installed ubuntu (wubi)"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by luckymancvp on 2009-08-27
I found this for my problem : recovery ubuntu after reinstall window.

Copy file : from C:\ (where window be installed) to other folder ex D:\boot

  AUTOEXEC.BAT  
  CONFIG.SYS  
  MSDOS.SYS	
  ntldr	 
  wubildr.mbr
  boot.ini      
  IO.SYS	  
  NTDETECT.COM	
  wubildr

Install window

Copy all file from D:\boot back to C:\

ps: I'm not good at English :(

---

### Post by rcayea on 2009-08-27
Are you trying to install Windows and keep Ubuntu (wubi)? Or, do you want to install Windows and remove Ubuntu?

---

### Post by luckymancvp on 2009-08-27
> **rcayea said:**
> Are you trying to install Windows and keep Ubuntu (wubi)? Or, do you want to install Windows and remove Ubuntu?

I install new Windows and keep Ubuntu (wubi)

---

### Post by Mark Phelps on 2009-08-28
Hope you're talking about Windows XP because that's what this file list applies to.  Windows Vista would need a different file list.

---

### Post by LewRockwell on 2009-08-28
the wubi-buntu-landmine strikes again

.

---

### Post by luckymancvp on 2009-08-28
> **Mark Phelps said:**
> Hope you're talking about Windows XP because that's what this file list applies to.  Windows Vista would need a different file list.

That right, I'm talking about XP . My computer isn't strong enough to install Vista.

---

