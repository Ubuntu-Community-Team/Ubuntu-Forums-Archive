---
title: "Please give me a solution for Authentication"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-09-29
Well, this is the requirement of the day at my office.
   I want a single Linux server box to have the database of all the users on  the LAN, and when a client tries to login from his computer, the username and the password are checked against those existing on the
main Server and then take him to his usual Home on his own computer..

Is this possible..if yes plz plz do lemme know..

I tried Samba PDC..but I got lost..

If u have a nice way of explaining it plz do so..
I can start afresh

---

### Post by wieman01 on 2006-09-29
Are you referring to authentication before users log on to the network (network authentication) or only for SAMBA (server authentication) while they are already part of the network?

For wireless network I would suggest **WPA2 with EAP**... aka **"Extensible Authentication Protocol"** which enables you to ask for username & password before users log on.

---

### Post by hellmet on 2006-09-30
> **wieman01 said:**
> Are you referring to authentication before users log on to the network (network authentication) or only for SAMBA (server authentication) while they are already part of the network?

For wireless network I would suggest **WPA2 with EAP**... aka **"Extensible Authentication Protocol"** which enables you to ask for username & password before users log on.
well , I am talking abt network authentication..i hope..

Its like I want the server to authenticate the users rather than the 
local client's system...
and then bring him to his own hard disk

---

### Post by hellmet on 2006-09-30
SAMBA PDC gives me this error when access from Win2K..

see attachment

whats wrong??

---

### Post by mips on 2006-09-30
So you want samba to act as a domain controller for the windows pcs ?

Maybe have a look at [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

