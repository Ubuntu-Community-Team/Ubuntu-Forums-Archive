---
title: "Some programs won't start"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by CoreyB. on 2009-02-01
Some of the programs I have installed won't start.  One, jEdit, shows the splash screen, and just stalls.  I just installed that program a few days ago.  Another one that won't start is IPblock.  The prompt for admin privlages shows up, but after I type them in, the program won't start.  I've tried doing a complete removal in synaptic and reinstall, but it still won't start.

I have had both of these programs start before without issue.  I have also tried booting to an earlier kernal, but that didn't help.

I have know idea where to start troubleshooting or what could be wrong, I am new to Ubuntu and Linux.

How can I troubleshoot and what other info do you need?

---

### Post by kestrel1 on 2009-02-01
Have you tried starting the programs from the terminal?
Try typing jedit in a terminal & post the output if there are errors.

---

### Post by CoreyB. on 2009-02-01
> **kestrel1 said:**
> Have you tried starting the programs from the terminal?
Try typing jedit in a terminal & post the output if there are errors.

Thanks a ton.  I ran jedit through the terminal and I got a warning about not having my JAVA_HOME environment variable set.  I googled the problem and found that if I add the line "export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.10" in the file, "/etc/environment".

---

### Post by Daveth on 2009-02-01
bit of an obvious question, but you installed java 6 jre I assume? It is in the repository.

---

### Post by kestrel1 on 2009-02-01
Probably better to install ubuntu-restricted-extras. I think I remember that java is installed along with it.

---

### Post by CoreyB. on 2009-02-01
> **Daveth said:**
> bit of an obvious question, but you installed java 6 jre I assume? It is in the repository.

Yeah, I installed the jre awhile ago, but recently installed the jdk, that may have somehow screwed something up.  All of the programs that had issues relied on java, but they are all fine now that I did what I mentioned above.

---

