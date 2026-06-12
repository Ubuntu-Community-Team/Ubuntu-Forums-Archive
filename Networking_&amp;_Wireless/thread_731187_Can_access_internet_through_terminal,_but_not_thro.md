---
title: "Can access internet through terminal, but not through browser"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Locutus_of_Borg on 2008-03-21
Wrong forum, but the people here seem more ready to assist that at Gentoo forums, but..I have a fresh install of Gentoo kernel 2.6.24 and just got my wireless working, well mostly working.  I can emerge from the terminal (gentoo's equivalent of apt-get) and can connect with pidgin instant messenger, but Firefox and Epiphany web browsers are unable to connect to anything.


I'd though at first it was /etc/resolv.conf so I copied the file form my ubuntu partition over, and no luck, same with /etc/hosts


when I upgraded 7.04 to 7.10 I had this same problem in Ubuntu, i fixed it somehow by running apt-get update && apt-get upgrade only then would firefox resolve any domain names

i tried an emerge --sync, which completed with no error, yet firefox still cannot reach any server


any ideas?

---

### Post by agurk on 2008-03-21
Can you wget a file from the terminal as well? Checked your proxy settings in Firefox and Epiphany?

---

### Post by Locutus_of_Borg on 2008-03-21
i didnt try wget

and I have no proxy settings at all.  I m using firefox now from ubuntu on the same computer, with seemingly the same settings, but I just saw a post about disabling ipv6 for someone in a similar situation.  i will try that.

---

### Post by Locutus_of_Borg on 2008-03-21
I cannot wget >> Network is unreachable

and disabling ipv6 did not help, at least i think i disabled it since i recompiled firefox with -ipv6 set in the use flag

pretty new to gentoo though.

---

### Post by agurk on 2008-03-22
I wonder if it could be DNS related, can you reach these forums on [http://91.189.94.186](http://91.189.94.186) ?

---

### Post by Locutus_of_Borg on 2008-03-22
oh i managed to fix it through about:config >> network.dns.disableipv6 set to true

---

