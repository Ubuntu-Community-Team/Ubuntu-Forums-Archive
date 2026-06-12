---
title: "[SOLVED] How can I prevent creation of eth0:avah interface?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by The Cog on 2008-02-11
I don't need this interface, and we don't want extraneous IP addresses appearing on our servers. I can of course make firewall entries to block this address range, but I would rather just not have the interface created in the first place.

I have disabled the avahi daemon, and all my interfaces that I need have static addresses configured but this pesky avah interface still appears when I reboot.

---

### Post by hahahan on 2008-02-11
Yip, same problem here, I uninstalled Avahi with synaptic, that works nice.

regards.

---

### Post by The Cog on 2008-02-11
Thanks. 
You're right - uninstalling **avahi-autopid** does the trick.

---

