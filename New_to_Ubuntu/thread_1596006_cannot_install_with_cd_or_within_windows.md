---
title: "cannot install with cd or within windows"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Boisvertgris on 2010-10-13
When I try to load from cd  I get this message after awhile:
 
[CENTER]Ubuntu 10.10

[/CENTER]
[LEFT]131.196144 Kernel panic-not syncing: Attempted to kill init!
131.196156 Pid:1, comm:run_init Not tainted 2.6.35-22 generic #33 Ubuntu
131.196165 call Trace:
131.196179 <c05c6468> ? printk+0x2d/0x35
131.196188 <c05c63c3> Panic+0x5a/0x2d
131.196197 <c014d734> forget_original_parent +0x2e4/0x2f0
131.196206 <c01ac66d> ? call_rcut 0xd/0x10
131.196213 <c014d753> exit_notify+0x13/0x170
131.196220 <c014f03c> do_exit+0x17c/0x340
131.196228 <c03da0507> ? redirected_tty_write+0x0/0x90
131.196236 <c014f2d87> sys_exit+0x18/0x20
131.196247 <c05c90a4> syscall_call+0x7/0xb
 
am I doing something wrong?[/LEFT]

---

### Post by diablo75 on 2010-10-13
Try to run the memory testing utility that's included with the CD to make sure your RAM is not faulty.

---

### Post by SoulSmasher on 2010-10-13
I'm not sure, whether it's cd reading related, but if it is, try [unetbootin]("http://unetbootin.sourceforge.net/") and install the iso image datas into a usb stick, and boot from it.

---

### Post by diablo75 on 2010-10-13
One other possibility is that your BIOS needs to be updated.  I used to have an older computer that would fail to boot from Linux CD's because the BIOS contained an glitch:  "Booting from a CD-ROM which is on the same IDE channel as the primary hard drive" could cause problems.  So two ways around that would be to put the CD-ROM on a separate IDE cable (if you even have those in your machine) or update your BIOS (if it's out of date).

---

### Post by Boisvertgris on 2010-10-13
Thanks for the info I will try  these things , hopefully something will work but even in windows it tells me an error occured  permission denied and that is as far as it will go .

---

### Post by diablo75 on 2010-10-13
> **Boisvertgris said:**
> Thanks for the info I will try  these things , hopefully something will work but even in windows it tells me an error occured  permission denied and that is as far as it will go .

Can you be more specific about this error?  Where/when does it say this?  Could you upload a screenshot perhaps?

---

