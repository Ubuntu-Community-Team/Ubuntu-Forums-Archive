---
title: "Problem installing nmt450 d-50 usb-modem"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by bldninja on 2007-11-30
staale@inspiron8600:/media/cdrom0/linux$ sudo ./rdevchg
Password:
RDEVCHG Linux Version : 1.0
Please, Wait!
Bus 001 Device 005: ID 16d8:680a  
...
Success SwitchMode.
[B]*** stack smashing detected ***: ./rdevchg terminated
Aborted (core dumped)[/B]
staale@inspiron8600:/media/cdrom0/linux$ 

Anyone know why i get error "***** stack smashing detected ***: ./rdevchg terminated Aborted (core dumped)**"?

---

### Post by TooLboy on 2008-02-06
I have the same problem. Too bad..is it the software that abuses the usb or something?

---

### Post by TooLboy on 2008-02-06
Problem solved. Not so difficult as it seemed because you can ignore the error and it works, if you get the blue light blinking.

I used the gnome-ppp application (apt-get install gnome-ppp) and run as root. Otherwise it disconnected all the time, at least for me it did.

:guitar:

---

