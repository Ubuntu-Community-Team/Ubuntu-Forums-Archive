---
title: "HELP: Changed eth1 to static IP for quicky file transfer, but now I got no internet!"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Remagen on 2009-10-18
So, I am connected to a DHCP connection.

But I needed to transfer 20+gigs of data between two computers, so I set them both to static IP's and put an ethernet cable directly between them.  

The transfer worked like a charm, but come morning, I plugged my computer back into the DHCP connection and tried to set it back to DHCP in nm-applet, only to get 'policykit authorization could not be created; invalid action id'.

Some debugging later, and now nm-applet won't even see eth1 (my adapter, no eth0)
dhclient finds nothing to renew itself with, and ifconfig says eth1 has no inet or inet6 address (but eth1:avahi does seem to have an inet addr).

How can I reset my adapter to be dhcp and get back to the internet? Or, failing that, how can I just totally reset my network settings to when I installed ubuntu?

---

### Post by yeats on 2009-10-18
> <snip>
so I set them both to static IP's
</snip>

Did you do this by editing /etc/networking/interfaces or somehow else?

---

### Post by Bucky Ball on 2009-10-18
System->Admin->Network, unlock, 'properties', 'Config: Auto-Config (DHCP)' instead of 'Static IP'?

---

### Post by Remagen on 2009-10-18
I used nm-applet on one computer and ifconfig on the one I'm having issues with now.

---

### Post by Remagen on 2009-10-18
> **Bucky Ball said:**
> System->Admin->Network, unlock, 'properties', 'Config: Auto-Config (DHCP)' instead of 'Static IP'?

The closest thing under admin, the closest thing is network tools
Under preferences, the closest thing is network connections, which is actually nm-applet.

---

### Post by Remagen on 2009-10-18
Man, I'm an idiot.

The Ethernet port in the wall has 2 ports on it, but apparently only one is wired in.

I just wish Ubuntu kinda pointed that out to me, instead of just... bah that was dumb.

---

