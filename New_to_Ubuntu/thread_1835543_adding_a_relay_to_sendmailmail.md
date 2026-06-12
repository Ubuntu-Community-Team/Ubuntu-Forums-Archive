---
title: "adding a relay to sendmail/mail"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by bneva on 2011-08-29
So I posted a thread before about my mail command not working when I did just a basic command

```
mail -s "hello" email@hotmail.com
```

and we determined it was because my relay was set to 127.0.0.1 so it wasn't sending any messages..

My question is, how do I set up a relay?  I have the mail server address for my ISP which works (according to a friend) but I am not sure what file to put it in.

---

### Post by bneva on 2011-08-29
nevermind I figured it out, had to put it under this in the "sendmail.cf"
# "Smart" relay host (may be null)

---

