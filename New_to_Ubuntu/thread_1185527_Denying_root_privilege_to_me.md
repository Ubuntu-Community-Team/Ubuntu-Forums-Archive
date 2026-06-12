---
title: "Denying root privilege to me"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by adc22 on 2009-06-12
Hi Everyone,

I'm using Ubuntu7.10 in my laptop. But when I try to login as root it denies me. 
Here is the snippet from terminal-

[COLOR=Navy]arindam@ADC:~/Public$ su root
Password: 
su: Authentication failure
Sorry.[/COLOR]

eg, as root, when I tried to edit  /etc/vim/gvimrc file, I could not do it.:(

Please help me. Thanking you in anticipation.

---

### Post by halitech on 2009-06-12
root is disabled by default in Ubuntu, use sudo to do admin tasks that would normally be done as root

---

### Post by mharrison on 2009-06-12
Someone correct me if I am wrong...

But, by default Ubuntu has no Root password.  So you would have to set one to be able to log into root.

If you want to edit /etc/vim/gvimrc, you can try sudo gedit /etc/vim/gvimrc from a terminal.

Sudo will prompt you for your user account password.

---

### Post by gradinaruvasile on 2009-06-12
Try

sudo su -

---

### Post by _Purple_ on 2009-06-12
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by adc22 on 2009-06-12
Thanks buddy. It worked.

---

