---
title: "How to set mutt 'From' field?"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by squinter on 2007-06-18
Hi,

I couldn't find a way to set mutt 'From' field. At the moment when I send an email from mutt, the from field reads: [email]user@serv1.example.com[/email], but I want it to be [email]user@example.com[/email].

Cheers

---

### Post by mitch.c on 2007-06-20
Add the following line to ~/.muttrc:
```
set from='yourname@yourdomain.com'
```
[URL="http://ubuntuforums.org/showthread.php?t=377083"]
[COLOR="Red"]UAResolved[/COLOR][/URL]

---

### Post by squinter on 2007-06-20
It doesn't work. Do I need to restart anything?

---

### Post by mitch.c on 2007-06-20
Sorry, I forgot... you also need the following line to ~/.muttrc:
```
set use_from=yes
```

---

### Post by squinter on 2007-06-21
That works! thank you very much ^^

---

