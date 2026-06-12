---
title: "Lirc Setup"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by G00D_GUY on 2009-11-04
I upgraded to 9.10 and went through the setup for Lirc, but then decided to use another remote. How do I run that setup again to choose the correct remote?

---

### Post by ohzopants on 2009-11-05
Try:
```

sudo dpkg-reconfigure lirc

```

Run that in a terminal and it should prompt you for the type of remote and receiver you are using.

---

### Post by G00D_GUY on 2009-11-05
Thanks. Thats what I needed. That was incredibly easy. 

Just when I thought I was becoming proficient at Ubuntu, or at least finding the answers, I got stumped by this apparently simple step. :(

Thanks again.

---

