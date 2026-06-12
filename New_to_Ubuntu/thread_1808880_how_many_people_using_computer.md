---
title: "how many people using computer?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-20
On the terminal, what is the command to see how many people are using the server?  Or who is logged in?

thank you.

---

### Post by skatinjj on 2011-07-20
```
users
```

---

### Post by tgalati4 on 2011-07-20
w

(which stands for "what")

---

### Post by skatinjj on 2011-07-20
I believe the 'who' command (no quotes) is a better solution after looking it up with google (see my signature).

---

### Post by 1clue on 2011-07-20
w
who
who am i
users

---

### Post by 007casper on 2011-07-20
thank you so much everyone

---

### Post by bodhi.zazen on 2011-07-21
Those commands do not directly tell you the number of logged in users.

```

echo "Number of logged in users = $(who | awk '{print $1}' | sort | uniq | wc -w)"
```

---

### Post by uRock on 2011-07-21
> **bodhi.zazen said:**
> Those commands do not directly tell you the number of logged in users.

```

echo "Number of logged in users = $(who | awk '{print $1}' | uniq | wc -w)"
```

I like that one. :)

---

### Post by 007casper on 2011-07-25
thank you so much bodhi.zazen

---

### Post by bodhi.zazen on 2011-07-25
Ooops, you actually need a sort in there. I edited my post.

---

### Post by sadaruwan12 on 2011-07-25
If you've been answered please close the thread by marking it as "SOLVED"

Thank you

---

