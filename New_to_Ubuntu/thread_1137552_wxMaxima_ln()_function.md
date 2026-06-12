---
title: "wxMaxima ln() function"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by mevets on 2009-04-25
I dont know how to represent the natural log in wxMaxima. I have figured out that e^n is exp(n), but figure out ln, even though I have look through the help pages.

Does anyone know how to represent ln using wxMaxima?

---

### Post by conscious on 2009-04-26
It's log(x).

If you have maxima-doc package installed, you can use the help menu to find information about functions.

---

### Post by mikethebike on 2009-09-13
The only way i can get ln(x) to work is by:-
float(log(x)/log(%e^1))

a bit long winded i know but it works.
hope this helps.

---

