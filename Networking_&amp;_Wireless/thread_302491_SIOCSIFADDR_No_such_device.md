---
title: "SIOCSIFADDR: No such device"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by crisis_davis on 2006-11-18
I have just installed edubuntu on a rather old machine, all works well except for network card.  I have no idea on how to get it going.

tried the following:

ifup eth0
I get SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: NO such device

ifconfig -a 
gives me l0 and sit0

any help adding this NIC would be greatly appreciated,
thanks

---

### Post by crisis_davis on 2006-11-18
I found this:

sudo modprobe 3c509

not sure what it does but it worked,

thanks.

---

### Post by FrodoB on 2006-11-19
> **crisis_davis said:**
> I found this:

sudo modprobe 3c509

not sure what it does but it worked,

thanks.


Now you will need to add 3c509 to the /etc/modules file:

$ sudo gedit /etc/modules

just a single line:

3c509

Now it will always load the driver module for your card.

---

### Post by tiver on 2007-05-17
Hello!

I followed these steps but when booting again it takes 2 minutes to do so (!) and finally it brings up an error (attachment). 

It says (partially translated):


While starting of the GNOME configuring services an error occurred:

Maybe certain things like themes, sounds or background services do not function correctly. 

The last error message was:

Did not receive a reply. Possibly causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

On the next logon GNOME will go on trying to start the configuration service.



If I leave the line 3c509 in /etc/modules it does not connect to the network on startup but it loads fast. When I include the line it connects on startup but it lasts very long and it brings this error. 

What can this be?

I hope you can help me.

---

