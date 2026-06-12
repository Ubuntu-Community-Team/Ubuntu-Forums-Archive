---
title: "/var/run"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-28
[SIZE="3"]Good morning!

What is the purpose of the /var/run folder?

ie...what files are contained in it and can they be deleted safely?

If they were "accidentally" deleted (:lolflag:) , is there a way to recover short of starting over and re-installing ubuntu?[/SIZE]

---

### Post by marco123 on 2009-02-28
/var/run contains system information data describing the system since it was booted. Files under this directory must be cleared (removed or truncated as appropriate) at the beginning of the boot process. Programs may have a subdirectory of /var/run; this is encouraged for programs that use more than one run-time file.

/var/run should be unwritable for unprivileged users (root or users running daemons); it is a major security problem if any user can write in this directory. Process identifier (PID) files, which were originally placed in /etc, must be placed in /var/run. The naming convention for PID files is <program-name>.pid. For example, the crond PID file is named /var/run/crond.pid.

Cheers, Marco.

---

### Post by mistypotato on 2009-02-28
Hi Marco and thanks  :KS

So I suppose if everything is gone from that directory, I can just re-boot the computer and it will return to "normal" ?

---

### Post by marco123 on 2009-02-28
> **mistypotato said:**
> Hi Marco and thanks  :KS

So I suppose if everything is gone from that directory, I can just re-boot the computer and it will return to "normal" ?

Probably, but I wouldn't recommend it.:)

Cheers, Marco.

---

### Post by mistypotato on 2009-02-28
Thx again Marco.

For anyone who searches on this topic later.........

I had changed permissions on the /var directory because mondo-rescue reported that it could not create the temp files it needed to create in the run directory and I wanted to see why.

In doing so, the "sudo" sub-directory permissions were changed and that caused a problem.  In fact, ALL the files in the /run directory _seemed_ to have been wiped out.

But, I kept getting an error message when using sudo(somthing) on that directory saying that the permissions were wrong on the subdir /sudo (which didn't even appear to be there)...

So I went ahead and changed the permissions on /sudo (even though I thought it was gone) and when I did that, everything re-appeared.

Don't ask me how or why.

Then I re-set permissions on the var directory back to what they normally are (by looking at another ubuntu computer next to it).

I re-booted and everything was fine.

thx for the assist Marco :KS

---

