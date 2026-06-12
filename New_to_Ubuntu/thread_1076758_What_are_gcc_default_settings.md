---
title: "What are gcc default settings?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Mariane on 2009-02-21
Hi, 

I am trying to install a program and it asks several questions. 
I don't know what to answer. Please tell me. I am using gcc 
as it came from the packages. 

What is/are the compiler command? [cc]
   No, this one is gcc
What is/are the compiler flags? [-g]
   I don't know
What is/are the install command? [install -s -m 755]
   I don't know
What is/are the archive sorting command? [ranlib]
   I don't know
What is/are the archive update command? [ar nu]
   Should I say it is "apt-get update"?
What is/are the architecture? [SUN]
   Should I say it is ubuntu?

This program expects a UNIX machine... 

Mariane

---

### Post by karlr42 on 2009-02-21
What program are you trying to install?

---

### Post by krzysz00 on 2009-02-21
> **Mariane said:**
> Hi, 

I am trying to install a program and it asks several questions. 
I don't know what to answer. Please tell me. I am using gcc 
as it came from the packages. 

What is/are the compiler command? [cc]
   No, this one is gcc
What is/are the compiler flags? [-g]
   I don't know
What is/are the install command? [install -s -m 755]
   I don't know
What is/are the archive sorting command? [ranlib]
   I don't know
What is/are the archive update command? [ar nu]
   Should I say it is "apt-get update"?
What is/are the architecture? [SUN]
   Should I say it is ubuntu?

This program expects a UNIX machine... 

Mariane
Accept the defaults for everything but architecture, there say x86. If that doesn't work try:
i386, 386, 496, 686, i686, i486, intel, INTEL.
Also, the archive update command is "ar u" (no quotes)
What is the program anyway?

---

### Post by snova on 2009-02-21
All of the defaults are reasonable, and correct. This is the only one I'm concerned about:

> **Mariane said:**
> 
What is/are the architecture? [SUN]


I would suggest **x86**. It could also be looking for OS information, though, in which case you could try **linux**.

I'd like to look at the script to be sure. What program is this?

---

