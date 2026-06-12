---
title: "TinyOs in ubuntu"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by s.sahar on 2010-07-19
Hello everybody,
I'm totally confused with installing a software on ubuntu 9.1 named **TinyOs**.:(
Is anybody  familiar with this software and how to install it on ubuntu?
All inputs are appreciated.


Regards

---

### Post by mikewhatever on 2010-07-19
Take a look at the Installation Page.
[http://docs.tinyos.net/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages](http://docs.tinyos.net/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages)

---

### Post by DexterLB on 2010-07-19
Edit: Wait, no, sorry. I was wrong.

---

### Post by s.sahar on 2010-07-19
I have seen that but this is the result  in terminal:

sahar@sahar-laptop:~/Desktop$ sudo apt-get install tinyos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tinyos is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Is it means that tinyos is already installed ?

---

### Post by Paqman on 2010-07-19
> **s.sahar said:**
> 
Is it means that tinyos is already installed ?

Yep.

---

### Post by s.sahar on 2010-07-19
If it is installed,why I can't see it?
How can I access to the program and use it?

---

### Post by Paqman on 2010-07-19
Have you read the [TinyOS documentation]("http://docs.tinyos.net/index.php/Using_TinyOS")? There's also a [FAQ]("http://webs.cs.berkeley.edu/tos/faq.html").

---

### Post by s.sahar on 2010-07-19
Yes,I have read the documentation but the problem is that I can't find the installed software icon to click on and open it!
:(

---

### Post by Paqman on 2010-07-19
I don't think you'll get an icon. I don't really know anything about it, but it seems to be an operating system for networked sensors. There do seems to be plugins available for Eclipse, according to it's Wikipedia page.

---

### Post by mikewhatever on 2010-07-19
Indeed, nothing suggests TinyOS has a point&click interface.

---

