---
title: "laptop froze"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by nikef on 2010-06-14
Hello all 
my laptop has frozen ,with out doing a force shut down is there a nicer way of doing it as my ubuntu does not like force shut down 
thanks

---

### Post by llawwehttam on 2010-06-14
The other way is to hold "alt + sysrq" and type slowly with 1 second in between each character "R E I S U B"

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

if that doesn't work a hard reset is the only way.

un**R**aw      (take control of keyboard back from [X]("http://en.wikipedia.org/wiki/X_Window_System")),  
 t**E**rminate (send [SIGTERM]("http://en.wikipedia.org/wiki/SIGTERM") to all processes, allowing them to terminate gracefully),
 k**I**ll      (send [SIGKILL]("http://en.wikipedia.org/wiki/SIGKILL") to all processes, forcing them to terminate immediately), 
  **S**ync     (flush data to disk),
  **U**nmount  (remount all filesystems read-only),
re**B**oot.

---

### Post by nikef on 2010-06-14
Thanks will give it a try

---

### Post by stoogiebuncho on 2010-06-14
Does it matter if you use the REISUB order or the RSEIUB order?  I learned to remember it with the phrase "Raising Skinny Elephants Is Utterly Boring"

Is one order superior?

---

### Post by RJ12 on 2010-06-14
> **llawwehttam said:**
> The other way is to hold "alt + sysrq" and type slowly with 1 second in between each character "R E I S U B"

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

if that doesn't work a hard reset is the only way.

un**R**aw      (take control of keyboard back from [X]("http://en.wikipedia.org/wiki/X_Window_System")),  
 t**E**rminate (send [SIGTERM]("http://en.wikipedia.org/wiki/SIGTERM") to all processes, allowing them to terminate gracefully),
 k**I**ll      (send [SIGKILL]("http://en.wikipedia.org/wiki/SIGKILL") to all processes, forcing them to terminate immediately), 
  **S**ync     (flush data to disk),
  **U**nmount  (remount all filesystems read-only),
re**B**oot.

^^Agreed this is better than hard resetting (Big time) I remember it with the phrase "Raising Elephants is so utterly boring"

---

