---
title: "irc issues"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by needlez on 2007-07-15
i have a different issue i've never seen looking round google nothin never had this issue on any distro...
well usually when you use irc you need an ident server yet with ubuntu it seems to id me without an ident server. does ubuntu come with one by default because in synaptic i could not find any installed. thank you in advance hopefully someone knows.

---

### Post by needlez on 2007-07-15
ok after hours of time still no luck. im so lost. i installed oidentd. and well i believe it did not even use it.then after i remove still connected to irc. this is problematic to me no ident yet i connect..

*im starting to think i shoulda posted this in general help*

---

### Post by vrangforestillinger on 2007-10-03
Many servers lets you connect despite of not getting an ident-response. If someone runs a /whois request they will see (among other things) ~yourusername@foo.host.domain. The tidle appears when the server did not get a satisfactory ident response. At least, thats the case on the servers I've tried.

Ubuntu (desktop version)  does not ship with an ident-server preinstalled. Thats the security policy for Ubuntu, not having services such as ssh and ident running by default.

---

