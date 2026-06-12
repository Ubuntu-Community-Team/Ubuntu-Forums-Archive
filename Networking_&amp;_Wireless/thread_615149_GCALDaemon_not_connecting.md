---
title: "GCALDaemon not connecting"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Maverickprowls on 2007-11-16
Not a request for help, but more passing on a lesson I've just learned.

Anyone trying to run GCALDaemon and presented with the message

[INDENT][INDENT][COLOR="Blue"]ERROR | Unable to load contact list!
net.sf.gm.GMException: Error in getContacts --> Not Connected[/COLOR]
[/INDENT][/INDENT]

I spent about half an hour trying to track down some help on this issue before I actually sat and had a think about it and checked my configuration.

GCALDaemon doesn't tell you that its failing for a bad password or username, Simply put, check your config files for typos.  I had mis-spelt my username, but it's just as easy to copy and paste the password incorrectly.  

Hope that helped someone.

---

### Post by onlineapps on 2007-11-17
I'm getting the same error, but I'm not misspelling my username or pw.  Maybe I'll try reinstalling with a clean config file...

---

