---
title: "DynDNS auto update dynamic ip?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2007-04-23
Is there a way to have my system automatically log into dyndns.org service and update my ip.  Sometimes my ip changes, and I have to manually update it.  However, sometimes when I am at work, I try to access my stuff and my IP has changed, thus my registered URL doesn't work.  Any Ideas?

I found this.  Will this work?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service)

Thanks for the help,
Hans

---

### Post by hansoffate on 2007-04-24
Bump

---

### Post by az on 2007-04-24
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ddclient](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ddclient)

There are other dynamic dns clients, too.

If you are using a router, your router should be the client, since it has the outside ip address..  Many routers have built-in clients for dynamic dns services.

---

### Post by arjanhs on 2007-12-29
I'm able to update my account with the router settings, but i'm using the MX record to, how will i be able to update this one to?

---

