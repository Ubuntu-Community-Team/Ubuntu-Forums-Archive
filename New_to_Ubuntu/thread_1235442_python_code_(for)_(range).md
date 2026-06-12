---
title: "python code (for) (range)"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by leedrew on 2009-08-09
Hi I been trying to figure out how to get a python code to work [COLOR=green]btw this is school homework [/COLOR][COLOR=black]and I keep getting the first part to run but then when i added a for counter range (0,number) the code stopped and said that I couldn't use (0, number) why is this?[/COLOR]

---

### Post by freak42 on 2009-08-09
hard to say without the code and the exact error message.

but you can check the following

is your number an integer?
is your number an initialized variable?

hth
matthias

---

### Post by The Cog on 2009-08-09
It would help if you posted the code and the error message. However, a couple of guesses:

* It should be:
```
for counter in range(0, number):
```
Notice the word in and the trailing colon. Your post was missing these.

* Make sure the variable **number** does indeed contain a number. That number should be a positive integer (not floating point).

---

