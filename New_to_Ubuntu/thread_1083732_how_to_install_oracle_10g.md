---
title: "how to install oracle 10g"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by gkraju on 2009-03-01
hi i want to install oracle 10g express edition(XE) in ubuntu 8.04
can any one tell me how to do it 
thanks in advance

---

### Post by Nepherte on 2009-03-01
Download the .deb file from their site: [http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html](http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html)
and double click on it.

---

### Post by gkraju on 2009-03-01
> **Nepherte said:**
> Download the .deb file from their site: [http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html](http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html)
and double click on it.
i did it but it displayed an error message saying that not enough swap space to install and installation failed

---

### Post by linux_tech on 2009-03-01
type ```
top
```
in terminal to see swap space
How much RAM do you have?
If you need to set up swap this should help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Binny88 on 2009-03-01
Oracle needs about 1 gb of space. Download Gparted from Ubuntu repositories then add more swap space. A word of caution though, after you create the swap  space you should initiate swapon ( using that space as swap) you wil find an option, but from my experience i have noticed it gets swapped off the nest restart,This will create problems for oracle. It may not happen on your distro. After installation you will be told to open a website using an ip address but it will not open. You can change this by opening the configuration file where you have to specify the user name(SYSTEM) and password. You might not encounter such problems if u r lucky

Best of Luck

---

