---
title: "Unable to find /boot.grub/stage1"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by uppidada on 2011-04-23
I've ubuntu 9.04 version installed in my computer. I've re-installed other OS and lost my grub.

I now have only ubuntu 7.10 live CD with me. Can i re-install grub with this?
If so,how?



I've tried with ubuntu 7.10


sudo grub
grub>find /boot/grub/stage1  
error 15:unable to find

---

### Post by uppidada on 2011-04-23
some one please help me with this..

---

### Post by Paddy Landau on 2011-04-23
I think the following might work from a Live CD:
```
 sudo update-grub
```Sorry, I don't know if this will work from 7.10. Once you have everything working again, it might be an idea to get an up-to-date CD.

---

