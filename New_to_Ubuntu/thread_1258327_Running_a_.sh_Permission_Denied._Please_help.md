---
title: "Running a .sh: Permission Denied. Please help"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Windows Nerd on 2009-09-04
Hey all,

I downloaded Netbeans IDE bundled with the Java JDK from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter").

It came downloaded as a .sh file. I tried to run it, but got the permission denied, even as root.

```
scott@scott-laptop:~/Desktop$ ./jdk-6u16-nb-6_7_1-linux-ml.sh
bash: ./jdk-6u16-nb-6_7_1-linux-ml.sh: Permission denied
scott@scott-laptop:~/Desktop$ sudo su
[sudo] password for scott: 
root@scott-laptop:/home/scott/Desktop# ./jdk-6u16-nb-6_7_1-linux-ml.sh
bash: ./jdk-6u16-nb-6_7_1-linux-ml.sh: Permission denied
root@scott-laptop:/home/scott/Desktop# 
```I think this may be because I do not have execute permissions for this file. Anyone want to offer some help?

Scott

---

### Post by pedro3005 on 2009-09-04
Run "chmod +x jdk-6u16-nb-6_7_1-linux-ml.sh" and try again.

---

### Post by |Porsche on 2009-09-04
Well said Don Ramon!

---

### Post by pedro3005 on 2009-09-04
Don Ramon is the best! Yeahhhh :D

---

### Post by Windows Nerd on 2009-09-04
> **pedro3005 said:**
> Run "chmod +x jdk-6u16-nb-6_7_1-linux-ml.sh" and try again.
Thanks. I forgot about chmod +x  to make a file execuetable. Silly me.

Scott

Edit: What were the point of making those two last posts?

---

### Post by pedro3005 on 2009-09-05
Because Don Ramon *is* the best.

---

