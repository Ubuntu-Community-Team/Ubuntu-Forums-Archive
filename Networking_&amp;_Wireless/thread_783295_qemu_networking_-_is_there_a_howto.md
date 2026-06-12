---
title: "qemu networking - is there a howto?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2008-05-05
hi,

i have installed ubuntu hardy and qemu and kqemu. i have created a couple of VM and i am now looking to find out how network these machines.
i used qemulator to create my VMs, and i do understand how TAP connectors work.
i suppose in future GUI applications for qemu will provide a more user-friendly interface for working with their networking but for the moment it is necessary to do it manually.

many thanks for all assistance.

regards,


Nicolas

---

### Post by chewearn on 2008-05-06
Here:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by nicolasdiogo on 2008-05-08
Thanks,

i have followed the information on that page but it now causes troubles when i suspend my laptop.
i believe the problem is to do with the bridge interface that i created on the /etc/network/interfaces.

would there be anything that i can do to setup the networking for VMs on a laptop?


Many thanks,


Nicolas

---

### Post by chewearn on 2008-05-08
Yeah, I just remembered, running kvm module causes suspend problem.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/113038](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/113038)

Workaround:
Instead of adding kvm into /etc/modules (so it's permanently loaded), use modprobe to load and unload the module as needed.

EDIT:
Networking part is complicated thing, but it's possible.  The howto gives a comprehensive instructions, but you will need to read carefully and thoroughly understand the options.

---

