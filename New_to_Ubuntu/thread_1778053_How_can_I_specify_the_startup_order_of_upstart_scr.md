---
title: "How can I specify the startup order of upstart scripts?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by sofakng on 2011-06-08
I have three upstart scripts (very basic) that I need to start in a specific order.  Actually, it would great if it could even pause between them.

For example:

Start script #1.
Sleep 5 seconds.
Start script #2.
Sleep 5 seconds.
Start script #3.

Is this possible?  If so, how?

---

### Post by TeoBigusGeekus on 2011-06-08
Why don't you join them all together in one script separated with sleep commands between them?

---

### Post by sofakng on 2011-06-09
Thanks for the response!

I was thinking of using a separate job for each application because I'd like to respawn automatically if they crash.  (using the upstart "respawn" flag)

---

