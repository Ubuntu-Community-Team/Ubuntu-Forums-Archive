---
title: "How to remap a key in ubuntu 10.04?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-01
The key "A" on my keyboard is not working.Can i make some arrangement by which i can use "Z" instead of "A"?

---

### Post by karthick87 on 2010-11-02
I have got the answer,thank you..

---

### Post by clive littlewood on 2010-11-02
What was the answer for anyone else who has this problem ??         :(

Clive

---

### Post by karthick87 on 2010-11-02
Type xev in terminal and press "z" to find the keycode of z

keycode of z is 52

```
xmodmap -e "keycode 52 = a A"
```

---

