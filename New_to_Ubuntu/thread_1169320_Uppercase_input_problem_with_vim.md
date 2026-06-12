---
title: "Uppercase input problem with vim"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by B07030810 on 2009-05-25
When I intend to input "W",I press "shift" and "w",but as soon as I press the "****",the cursor moved to other places.In another word,I can't input Uppercase .How to input the uppercase~~~

---

### Post by wizard10000 on 2009-05-25
> **B07030810 said:**
> When I intend to input "W",I press "shift" and "w",but as soon as I press the "****",the cursor moved to other places.In another word,I can't input Uppercase .How to input the uppercase~~~

There's a difference between command mode and insert mode in vim - if Shift-W moves the cursor instead of typing a capital "W" then you're in command mode.  Hit "i" to get into insert mode and your uppercase letters will work just fine.

Hit <esc> to get back into command mode.

---

