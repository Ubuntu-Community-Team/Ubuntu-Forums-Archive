---
title: "Hibernate/Suspend mode for HTTP Server"
date: 2015-06-12
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-06-12
Hello!
                              I wonder if web server ever goes to sleep  (hibernate/suspend mode)? And if a visitor's browser asks for a web  page, then the web server immediately wakes up? Is it really an option  or pure fantasy? 
                              The reason why I'm asking... I don't know  how big should be swap file. Generally the system never uses it (no  need!). But if the web server would go to sleep, then it's different...

---

### Post by ajgreeny on 2015-06-12
That is exactly what **Wake-On-Lan** is for, as far as I'm aware, which you will have to enable in the machine BIOS/UEFI.

You need hardware that enables WOL to be set-up, and then, of course you need to configure WOL, which I have never done, so I can't give you more detail of how it is best done.
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

### Post by papakota on 2015-06-12
Thanks for your reply!
Well, I realize that it's different... WOL is a hardware feature and listening to port - software.

---

