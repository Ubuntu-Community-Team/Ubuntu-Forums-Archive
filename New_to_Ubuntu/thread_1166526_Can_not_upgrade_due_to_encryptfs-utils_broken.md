---
title: "Can not upgrade due to encryptfs-utils broken"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by wariskampar on 2009-05-21
Hello, 

I just removed 8.10 and installed 9.04 (fresh install on /dev/sda1 as /, /dev/sda3 as /home). At the end of the installation, i got error  message that encryptfs-utils package is broken (something like that..) but I just hit the continue button and complete the process. When I boot in (very fast indeed!!), I see error icon on Panel (Please c attachment). Now, I can not upgrade, and try removing encryptfs-utils using Sypnatic yield nothing. What should I do next?

---

### Post by lisati on 2009-05-24
What happens when you go to the terminal and type in the following?
```
sudo dpkg --configure -a
```

---

### Post by wariskampar on 2009-05-25
Problem solved. I just followed the instruction in the error message. Ubuntu is getting better in each release.

---

