---
title: "inquiry please"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Evil79 on 2010-04-24
Greetings,

I'm trying to log in to the "Synaptic Package Manager" but i keep gettign this message.

[[img]http://xs.to/image-53CF_4BD34A3F.jpg[/img]](http://xs.to/share-53CF_4BD34A3F.html)

Require help please.

Regards,
Evil

---

### Post by lisati on 2010-04-24
Go to Applications->Accessories->Terminal, type in the command that it tells you to put in, and press "Enter". You will be asked for your password: it won't show as you type but will still be accepted.

---

### Post by jrothwell97 on 2010-04-24
Open up a terminal and run the following commands, one after the other:

```
sudo dpkg --reconfigure -a
sudo apt-get update
```

---

### Post by avtolle on 2010-04-24
From the command line (Applications>Accessories>Terminal) do ```
sudo dpkg --configure -a
```and see whether that doesn't take care of the problem. Close Synaptic first, if you have not already done so.

---

### Post by Evil79 on 2010-04-24
Indeed, The issue has been fixed.

Much appreciated { lisati - jrothwell97 - avtolle }.

Kind regards,
Evil

---

