---
title: "iptables problem"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by oldgarol on 2009-10-26
I am using Ubuntu 8.04 on my vps server. Trying to work on iptables but I am getting the following message after entering sudo iptables -L

garol@vps:~$ sudo iptables -L
FATAL: Could not load /lib/modules/2.6.18-128.4.1.el5xen/modules.dep: No such file or directory
iptables v1.3.8: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded

can anyone help please?

---

### Post by gvr2600 on 2009-11-08
Did you try to upgrade?

---

### Post by Noobus Boobus on 2009-12-06
Hello!  Did you solve the problem? I have the same kernel 2.6.18-128.4.1.el5xen on my VPS, and iptables doesn't seem to work with it. I have some projects running on that VPS, so compiling kernel seems a bit scary for me. Is it safe to install new kernel using aptitude?

---

