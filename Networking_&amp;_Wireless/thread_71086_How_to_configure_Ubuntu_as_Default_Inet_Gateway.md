---
title: "How to configure Ubuntu as Default Inet Gateway"
date: 2005-10-02
forum: Networking &amp; Wireless
---

### Post by oragon on 2005-10-02
hello everybody! please help me to setup or give me a guide to install and setup a simple network. Im planning to make my Ubuntu connected to DSL to become my internet gateway (from a local network)

any help will be appreciated!!!

Thank you!

---

### Post by mlomker on 2005-10-02
I haven't set that up before, but I do know that you'll have to set the machine up to perform NAT.  Do a search on **firestarter**.


EDIT: Got my terms wrong.

---

### Post by cwaldbieser on 2005-10-02
[QUOTE=oragon]hello everybody! please help me to setup or give me a guide to install and setup a simple network. Im planning to make my Ubuntu connected to DSL to become my internet gateway (from a local network)
any help will be appreciated!!!
Thank you![/QUOTE]

In Firestarter: Preferences -> Firewall -> Network Settings -> Enable Internet connection sharing.

The technical name for this that you see a lot in the server world is NAT (network address translation), while for home use you normally hear it called Internet Connection Sharing.  Both are really the same thing.  I have tended to find more Linux-based material on the subject by searching for "NAT", though.

---

