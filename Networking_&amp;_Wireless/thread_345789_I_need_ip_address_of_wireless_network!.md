---
title: "I need ip address of wireless network!"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by yosef on 2007-01-24
I am trying to help my friend secure his wireless network, but he changed the ip address of the router and doesn't know to what.  He remembers the passwords and everything so if I can just get the ip address we can do it.  I can connect to the network with my laptop, what command can I enter to see what the ip address is?

---

### Post by Daveski on 2007-01-24
```
ifconfig
```

and 

```
route
```

should do the trick if you have connectivity. This should show your IP address and the default gateway will be the address of the router.

---

### Post by yosef on 2007-01-24
Great!  That did the trick!  Thank you very much!
:guitar:

---

