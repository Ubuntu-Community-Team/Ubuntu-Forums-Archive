---
title: "Ubuntu FireFox and Invision power board problem"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Gp. on 2009-05-25
Hi,
I'm a frequent visitor to the [www.limpbizkit.org](www.limpbizkit.org) forums.

On Windows, I have no problems.

But when I use Firefox in Ubuntu the forums display differently. Different font, and the weirdest issue is avatars do not show?

Why?

---

### Post by Celauran on 2009-05-25
I know it sounds obvious, but have you checked that you're logged in on your Linux machine? Avatars won't show if you aren't.

Do you have the Microsoft fonts installed on your Linux box? The CSS for that site specifies some Windows-specific fonts first, then the default sans-serif for your machine, which will also be different on Linux than in Windows. If you've got the MS fonts installed, then it's an interesting problem. If you don't, it's normal behaviour.

---

### Post by Gp. on 2009-05-25
No I don't. How do I install the MS fonts?.

---

### Post by eilios on 2009-05-25
Use "sudo apt-get install msttcorefonts"

---

### Post by xtremo on 2009-06-14
Many thanks!

---

