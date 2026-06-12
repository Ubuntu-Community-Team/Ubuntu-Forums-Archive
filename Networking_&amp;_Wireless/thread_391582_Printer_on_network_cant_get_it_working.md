---
title: "Printer on network cant get it working"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by mpooley on 2007-03-23
Hi all
Not sure if this is the right place to ask but i am a new user of linux and am trying to set up my printer which is a HP deskjet  980cxi attatched to usb port on my US robotics router.

I have tried following all the setup instructions i can find and all of the different drivers but nothing works!

I can get it working easily as a straightforward USB printer BTW

so in desperation i am trying to set it up from a KDE desktop and this is asking me not only for the printer address but a port number?  
the ip address is htttp:/192.168.2.1:1631/printers/My_Printer  (and no the 1631 is NOT a typo)  but how can i find the port number please?


thanks

Mike

---

### Post by ffxr on 2007-03-23
you've confused me a little but i beleive your printers address is htttp:/192.168.2.1/printers/My_Print & its port number is 1631

---

### Post by chili555 on 2007-03-23
Isn't the correct port for a printer 631? I would try:```
http://192.168.2.1:631/printers/My_printer
```Maybe KDE knows something I don't. Always a possibility!

---

### Post by mpooley on 2007-03-23
> **chili555 said:**
> Isn't the correct port for a printer 631? I would try:```
http://192.168.2.1:631/printers/My_printer
```Maybe KDE knows something I don't. Always a possibility!

No Honestly :)   I have tried that before and the router is quite definite that that is the address of my printer -- It also works ok on XP using that address?

---

### Post by doncristobal on 2007-07-08
Maybe this might help: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)
It's how i finally solved a very similar problem. 

Good luck!

---

