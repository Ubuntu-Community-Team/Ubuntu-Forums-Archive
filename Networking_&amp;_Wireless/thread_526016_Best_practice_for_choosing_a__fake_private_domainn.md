---
title: "Best practice for choosing a  fake private domainname"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by kentsin on 2007-08-15
When set up a new system, how to setup a fully qualified hostname? what private IP address?

The problem is : 

I (most people) do not have a domain name. Or case is they will connect to their company;s network, but they do not want to use that all the times.

From time to time, I need to connect to a corp. network, using cable. 

I want to connect to HOT SPOTs without giving out private information like corp domain name.

I also run some server apps which require a fake domainname, with a fix ip (not localhost) because I want to expose to others. This is bad because the corp network assign ip automatically.

I hope the above is common to all ubuntu users:

In choice of a fake root domain or a fake host with a real (dyndns) domain, what are the consideration?

What is the best practice to config in such conditions? Or are there any packages helpful?

---

### Post by ihristov on 2007-08-17
The default (commonly used) domain name when you don't really have one is localdomain

I believe after a default install your fully qualified host name is something like

  ubuntu.localdomain

---

