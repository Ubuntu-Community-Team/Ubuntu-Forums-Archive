---
title: "i need to add a domain name"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by jimbean on 2007-03-04
i cannot download any updates 
i cannot use evolution email
i cannot use synaptic
if i dont install a domain name 
what is the best domain
to put in network settings

---

### Post by gradedcheese on 2007-03-04
You mean DNS settings?  Try this, open (with sudo) the file /etc/resolv.conf and edit it so that it contains:

```

search opendns.com
nameserver 208.67.222.222
nameserver 208.67.220.220

```

That will set you up with the opendns service, which should work fine.  Save the changes, close the file, and then try using the internet...

---

### Post by jimbean on 2007-03-06
thanks for the reply
 but i used ubuntu.com and i am a happy camper
i believe i fixed it but if u see a problem please type back

---

### Post by gradedcheese on 2007-03-07
> **jimbean said:**
> thanks for the reply
 but i used ubuntu.com and i am a happy camper
i believe i fixed it but if u see a problem please type back

please explain to me what you're talking about :)

...setting your host name?  setting up DNS (as above)?  what does ubuntu.com have to do with anything?

---

