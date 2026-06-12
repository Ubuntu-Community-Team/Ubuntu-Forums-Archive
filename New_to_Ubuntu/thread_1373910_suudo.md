---
title: "suudo?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Paul T. on 2010-01-06
I just accidentally entered "suudo prelink -a" into a terminal, and pc went beserk...... 
Cursor was constantly scrolling across window producing no output, couldn't stop it. Re-started, opened terminal window and cursor was still doing same thing! After several attempts at typing "exit" I was eventually able to stop it, what the hell did "suudo" do?
Daren't try it again :confused:

---

### Post by chewearn on 2010-01-06
```

$ suudo prelink -a
bash: suudo: command not found

```

:mrgreen:

---

### Post by lotharmat on 2010-01-06
[Here you go]("http://tinyurl.com/yj3g2uj")

---

### Post by Penguin Guy on 2010-01-06
@ Paul T.
When I do the same thing, I get this:
```
$ suudo
bash: suudo: command not found
$ man suudo
No manual entry for suudo
$ help suudo
bash: help: no help topics match `suudo'.  Try `help help' or `man -k suudo' or `info suudo'.

```
Try again, see if the problem persists.


@ lotharmat
If you'd bothered to search google before criticising him for not doing so, you'd find that this page is the first link, and the other links are all to unrelated topics.

---

### Post by Captain_tux on 2010-01-06
> **Paul T. said:**
> "suudo prelink -a"

Are you **sure** that's what you entered? It's an invalid command and it shouldn't had done anything other than tell you it's invalid.

---

