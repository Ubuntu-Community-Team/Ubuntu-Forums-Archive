---
title: "Sources list error. Please Help"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Pall_tech on 2010-07-09
Hello, 

New member here, and also a new convert to Ubuntu. I am getting a sources list error, if any one of you could help me with that.

2 errors, Related, both the same, 

> Failed to load the package list
This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.This comes in in the software centre.

while this

> Could not initialise the package information
An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘wget’ is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'occurs in the update manager. 

I went into /etc/apt/sources.list and went to line 54 to add a # to it, but I cant seem to be able to edit anything in there. 

if anyone could help me out with this. That'd be great. Thanks in advance.

---

### Post by howefield on 2010-07-09
> **Pall_tech said:**
> I went into /etc/apt/sources.list and went to line 54 to add a # to it, but I cant seem to be able to edit anything in there

Try opening a terminal and type the following..

```
gksudo gedit /etc/apt/sources.list
```

Then edit as required.

---

### Post by Pall_tech on 2010-07-09
aaah thank you sir! you just made my night! all fixed and running well!

---

