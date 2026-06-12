---
title: "X : 1 -query startup"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by Matthijs on 2007-08-29
Hello there, 

I having a server at home and i manly connect to it with SSH. But now a friend of my had shown me a way to do the same, only with X!! here's the command i use then.
  X :1 -query 192.168.1.102
After that, there is a new gnome session in tty8 (Ctrl+Alt+F8) and that's really great!

My question is how to make this default when i boot up my PC. So that tty7 is my normally work PC, en tty8 will be my server. Is it even possible?

Thank You,

Matthijs

---

### Post by timcredible on 2007-08-29
you could also connect to your server with a normal window via Xnest.  sample:
Xnest :30 -query 192.168.1.102
from a gnome terminal after you've logged in normally.  that way you can be working on both at the same time and can connect to multiple servers at once if you want.  it's easier and more functional, IMHO.  Xnest is available in synaptic.

---

### Post by Matthijs on 2007-08-30
Hello timcredible,

That way i did the trick before... and using it a lot now. But i was curious if there is a way to do this on a other tty.  

So thank you for your answer/time, but it is not the answer to my question.

---

### Post by Matthijs on 2007-09-29
*bumb*

---

