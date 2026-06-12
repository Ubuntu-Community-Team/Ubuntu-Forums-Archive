---
title: "How can I prevent a user from accessing an specific network interface?"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by legolas_w on 2009-09-04
Hi
Thank you for reading my post, can someone please let me know how I can prevent a user from accessing an specific network adapter (interface)?

My computer has two network interfaces and I want to make sure that second user has no access to that interface.

Thanks

---

### Post by Old_Grey_Wolf on 2009-09-04
I'm not going to be online very long before going to sleep.

Some more information may be needed before someone can help you. Such as, are you using wired or wireless connections?

---

### Post by cwsnyder on 2009-09-04
I think you are going to get your hands dirty with the command line in Terminal, if you are going to do what you specify.  This is not the type of thing the GUI was meant to handle.  For one thing, multiple network interfaces, unless they access different types of networks, are not normal outside of a router setup.

I think you can do what you want, but it will probably involve using setting permissions for the device, and I am not familiar enough with chmod and related commands to outline how to do it.

---

### Post by legolas_w on 2009-09-05
Hi,

Thank you for reply.
I am using both wired and wireless interfaces. 

Thanks.

---

### Post by Old_Grey_Wolf on 2009-09-05
> **legolas_w said:**
> Hi,

Thank you for reply.
I am using both wired and wireless interfaces. 

Thanks.

If the user does not have sudo privileges, then block the IP address in iptables.

---

### Post by Old_Grey_Wolf on 2009-09-05
> **Old_Gray_Wolf said:**
> If the user does not have sudo privileges, then block the IP address in iptables.

Thy this [http://ubuntu-unleashed.com/tag/block-user-internet-access](http://ubuntu-unleashed.com/tag/block-user-internet-access).

Edit: I think there is an error in the instructions on that page. I think it should be "--uid-owner" instead of "&#8211;uid-owner".

You can read about other iptables capabilities or understand the command at this site [http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables) easier to read than using man in terminal.

---

