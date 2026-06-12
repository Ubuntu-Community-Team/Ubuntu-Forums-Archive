---
title: "[SOLVED] What subsystems follow &amp;quot;allow-&amp;quot; in /etc/network/interfaces stanzas?"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by danduq on 2008-11-13
Hi,

I'm just playing with my network settings and have my wlan0 set to ifup automatically and get settings from dhcp;
```
auto wlan0
iface wlan0 inet dhcp

```
Around 95% of the time my wireless is disabled on my laptop (via the h/w switch on the machine itself) so I probably only want it to attempt to connect to the DHCP server when this switch is enabled, not when the system boots.

Reading the interfaces man page it says you can use an "allow-" stanza for various subsystems to be able to bring up the interface. Where can I find out what these subsystems are? The only examples in the man page are "allow-auto" and "allow-hotplug".

Am I barking up the wrong tree? Is there a better setting I should use?

Thanks.

---

### Post by danduq on 2008-11-17
bump

---

### Post by danduq on 2009-01-02
Don't really need this info now, and no-one seems to know anyway. Marking as solved.

---

