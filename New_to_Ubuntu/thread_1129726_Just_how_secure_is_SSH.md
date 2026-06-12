---
title: "Just how secure is SSH?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Vunutus on 2009-04-19
That question has been rattling around in my mind for a while now. Is SSH's security currently unbeatable? Can I always assume that whatever I send over SSH will be secure?

For example, say I'm on my laptop at some unsecured wifi hotspot. For some reason, I need to enter some financial information into a website. If I SSH into my home computer, start up Firefox, and enter said information in that SSH'd Firefox, would I be safe?

---

### Post by juancarlospaco on 2009-04-19
Highest security.

---

### Post by amingv on 2009-04-19
In theory: yes.

In practice: there's no such thing as safety, but SSH it's pretty damn close as long as you keep good practices that don't compromise your passwords and make sure you're connecting to the right host.
If you think about it too much you might as well leave online banking altogether (some of the algorithms are the same).

(I wouldn't send financial info in just any pubic place tho, security cameras everywhere and so forth).

---

### Post by doas777 on 2009-04-19
is it secure? no. is it safe, probably, if safely configured.

any open port/process is a point of vulnerability. if that vulnerability will be exploited is the core of the issue. I do not enable ssh access to my routers from the wan interface because i do not believe that it is safe enough to allow administration from the outside. 

that said, I would feel more comfortable exposing an ssh port to the world, than most other processes, including some popular VPN packages. if your users are well trained, and you have a strong password policy (changes often and requires 4-factor passwords, etc) then it is probably safe enough for most purposes.

---

### Post by llamabr on 2009-04-19
More so than most.  Of course, you're more secure using keys, than typing your password.

---

