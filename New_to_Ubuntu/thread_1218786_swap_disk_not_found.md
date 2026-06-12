---
title: "swap disk not found"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by scotcella on 2009-07-21
Hi all,

I am having some issues, 

Please refer to my original post:

[http://ubuntuforums.org/showthread.php?t=1218074](http://ubuntuforums.org/showthread.php?t=1218074)

Anyway, upon scanning using the live cd and fdsk'ing as i mentioned in the original post. 

Anyway I noted that the swap space was not found. Is this bad? If it is, how can I fix it?

Thanks in advance.

---

### Post by Finalfantasykid on 2009-07-21
Do you have your swap partiton set to 'swapon' ?  I had a similar problem, and all I had to do was swapon by using GParted.

---

### Post by Tman5293 on 2009-07-21
I had this same problem and I thought that gparted fixed the problem but my swap was off again when I restarted my computer. To fix this you might have to edit your fstab file.

---

