---
title: "xhost +otherhost not working"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by snowsquirrel on 2005-08-26
I am trying to throw a screen from my Sun box back to my new ubuntu box.  I do a "xhost +sunhost", then from my sunhost do a "export DISPLAY=ubuntuhost:0.0 try to run an xapp.  But I get an error not able to open display.  I am assuming I have to enable something in some config file.  Does anyone know how to do this?  Do not give me a lecture on ssh or xauth, I just want to do it using good ol' xhost.  Thanks.

~S

---

### Post by s_p_a_r_k_y on 2005-08-26
/me has never used a sun box or you xhost. I'm not sure if this crowd of Linux users is old enuff to have tried running xapps on other hosts.

have you tried ssh? : ) How far away is the sunbox from the linux box or how bad is the latency I should ask. I would look up on google for more help on this topic

---

### Post by snowsquirrel on 2005-08-27
I have done this before, but I just forget how I set it up.
Both boxes are local, and both are behind a firewall, that is was wanting to export just raw X.  I know they are compatible, as I just tried using the kdm chooser, and was able to log into the sun box fine.  But I want to just throw back the odd screen.  I will try my search again on google.

> I'm not sure if this crowd of Linux users is old enuff to have tried running xapps on other hosts.   Agreed.  

~S

---

### Post by crashtest on 2005-08-27
Edit the file /etc/gdm/gdm.conf.  Find the line that says "DisallowTCP=true" and change it to read "DisallowTCP=false".

If it doesn't work immediately, restart the xserver, then you'll be fine.

---

### Post by patrick295767 on 2005-10-01
[QUOTE=crashtest]Edit the file /etc/gdm/gdm.conf.  Find the line that says "DisallowTCP=true" and change it to read "DisallowTCP=false".
If it doesn't work immediately, restart the xserver, then you'll be fine.[/QUOTE]


The idea is to do a rlogin on the remote pc via ssh
then on the local pc : to do xhost + sthg
then to do export DISPLAY=IP:0.0

but the result is similar , cannot find display... 


I dont know how it works .
that's rather strange cos with the previous distri of debian, that was possible to do so.. 
Or maybe I forgot sthg to enter on my pc ... 

I hope that the TCP willl works but I have rather doubts ... i hope ... 

If someone see the solution, please let us know !!

Thank you 

Patrick

---

### Post by patrick295767 on 2005-10-01
[QUOTE=crashtest]Edit the file /etc/gdm/gdm.conf.  Find the line that says "DisallowTCP=true" and change it to read "DisallowTCP=false".
If it doesn't work immediately, restart the xserver, then you'll be fine.[/QUOTE]


Hi, 

I tried your technology and ... 

It s not workign !! (i restarted xserver and so on).

---

It's normally very very easy :

on the PC1 : xhost + PC2

then:
rlogin PC2
export DISPLAY=IP_PC2:0.0
xclock &

and xclock should appear on the PC1's screen...


If someone knows the trick to make it, thank you very much !

Patrick

---

### Post by mlomker on 2005-10-01
> PC1 : xhost + PC2


Perhaps it is having problems resolving the hostname?  Try **xhost +** as a test.  That is not secure but a good test.

---

### Post by patrick295767 on 2005-10-01
[QUOTE=mlomker]Perhaps it is having problems resolving the hostname?  Try **xhost +** as a test.  That is not secure but a good test.[/QUOTE]


errata :
xhost + IP_PC2
I meant IP_PC2; I am using the IP adress (to be sure it works).

thanks for yoru comment !!

And result is : Display not found ... 

I also tried with xhost + 
and ... similar result : display not found

I dont know, and I was able to do it at school ... sthg changed maybe in the debian since few years ... 
I dont see 

Thx

Patrick

---

### Post by patrick295767 on 2005-10-01
:-) 
I just managed with xhost ...!!! 
Everything i wrote was right ... 
just we have to be very careful with the user !!!
it has to be the same as the x server running and rlogin and so on !
(i dont know if the trick disableTCP=false       helped actually)
(--- be careful with the users by doing a su USER ... )
Pat'

---

