---
title: "network settings dont stick"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by drtvasudevan on 2006-08-03
with great difficulty i figured out what should be the network settings to get the updates without problems.
the problems is that it does not stick.
every time i have to redo the settings and click ok.
what do i do to keep the settings?
:confused:

---

### Post by ciscosurfer on 2006-08-03
Please be more specific.

---

### Post by mips on 2006-08-03
[http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)

---

### Post by drtvasudevan on 2006-08-04
> **mips said:**
> [http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)

i have seen this thread.
during installation i configured network settings with dhcp.
found that updates dont work with that.
changed settings to manual> entered values.
still wont work.
after more search i found i missed mentioning the domain name under the general tab.
entered that and i can now update.
the problem being on booting i find that the values are not in the settings.
i have to enter all the values again.

how do i make the changes to keep the settings?

i have edited the /etc/dhcp3/dhclient.conf THIS WAY:

prepend domain-name-servers CDL01;

(this was given by my service providerfor win 98 )
also
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope; 

as given in the thread.

---

### Post by drtvasudevan on 2006-08-05
someone please reply.....

---

