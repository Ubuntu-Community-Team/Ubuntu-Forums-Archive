---
title: "setup wired internet conne. in ubuntu 9.04"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by spt025 on 2010-03-13
hi there,,
i'm complitly new in ubuntu<u can say 1st standard>
i have internet connection of youtelecom<wired connection> & i want to setup internet connection in ubuntu9.04 which i installed inside windows jst a few days ago...
i'm not having any static ip add.
<i tried to set up net but i couldn't do much i tried to use those network manager things & went in dhcp type but still i'm nt gettin anythin>



plz plz help:)

---

### Post by karthick87 on 2010-03-13
Configure your internet connection by running this in terminal..

```
sudo pppoeconf
```

---

### Post by Chris_cur on 2010-03-13
> **spt025 said:**
> hi there,,
i'm complitly new in ubuntu<u can say 1st standard>
i have internet connection of youtelecom<wired connection> & i want to setup internet connection in ubuntu9.04 which i installed inside windows jst a few days ago...
i'm not having any static ip add.
<i tried to set up net but i couldn't do much i tried to use those network manager things & went in dhcp type but still i'm nt gettin anythin>



plz plz help:)

Give this a try:
System>Administration> Users and Groups > Unlock > Select your user> Properties> Select User Privileges tab> make sure that "Connect to Internet using Modem is checked.

Also, if you are the only user and you feel your computer is secure enough, I would go ahead and check the others that you wish to apply.

Hope this works.

---

### Post by Chris_cur on 2010-03-13
Any luck, friend?

---

### Post by spt025 on 2010-03-14
hi frnd your trick worked but still in network connections i am disconnected but i can access internet 
...................
new problem is that i dont know how to terminate this connection via terminal so plz rply as soon as possible.............................
thnk you in advance

---

### Post by 110south on 2010-04-08
I tried the sudo pppoeconf and received the following message:

Not Connected

Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

1. Does this mean another computer connected to the same line must be disconnected first?

2. There is definitely no problem with the incoming provider connection as this is a dual boot with Vista and it works fine on that OS.

I would appreciate any help (have tried many things, including the other above listed items)

---

