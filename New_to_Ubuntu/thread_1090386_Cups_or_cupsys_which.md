---
title: "Cups or cupsys which ?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-03-08
I have not had much luck with my requests for help after losing connection with my HP 3822 printer since doing an update , so I will have to try myself. Firstly I seem to have both cups and cupsys in my /etc folder , but as neither show up in admin/services I can't activate either so all I get is cups scheduler not running and I can't connect with local host 631 .
Should I uninstall either cups or cupsys , and try to reinstall if so which? It was all working perfectly before .

---

### Post by Dr Small on 2009-03-08
Try starting cups and see if it exists:
```
sudo /etc/init.d/cupsys start
```

---

### Post by ex-wirecutter on 2009-03-08
Thanks for your reply ,no I tried this before , it just keeps coming up not found .
The cups folder is still there as is the driver for my printer. I have tried cupsd.config , and service cups restart , and just about everything else , just wondering if I have two conflicting systems , cups and cupsys ?

---

