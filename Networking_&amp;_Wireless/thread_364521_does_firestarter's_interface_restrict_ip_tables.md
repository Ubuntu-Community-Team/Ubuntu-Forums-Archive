---
title: "does firestarter's interface restrict ip tables?"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by TomFumb on 2007-02-18
Hopefully this is a quick and easy question but I can't find information elsewhere in the forum

When I configure firestarter, I have to choose an interface to configure. Does this mean that ip tables are then only configured for that interface? I often switch between wired and wireless and I want to be sure I'm covered. 

thanks for any information

---

### Post by koenn on 2007-02-18
> When I configure firestarter, I have to choose an interface to configure. Does this mean that ip tables are then only configured for that interface?

yes

it is sometimes easier to use ip addresses / ranges i.s.o. interfaces to avoid this, bit I don't know if firestarter can do that

---

### Post by TomFumb on 2007-02-19
thanks, 

so if I configure firestarter for eth1 and then for eth0, will ip tables only be configured for eth0?

---

### Post by koenn on 2007-02-19
no, 
the rules you set for traffic via eth0 will apply to traffic going through eth0, 
the rules you set for traffic via eth1 will apply to traffic going through eth1, 

- at least, when you write an iptables script. But I suppose all firestarter does is write that script for you after you've checked a couple of check boxes, so it should work the same way.

---

### Post by TomFumb on 2007-02-19
Ok thanks a lot for your help, I'll sit back and trust in my firewall.

---

