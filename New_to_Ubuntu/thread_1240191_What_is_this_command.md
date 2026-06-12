---
title: "What is this command?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Kansasguy on 2009-08-14
lspci –v | less



Actually, what is the character between the 
"lspci -v"        and the "less"?

and how do you make it?

Thanks

---

### Post by halitech on 2009-08-14
lspci - list the pci based hardware in your system
-v use the verbose mode
| pipe
less - means you get 1 screen and can scroll through it

the | is Shift + \ which gives you the |

---

### Post by Kansasguy on 2009-08-14
Thank you so much

---

### Post by colau on 2009-08-14
```

man lspci

```

---

### Post by colau on 2009-08-14
"|" means pipe, the output of first command "lspci -v" would be the input for second command "less".

---

### Post by Sidewinder1 on 2009-08-14
As colau stated, kinda, you can:
```
man "any linux command here"
``` 
and get all the info you need.
Even:
```
man man
```
to get started...
HTH,
Side

---

