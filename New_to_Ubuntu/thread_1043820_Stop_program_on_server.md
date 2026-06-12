---
title: "Stop program on server"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by FiskFisk33 on 2009-01-18
When i run a program on the ubuntu server (8.10) lets take "ping www.google.com" for example, which like other programs i use "take control" of the screen and it seems like what i type in does nothing.

so, well, how do i end it, and get back to where i can type commands?

---

### Post by Bachstelze on 2009-01-18
Ctrl+C.

---

### Post by mjheagle8 on 2009-01-18
```
killall <program name>
```

---

### Post by FiskFisk33 on 2009-01-18
thanks a lot! :)

Edit:
does ctrl+c kill the program or does it leave it running behind, so u need killall <program name> to actually kill it?

---

### Post by Bachstelze on 2009-01-18
It does terminate the program. Don't use kill and killall if you don't know what they do, you shouldn't normally need to anyway.

---

### Post by FiskFisk33 on 2009-01-18
thanks :)

---

