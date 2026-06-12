---
title: "Change system name on Ubuntu 8.1"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Feyroce on 2009-01-07
Hi,

I have just installed a fresh Ubuntu 8.1 on my former Vista computer.
Unfortunately, I didn't change the system name.
How can I do that once the system is installed ? :confused:

Thx,

B.

---

### Post by scorp123 on 2009-01-07
> **Feyroce said:**
> Unfortunately, I didn't change the system name.
How can I do that once the system is installed ? Open a terminal ( Applications > Accessories > Terminal ) and then type this into it (please copy & paste!): ```
gksu gedit /etc/hostname
``` ... You will be asked for your password.

After that an editor should have opened containing the hostname of your PC. Change the hostname, but please leave it at one line (no pressing of enter or something like that, OK?). Save & close.

After that reboot. When the PC comes up again it should have its new hostname.

---

### Post by Feyroce on 2009-01-07
Worked perfectly !

Thanks !

---

### Post by scorp123 on 2009-01-07
> **Feyroce said:**
> Worked perfectly !

Thanks ! Feel free to hit that "Thank you" button ... ;)

---

### Post by The Cog on 2009-01-07
You will probably find that you can't use sudo any more. If so, boot into recovery mode and use the command
> sudo nano /etc/hosts
and edit the host name there (against 127.0.1.1) to match the new host name. Then reboot.

---

### Post by scorp123 on 2009-01-07
> **The Cog said:**
> You will probably find that you can't use sudo anymore ...  Hmm? Why would that be? :confused: Just because of changing /etc/hostname? 

But you're right regarding /etc/hosts ... I forgot about that one. But I don't really get the connection between the hostname and "sudo" ... ?

---

### Post by The Cog on 2009-01-07
Hmm. I just tried it again, and it seems that sudo doesn't break, it just complains it can't resolve the host name. I'm sure it used to break, years ago. Either that or I mis-typed the password and assumed it had broken, and never tried it again. Live and learn, as they say.

---

### Post by scorp123 on 2009-01-07
> **The Cog said:**
> Live and learn, as they say. :-k Boah, you really got me scared there ... [-X 

:D

---

