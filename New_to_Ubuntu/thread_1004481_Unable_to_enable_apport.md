---
title: "Unable to enable apport"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by banerjeerupak on 2008-12-07
I have gone through the wiki page on apport. However, i am still now able to enable apport

I gave the following command

*sudo nano /etc/default/appor*t

a set of command does come up. But i am unable to change the status to 1 from 0. How to go about it.

---

### Post by banerjeerupak on 2008-12-07
can someone just tell me how to change the enable to 1. 

i am getting stuck there.

---

### Post by lovelyvik293 on 2008-12-07
You can use the gedit instead of the nano which is much graphical and also easy to handle.
Use
```
gksudo gedit /etc/default/apport
```

---

### Post by banerjeerupak on 2008-12-07
Well it did work. I have made the changes. 
Lets see if apport starts functioning now. Got to wait till my first crash to finally know if its working.

---

