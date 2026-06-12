---
title: "OpenSSH Server - Disable ID Message"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by ricadelic on 2006-12-01
Hi

when i telnet to my openssh server on port 22 i get the message "SSH-2.0-OpemSSH_4.3p2 Debian-5ubuntu1".

Since i've forwarded this port on my router to port 80, i would like to disable this line and show an empty, or custom message, since anyone who browses to my domain gets to see that OpenSSH is installed on this pc.

Does anyone know how to disable this ID string, or how can i change it?

Cheers

---

### Post by ricadelic on 2006-12-05
Bump ! ;-) .. Anyone who knows how to disable the server's ID message?

---

### Post by netztier on 2006-12-05
> **ricadelic said:**
> Bump ! ;-) .. Anyone who knows how to disable the server's ID message?

Glancing over [FONT="Courier New"]**/etc/ssh/sshd_config**[/FONT], the line

```
# Banner /etc/issue.net
```

makes me wonder... what happens if you uncomment it, pute some customized text in that file and the restart sshd?

regards

Marc

---

### Post by ricadelic on 2006-12-05
Cheers Marc, gonna try it when i get home. Thanks!

---

### Post by kjacks on 2006-12-07
nope, that didn't work.  that changes the text that's shown before you type your user/password when you first login via ssh.

thats a great place to add something like :

"only authorized users may access, we monitor everything.."

---

### Post by netztier on 2006-12-13
> **kjacks said:**
> nope, that didn't work.  that changes the text that's shown before you type your user/password when you first login via ssh.

thats a great place to add something like :

"only authorized users may access, we monitor everything.."

Ah well - that was the other thing I had suspected "banner" to be. I apologize for speculating in the wrong direction and therefore being misleading.

regards

Marc

---

