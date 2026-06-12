---
title: "I dont want to type sudo password for installing software"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by paddy100 on 2010-06-03
Hi all,
I have been playing with ubuntu for about a year and i am getting tired typing in the sudo password each time i want to install some software. How can I set it so that I dont have to enter the sudo password when i type [INDENT]sudo apt-get install .................

[/INDENT]All help is greatly appreciated

---

### Post by consindo on 2010-06-03
Type in
```
sudo su
```

Enter your password and then execute any root command you need to. :)

---

### Post by philinux on 2010-06-03
> **paddy100 said:**
> Hi all,
I have been playing with ubuntu for about a year and i am getting tired typing in the sudo password each time i want to install some software. How can I set it so that I dont have to enter the sudo password when i type [INDENT]sudo apt-get install .................

[/INDENT]All help is greatly appreciated

Please read this.
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by HermanAB on 2010-06-03
Simple really, change to Mandriva Linux.

---

### Post by da burger on 2010-06-03
This is not something that I know much about but a more experienced user may be able to explain it better for you. You can configure sudo to run certain commands as root without needing a password for certain users. This is done in the /etc/sudoers file. However please please before even thinking about editing this file make sure you have read at least some of the relevant manuals (man sudoers for example) and backed up the file. Again be careful.
Angus

---

### Post by bodhi.zazen on 2010-06-03
Use an alias in ~/.bashrc

alias apt-get="sudo apt-get"

---

