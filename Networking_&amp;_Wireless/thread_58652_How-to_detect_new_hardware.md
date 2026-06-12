---
title: "How-to detect new hardware"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by winksaville on 2005-08-21
Hello,

I've added a new network card, a GA302T from netgear, to an existing install of 5.04. It was not automatically detected, so I searched the net and it appears that I should install tg3 (Tigon3 driver). I tried "modprobe tg3" that loaded the module but it doesn't appear as ethX after exectuing "ifconfig"?

What do I need to do to either have it automatically detected or manually install the driver?

Thanks,

Wink

---

### Post by nad on 2005-08-21
Add the module name to /etc/modules to have it loaded at startup.

Once you have installed the driver manually, you may: tail /var/log/messages (dmesg | tail) to read any system messages. If your system now recognizes an ethX device, you may: /etc/init.d/networking restart  to bring your network interface up (or if you know your device designation: ifconfig ethX up ).

---

