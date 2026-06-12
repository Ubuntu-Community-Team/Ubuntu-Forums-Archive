---
title: "trouble executing shell scripts in GUI"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by aric9514 on 2009-01-04
I'm having trouble executing any shell scripts by double clicking (using 8.10).
an example is

```
#!/bin/bash
cat > test << EOF
Test text
```
with permissions set to
```
-rwxr-xr-x
```
it works fine from konsole, but does absolutely nothing if I double click on it.

Can anyone offer ideas?

---

### Post by SuperSonic4 on 2009-01-04
Isn't it single click in dolphin?

Check the output anyway, I did a conversion script before and it done it in the background. I didn't actually find out until I checked the directory

---

### Post by aric9514 on 2009-01-04
Yeah, I changed dolphin to double click. I've only just moved over from windows and needed my reassuring double clicks.

How do I check the output? for what it's worth, I'm actually trying to get ssh to run from the desktop, and that requires me inputting  password at some stage so I don't think it's running in the background. It did create the file in the ~/scripts directory when run from konsole, but it didn't when run from GUI.

---

### Post by txcrackers on 2009-01-05
Why don't you use *kdessh* or one of the other GUI SSH front-ends? (Search for "kde ssh" in adept or synaptic)

---

