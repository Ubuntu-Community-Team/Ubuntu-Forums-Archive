---
title: "Firefox Defaults to Offline mode - Make it stop"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by crjackson on 2009-06-14
Okay, here's the deal. I built a system for an old friend of mine (2K miles away).

The system is dial up and after several weeks he can finally connect and login to his provider.

The system is running Jaunty and firefox.

Now the problem:

After he makes connection and launches, Firefox is ALWAYS in offline mode. He then goes to the File menu and unticks the offline setting and it works.

HOWEVER...

Every time he launches Firefox it has reverted to Offline mode. Is this due to not having a broadband connection?

How can I make this thing open in ONLINE mode?

Thanks

---

### Post by ChaiTan on 2009-06-14
type about:config in the url bar of firefox and modify toolkit.networkmanager.disable to true.

---

### Post by crjackson on 2009-06-14
> **ChaiTan said:**
> type about:config in the url bar of firefox and modify toolkit.networkmanager.disable to true.

Okay, I'll see what happens.  Thanks

UPDATE:

Thanks ChaiTan - That fixed the issue...=D>

---

