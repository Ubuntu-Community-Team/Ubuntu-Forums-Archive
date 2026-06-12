---
title: "apt get help for lightning extension"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by hagar54 on 2011-04-24
I am attempting to use apt-get to install the lightning extension for Thunderbird. When typing

1)  sudo apt-get lightning
or
2)sudo apt-get lightning-extension

I receive 

1) E: Invalid operation lightning

This is the current problem I am having and would like to fix, consequently; I am unable to use apt-cache to search for anything.

I have read though the ubuntu apt-get how to without finding (or knowing I found) the answer.

Thanks for any help

---

### Post by Elfy on 2011-04-24
You're missing the install

```
sudo apt-get install *package*
```

---

### Post by oldos2er on 2011-04-24
```
sudo apt-get install xul-ext-lightning
```

---

### Post by hagar54 on 2011-04-24
That was easy and worked, of course...

Thank You both for the quick reply




..also, I believe I am suppose to mark this as solved, but cannot find the correct action...Thanks again for your help

---

### Post by Elfy on 2011-04-24
It's in Thread Tools at the top of this thread.

---

