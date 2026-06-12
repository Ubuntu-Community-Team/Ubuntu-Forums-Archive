---
title: "scripting"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by joe1600 on 2010-02-12
hiii 
am new to ubuntu uinix linux etc..
i would like to know how to write scripts for example
sudo apt-get install wireshark..supply the passwd then answer y or no question and then shudown using init 0 ...

expecting help

reagrds

Joe Joseph

---

### Post by Satoru-san on 2010-02-12
Hey Joe, welcome to the forums.

Unfortuantly there is no way to get it to enter your password for you. Besides why would you need to have a program that did that, its a security risk.

---

### Post by pizza-is-good on 2010-02-12
I used [this book]("http://gd.tuwien.ac.at/linuxcommand.org/tlcl.php") to learn how to use the terminal and scripting. It is very good.

Good luck.

~pizza

---

### Post by jken146 on 2010-02-12
Don't shutdown by doing 'init 0'. Use the command ```
shutdown
```

---

### Post by Satoru-san on 2010-02-12
> **jken146 said:**
> Don't shutdown by doing 'init 0'. Use the command ```
shutdown
```
```
sudo halt
```
If you ever decide to use a different distro there is no shutdown command instead you type halt to turn off your computer.

---

### Post by Vishal Agarwal on 2010-02-12
> **jken146 said:**
> Don't shutdown by doing 'init 0'. Use the command ```
shutdown
```

what is the harm using init 0 ? 
i use it many times.

---

### Post by jken146 on 2010-02-12
> **Vishal Agarwal said:**
> what is the harm using init 0 ? 
i use it many times.

I've had a poke at the docs, and it seems that there is in fact no harm at all. **shutdown**, **telinit**, **reboot** and **halt** are just different tools for changing the runlevel. **shutdown** does have the advantages of setting times and messages, but there's no difference in the actual shutting down process.

---

### Post by spcwingo on 2010-02-12
Try this, but I'll go ahead and tell you that it will just prompt for password, not enter it for you:

```
#!/bin/bash
#
gksudo apt-get install -y wireshark && gksudo shutdown
```

EDIT:  Just note the the above command will only work under GTK environments (gksudo).  If you are using KDE just replace gksudo with kdesudo.

---

### Post by iponeverything on 2010-02-13
expect can be used to interact with passwd (among many other things)

---

