---
title: "What is auth?"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by googlegot on 2007-10-15
What program is the "auth" service running under?  Its running on port 113, which i know is used for ident, but i cannot for the life of me find out what program it is running under

---

### Post by spd106 on 2007-10-15
I've never seen this before, it's certainly not there on a default install.

Try running this terminal command to see the process id associated with the socket.
```
sudo netstat -lp
```

---

### Post by noob12 on 2007-10-16
Well auth is another name for the ident service.  It usually runs within one of the inetd (inet-superserver) variants.

---

