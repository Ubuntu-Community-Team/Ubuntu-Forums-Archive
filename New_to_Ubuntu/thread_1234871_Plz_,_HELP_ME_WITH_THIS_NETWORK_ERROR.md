---
title: "Plz , HELP ME WITH THIS NETWORK ERROR"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by gprateek on 2009-08-08
**THERE ARE TWO VERY BIG PROBLEMS I AM FACING CURRENTLY:**
 
_**1.**_
Please go through my problems:
I am connected to University LAN in HOSTEL. The IP addresses are assigned as 172.16.86.* and we connect to the internet by logging in the server.BUT sometimes , due to some disturbance in LAN , the IP address of some users(connected to LAN ports changes to type 192.168.0.* and inthis condition ,there is very limited access and SERVER cannot be connected. To remove this problem in WINDOWS , we manually change our IP Address to the earlier one and restart and the problem is fixed.
 
BUT , how to solve it in UBUNTU , also I would like to know more about this problem if anyone has experienced it and its causes+solutions. 
 
 
_**2.**_
I was trying to install from tar.gz type package and the following error occured when i was compiling ./configure ............ The package was GNOME IPMSG .Please have a Look at it:
 
>  
 
loading cache ./config.cache
checking what warning flags to pass to the C compiler... -Wall -Wunused
checking what language compliance flags to pass to the C compiler...
checking for pthread_create in -lpthread... yes
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: GTK not installed
prateek@prateek-laptop:~/DOWNLOADS/gipmsg-0.4.0beta1$
 

It seems that something called GTK was not found/available/accessable .
Pls help me with solving this problem.

---

### Post by Liolikas on 2009-08-08
1) read:
```
 
man ifconfig

```

2)
>I was trying to install from tar.gz 
Do not try this again use Synaptic.

---

### Post by superprash2003 on 2009-08-08
if you are asking on how to assign a static ip in ubuntu , then hopefully this should help [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by gprateek on 2009-08-09
Thanks for your information , but still the second mind is not that useful.

When I used the synaptic package manager , it could not install that . It couldnt recognice the package , however xipmsg was easily recognised by it. 

However I would like to install ipmsg as through it , files can also be transferred by within the LAN.
  
If you know any software which could transfer files also please tell me.

---

