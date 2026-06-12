---
title: "Wireless problem"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by Boule on 2007-04-17
Hi,

I'm having a problem with network manager (edgy). When I wake up my laptop from stand by mode, it doesn't reconnect automatically, and when I click on the network manager icon to connect manually, it says "no network hardware detected". And since my network adaptors are disabled in order for them to be handled by nm, I can't "down/up" them, the only thing that's working is signing in again, which can be rather annoying !!

Any ideas on why it's happenning, and how to fix it ?

---

### Post by leibowitz on 2007-04-17
That's related to the suspend mode (acpi, apm or whatever). 

It has been hard to handle those things, but apparently (from what I have read) it's even harder to handle this in the kernel modules (ie the drivers). That means often drivers are broken (related to acpi/suspend resume behavior). It's not clear what they should clean (in term of memory... or ... no that's my memory that don't remember that part of the story) after resuming.

Don't expect your computer to handle this tomorrow, so don't ask me anything about today.

---

