---
title: "Running a Java Development Kit (JDK)"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by blackbeltsas on 2010-08-30
I am trying to run a file called jdk-6u20-linux-i586.bin and I have already made to executable but when I click on it Archive Manager says Archive type not supported.  I tried doing it through terminal with ./jdk-6u20-linux-i586.bin but this came up 
./jdk-6u20-linux-i586.bin: line 1: syntax error near unexpected token `<'
./jdk-6u20-linux-i586.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

so I am at a loss and can't program for school if anyone can help it will be much appreciated. Thanks

---

### Post by QIII on 2010-08-30
First, if you are going to do it that way, use Update 21.  

Otherwise, enable the Partner repo in Software Sources and install Update 20 from the Partner repo via Synaptic.  (Maybe they have updated to Update 21, in which case your problem is solved.)

Could you give me a step-by-step of what you have done?

---

### Post by spjackson on 2010-08-30
> **blackbeltsas said:**
> I am trying to run a file called jdk-6u20-linux-i586.bin and I have already made to executable but when I click on it Archive Manager says Archive type not supported.  I tried doing it through terminal with ./jdk-6u20-linux-i586.bin but this came up 
./jdk-6u20-linux-i586.bin: line 1: syntax error near unexpected token `<'
./jdk-6u20-linux-i586.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

so I am at a loss and can't program for school if anyone can help it will be much appreciated. Thanks
It looks like you have not downloaded it properly. What does
```
ls -l ./jdk-6u20-linux-i586.bin
```show? The size should be 84796967. It looks like you have downloaded a web error page instead.

But as QIII says, you'd probably be better off using the repositories.

---

### Post by dv3500ea on 2010-08-30
Can't you just install [openjdk-6-jdk]("apt:openjdk-6-jdk") or [gcj]("apt:gcj")?

---

### Post by QIII on 2010-08-30
> **dv3500ea said:**
> Can't you just install [openjdk-6-jdk]("apt:openjdk-6-jdk") or [gcj]("apt:gcj")?

If the instructor requires Java JDK, then that's what he needs.

And Yes, I do realize what OpenJDK is and where it comes from.

By the way, blackbeltsas, we'll help with this part but not with actual homework.  ;)

---

