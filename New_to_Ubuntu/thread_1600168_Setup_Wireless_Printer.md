---
title: "Setup Wireless Printer"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by Al_is_venting on 2010-10-18
Hey guys sorry to bring this back from the dead, but how can i setup wireless function of this printer?

---

### Post by cariboo on 2010-10-18
Moved to a thread of it's own.

We need more info in order to answer your question. What make/model printer are you trying to setup?

---

### Post by Al_is_venting on 2010-10-18
You're making it sound like i did something wrong, the printer info was on the post i replied to.

Printer is an HP F-4580. 
 I have no problem hard wiring it but i don't know how to utilize the wireless function.

Thanks for any help.

---

### Post by Temposs on 2010-10-18
First thing to try is:

```
sudo hp-setup
```

Then choose the option to scan for wireless capability. Make sure to plug in the printer when it says. 

If it is unable to find your printer by that method, then you need to find the IP address of your printer. If you have a printer with a display(which you probably do, since yours is an All-In-One printer model), then you may be able to get the IP address on there. When you have the IP address, go to System->Admin->Printing, click Add, then choose AppSocket/HP DirectJet. Type in the IP address(should be something like 192.168.X.X), then click Forward, and see if it works :-)

---

### Post by lucykhloe on 2010-10-19
If you have a printer with a screen so that you may be able to obtain the IP address of the existence . Once you have the IP address, go to System-Administration-Printing, click Add, then select AppSocket / HP DirectJet. Type the IP address it seems like 0.0.0.0 then click Next and ok.

---

