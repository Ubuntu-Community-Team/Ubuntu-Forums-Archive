---
title: "clearing the terminal window"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Matt26 on 2009-01-17
what command will clear the current contents of a terminal window, so that i can get a blank terminal window like when i first open it?

thanks.

---

### Post by thezood on 2009-01-17
```
clear
```
:)

---

### Post by homemadejam on 2009-01-17
You could also use *Ctrl + L* too :]

Jam

---

### Post by Matt26 on 2009-01-17
> **thezood said:**
> ```
clear
```
:)

i knew it was something obvious like that- i thought i had already tried that command but apparently not... thanks.

---

### Post by drs305 on 2009-01-17
Another command that will clear the screen is:
```
reset
```
The difference is that 'reset' will truly clear the screen - you won't be able to scroll back up to see previous screen outputs.

---

### Post by rfreedman on 2009-01-17
> **drs305 said:**
> Another command that will clear the screen is:
```
reset
```
The difference is that 'reset' will truly clear the screen - you won't be able to scroll back up to see previous screen outputs.

While this is true, clearing the screen is really just a side-effect of reset - what it really does is re-initialize the terminal.
See ```
man reset
``` for more detail.

---

