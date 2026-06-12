---
title: "Accessing Xubuntu system from another computer in the same network"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by mravenca on 2006-11-05
Hello, I have this problem: 
I would like to be able to access a computer with XUbuntu installed on it from a different computer connected in my network. I would like to be able to view it's shell in one window on my computer with Windows XP.
What is the easiest way to do this? 
Thank you very much. I will appreciate any help, actually I do not know what should I exactly search for.

---

### Post by FrodoB on 2006-11-05
Using Synaptic install openssh-server on the Xubuntu machine, if it has not been done already, and edit /etc/ssh/ssh_config and uncomment the line:

PasswordAuthentication yes

Then get putty for the Windows machine and install it:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

Putty has to be installed into a place that is in your path, or modify you path to it.

---

