---
title: "VNC / Remote Desktop login"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by whouseswindowsanyway on 2008-04-16
Hi Guys, 

Sorry I'm new to these forums - I just need to get an answer - we are redoing our whole server system at work -- at last moving from Windows Server 2003 to Ubuntu -- we are at the moment testing some stuff on Ubuntu 7.10 - Now the thing is I need to install VNC on one of our servers,
what I need it to do is to :
Accept logins ( in other words the server shouldn't have to be logged in first ).
And if possible more than one login per time ( even if it is different users ).

I am not sure if these are possible with VNC - can somebody please help me with something else I can use - or if there is a way I can accomplish this.

Thanks in advance.

---

### Post by Pap3r on 2008-04-16
Yes, VNC can connect with multiple connections.  To install vnc and configure it, type ```
 sudo apt-get install vncserver xvncviewer
```

---

### Post by Bosk22 on 2008-04-16
VNC can be slow (very slow) and clunky you may want to look at NX by nomachine before going ahead with VNC

[http://www.nomachine.com/](http://www.nomachine.com/)

Faster, simple to install, works with Windows, Linux (any distro), allows multiple concurrent logons, file sharing, multimedia supprt etc etc etc etc


Regards

Bosk

---

### Post by whouseswindowsanyway on 2008-04-18
> **Pap3r said:**
> Yes, VNC can connect with multiple connections.  To install vnc and configure it, type ```
 sudo apt-get install vncserver xvncviewer
```

I have vnc server installed -- look the prob is that the server needs to be logged on for me to connect to it -- lets say the server restarts -- then i cant login with vnc --- i have to first go to the physical server log it in -- and then connect with vnc....

---

### Post by whouseswindowsanyway on 2008-04-18
> **Bosk22 said:**
> VNC can be slow (very slow) and clunky you may want to look at NX by nomachine before going ahead with VNC

[http://www.nomachine.com/](http://www.nomachine.com/)

Faster, simple to install, works with Windows, Linux (any distro), allows multiple concurrent logons, file sharing, multimedia supprt etc etc etc etc


Regards

Bosk
Thanx !!!!!! I will have a look at this!

---

