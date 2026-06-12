---
title: "Ndiswrapper just stopped"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Invincible13 on 2007-02-16
I have a Broadcom Air Force wireless card and used the installer I found on these forums and it has been working for me, but recently it just stopped.  It can still scan for networks but it just stalls in the connection process and dies.  Is one of the recent updates interferring with ndiswrapper or am I missing something?

Keep in mind it worked for me when I closed my laptop last night, and tonight it doesn't.

---

### Post by gradedcheese on 2007-02-16
well, the latest kernel does break ndiswrapper, but I'm not sure that that's your problem.  Try:

```

sudo /etc/init.d/networking restart

```

to reload your interfaces.  Then check if it can still scan and then move to trying to associate and get an IP address.  You can also check if the driver is loaded:

```

lsmod | grep ndis

```

...should return something if the module is currently loaded.  If it's not, try:

```

sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart

```

---

### Post by Invincible13 on 2007-02-17
I tried what you said, it errors for me loading the wireless card and from what I've read online, the error ("Can't allocate interface elease { interface .") is related to the dhcp client, is there a fix for this?

---

### Post by gradedcheese on 2007-02-17
you can manually run dhclient:

sudo killall dhclient
sudo dhclient interface_name_here

---

### Post by Invincible13 on 2007-02-18
It didn't do anything for dhclient not working with my wireless:

```
sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Can't allocate interface elease {
  interface .
Failed to bring up eth1.
```

Not quite sure what this means...

Thank you for the help

---

