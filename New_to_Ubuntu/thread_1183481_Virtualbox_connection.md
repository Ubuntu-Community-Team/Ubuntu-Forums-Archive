---
title: "Virtualbox connection"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by mj1001 on 2009-06-10
I have a computer connected to a lan (Windows XP operating system) and I have a laptop (using Ubuntu 8.
10) and the program installed on my laptop called virtual box.
How do I view my windows xp operating system (computer connected on lan)  on my laptopn using ubuntu through virtual box?

Please show me in step because this is my first time to do it ?


Thank you

---

### Post by jaqrah on 2009-06-10
Please verify if the following is true:

Computer #1 (desktop) os=windows xp
Computer #2 (laptop) os=Ubuntu 8.10

If so, virtualbox isn't necessary.  You would need to set up Samba (it allows network sharing so your Ubuntu laptop can see your windows desktop shares).  There are quite a few tutorials if you google Ubuntu 8.10 samba tutorial.  Even  though its a bit dated, I used the following tutorial to set up my samba shares.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Now if you meant you are running xp as a vbox guest on an ubuntu host and you want to see your windows desktop I would suggest searching this site for vbox file sharing.  There are many threads about this topic in the Virtualization forum.

---

### Post by mj1001 on 2009-06-10
> **jaqrah said:**
> Please verify if the following is true:

Computer #1 (desktop) os=windows xp
Computer #2 (laptop) os=Ubuntu 8.10

If so, virtualbox isn't necessary.  You would need to set up Samba (it allows network sharing so your Ubuntu laptop can see your windows desktop shares).  There are quite a few tutorials if you google Ubuntu 8.10 samba tutorial.  Even  though its a bit dated, I used the following tutorial to set up my samba shares.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Now if you meant you are running xp as a vbox guest on an ubuntu host and you want to see your windows desktop I would suggest searching this site for vbox file sharing.  There are many threads about this topic in the Virtualization forum.

Thank aloot for your help

---

### Post by YldGuy on 2009-06-10
> **mj1001 said:**
> I have a computer connected to a lan (Windows XP operating system) and I have a laptop (using Ubuntu 8.
10) and the program installed on my laptop called virtual box.
How do I view my windows xp operating system (computer connected on lan)  on my laptopn using ubuntu through virtual box?

Please show me in step because this is my first time to do it ?


Thank you

well.. you cant use virtualbox to see a machine on the network. virtualbox is used to *install* xp as a virtual machine in it. what are you trying to do anyway?

---

