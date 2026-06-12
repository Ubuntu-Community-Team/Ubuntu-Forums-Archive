---
title: "Internet Connection Status, wvdial"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by thelazytech on 2008-02-10
I configured my ubuntu to connect to internet through my nokia n72 and its working fine. When I click the launcher on the panel to run wvdial, though my system gets connected to the internet and I am unable see the status until I go to the terminal and ping any IP. Is there a way I can setup something like we have in windows (two computers blinking in system tray). That will be helpful in seeing the status as sometimes the connection drops and I never know until any error in download comes or I again have to go to the terminal and see the ping.

Any help in this regard will be highly appreciated. 

Thanks in advance.

---

### Post by soro2005 on 2008-02-10
You could use gnome-ppp (as a graphical frontend to wvdial) or kppp to connect. For some reason, kppp works much better on my machine, but you might need somde kde dependencies to use it. Which you may not want to clutter your computer with.

Gnome-PPP should be installed on your system if you use Gnome. It's in Applications --> Internet.

---

### Post by thelazytech on 2008-02-11
Thanks, I will try that as soon as i am back there on ubuntu. :)

---

### Post by soro2005 on 2008-02-12
Btw: I also have an applet called "Modem Monitor" in my Gnome panel applets (right click on a panel --> "Add to Panel"). Not sure it's any good, I'm not really using the modem...

---

### Post by thelazytech on 2008-03-05
I have also faced one more issue with wvdial. All of a sudden the connection gets disconnected and then when i try to reconnect i get error that the device is not available though when i do lsusb i see my nokia phone connected there. After this i had to restart my computer so that the device is available again to be used.

regrards,

---

