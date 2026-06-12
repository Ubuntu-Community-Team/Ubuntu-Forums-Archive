---
title: "Error connecting to shared Windows comp with &quot;smbclient&quot; command"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by rainwalker on 2008-04-25
I do fresh installs of Ubuntu every release, but I back up to our Windows desktop beforehand. My dad (who is unavailable at the moment, so I can't ask him) gave me this command a while back that has worked up until now:
```
smbclient //192.168.1.100/riley$
```
After doing that, it usually asks me for the password to the Windows computer, and then I get and "smb\>" prompt. This time, however, I get this:
> riley@riley-laptop:~$ sudo smbclient //192.168.1.100/riley$
timeout connecting to 192.168.1.100:445
timeout connecting to 192.168.1.100:139
Error connecting to 192.168.1.100 (Operation already in progress)
Connection to 192.168.1.100 failed (Error NT_STATUS_ACCESS_DENIED)
Just FYI, it doesn't ask for the admin password because I've entered it a couple of times already. But anyway, that's the error I keep getting (with and without "sudo").

Any suggestions? 
Places > Network won't work, it never asks for a password (tried it back when I installed Gutsy)

---

### Post by Iowan on 2008-04-26
Can you **ping** the machine (192.168.1.100)?

---

### Post by rainwalker on 2008-04-26
Ah, I actually figured it out...I had a different IP address than the one that had been set to be allowed access to the computer.
Looking back, it was shamefully obvious.

---

### Post by Iowan on 2008-04-27
Glad you found it... Mark this one SOLVED (Thread Tools).

---

