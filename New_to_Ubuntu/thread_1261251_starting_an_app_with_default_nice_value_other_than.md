---
title: "starting an app with default nice value other than 0"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by zhanglini on 2009-09-08
How do I start an app with default nice value other than 0?
I mean, I don't want to use "renice" to change the value every time AFTER I started an app.
I tried something like "sudo nice -n -10 firefox" and it did not work...
Thanks in advance

---

### Post by bodhi.zazen on 2009-09-08
What error message ?

You know you need to run nice as root to go lower then 0 , but you will be running firefox as root.

So ...

```
sudo nice -n -10 sudo -u you firefox &
```

Substitue "you" with your log in name.

---

### Post by zhanglini on 2009-09-08
> sudo nice -n -10 sudo -u you firefox 
works!
Thanks Bodhi!

---

### Post by Ganton on 2010-05-18
> Substitute "you" with your log in name

"Sudo myself"... maybe I would never have thought of this. Clever man! It worked!

[...]

I'm thinking that this way you don't have to substitute anything, just make it available for any user:
```
sudo nice -n -10 sudo -u "$USER" firefox &
```

 Thanks!

---

