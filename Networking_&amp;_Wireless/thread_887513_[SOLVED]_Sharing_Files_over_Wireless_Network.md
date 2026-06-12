---
title: "[SOLVED] Sharing Files over Wireless Network"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by getitright on 2008-08-12
I am trying to establish a home wireless network in order to share files between computers. I have tried right clicking a folder and going to Share Options, a la Windows, but get the following message.


'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

How can I proceed from here.

---

### Post by kjyoder on 2008-08-12
Just pop open terminal and run> sudo nautilus

that will open nautilus with root access and you can add permissions/whatever you need to do from there

---

### Post by kjyoder on 2008-08-18
Or, even better, run ```
gksu nautilus
```

---

