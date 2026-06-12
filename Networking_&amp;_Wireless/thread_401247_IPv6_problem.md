---
title: "IPv6 problem"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by SikEnCide on 2007-04-04
ok so here is the deal.. i have tried the dirrection on here

[https://help.ubuntu.com/community/We...ngSlowIPv6IPv4](https://help.ubuntu.com/community/We...ngSlowIPv6IPv4)

when gedit comes up with the files i am suppsoed to edit there is nothing in them.
i am using ubuntu 6.05

and it wont connect ot the internet because its using IPv6. i disabled it in firefox now i just need to do it on the system and it wont work..

i manualy found the files and tried to edit them but it would not let me save them.

---

### Post by chili555 on 2007-04-04
In a terminal, type:```
sudo gedit /etc/modprobe.d/blacklist
```Is the file empty? If so, you have mis-typed the command some way.  Close and try again.

If it is not empty, type, on a new line, at the end:```
blacklist  ipv6
```Save and close gedit. You will have to reboot for it to take effect.

---

### Post by Kobalt on 2007-04-04
To disable IPv6 you should enter this command line 
```
gksudo gedit /etc/modprobe.d/aliases
```
find the following line 
> alias net-pf-10 ipv6
and make it look like this 
> alias net-pf-10 off ipv6
Save & close, and finally reboot.

---

### Post by SikEnCide on 2007-04-04
ok well i can connect through my wireless connection, but hte lan still wants ot us ipv6 i think.. i did both those things and restarted it still wont work.:mad:

i did remember reading to comment out the

alias net-pf-10 ipv6

part.. instead of the off being in it.
think that could be it ?

---

### Post by SikEnCide on 2007-04-04
nevermind my last post.. everything seems to be working now. thank you for your help and timely response.

---

