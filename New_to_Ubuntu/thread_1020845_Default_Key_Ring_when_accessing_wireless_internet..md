---
title: "Default Key Ring when accessing wireless internet."
date: 2008-12-24
forum: New to Ubuntu
---

### Post by bluejay9109 on 2008-12-24
I'm some what new to Ubuntu.  I have 8.10, and when I wish to connect to my wireless network at home, I have to enter my password to access the default keyring.  Is there anyway to take this off so I can access wireless without having to type my password?

---

### Post by flanagan on 2008-12-26
I had this problem in Hardy (8.04) apparently due to a bug in the default network manager applet. Replacing the network manager with Wicd solved the problem: see [http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04).

I have another machine with a clean install of 8.10 and the default network manager works fine there. I suppose that the bug may have persisted if you upgraded from 8.04 to 8.10 (a possibility), but I would still recommend Wicd.

---

### Post by mrhorrible78 on 2008-12-26
I had the same problem too, but installing wicd seems to have solved it.  Thanks for the suggestion!  I like the interface much better.

---

