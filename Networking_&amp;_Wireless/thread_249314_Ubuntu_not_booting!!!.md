---
title: "Ubuntu not booting!!!"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by DavidCar on 2006-09-02
Hi!
I have a problem with my network; I have two inteface, a Wi-Fi card and a Ethernet connection, the last time I logged into Ubuntu I set both of interfaces "active" and now my system is not booting by anyway, it stops somewhere in the Init processes, the last line says that there was some kind of problem with the ndiswrapper and something like "abnormal exit in process blabla".
I think I can solve this if I deactivate one network interface, but I can't even get a shell and I don't know which configuration files edit, so any suggestion or help would be very very useful!!!:D 

Thanks.

---

### Post by Stone123 on 2006-09-02
Boot in single mode(recovery ). Then you might try startx , if not that then  
vi /etc/network/interfaces

Press i for input /edit .
# <- coments out  a row . 
# iface wlan0 auto 
 
press : 
then type wq

---

### Post by DavidCar on 2006-09-02
Hi!
I can't enter even the recovery mode...](*,)

---

### Post by Uluen on 2006-09-03
Try pressing CTRL-C repeatedly when it's loading drivers, see if you can get it to finish booting that way, then do what Stone123 said.

---

