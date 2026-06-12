---
title: "Shutdown problem on Netbook"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by XenoGuard on 2010-07-16
Hello,
 
I am wondering if anyone can help me with an issue I have on the Asus eee Pc 701 with Ubuntu Netbook 10.4
 
The installation went fine and at first I never had this issue but over the last few days I am unable to shut down or re-start the system without it hanging on the Ubuntu Splash Screen.
 
I have searched for this problem and found some things to try but so far, unless I am doing them wrong they have not helped
 
So far I have tried:
 
Editing /etc/init.d/halt & adding rmmod snd-hda-intel after do_stop
 
I have also tried adding rmmod snd-hda-intel to the end of the halt file in /etc/default and this did not help either.
 
Is their something I am doing wrong or missing? Or something else I can try.
 
Thanks.

---

### Post by XenoGuard on 2010-07-16
**_Update01:_**
 
Using FN+F2 on my webook turns off the Wi-Fi, however this causes the OS to freeze, I held the button down to shutdown and on a re-boot the Wireless was still off,
 
After loading Ubuntu, I immediately clicked shutdown and it worked.
 
However I cannot turn off wireless before shutting down each time because the system freezes.

---

### Post by XenoGuard on 2010-07-16
**_Update02:_**
 
I believe I have found the fix - 
 
It appears I adding the line slightly wrong into the halt file.
 
**rrmod snd-hda-intel.**
 
I have added this and done a few shutdowns after this and so far has worked everytime.

---

