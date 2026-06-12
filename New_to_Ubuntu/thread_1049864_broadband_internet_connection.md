---
title: "broadband internet connection"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by tushar88 on 2009-01-25
how to connect to internet in ubuntu 7.10 .

---

### Post by anewguy on 2009-01-25
With what?  Hard-wired to a router?  Wireless?  Need a lot more information.

Also post back the output from the following:

- open a terminal window (applications/accessories/terminal)

- type:

lspci <press enter>

This tells Ubuntu to list all know devices on the PCI buss.

- type:

lshw -C network <press enter>

This tells Ubuntu to list all hardware, but to filter out everything except network devices.

Post all of that back here, as well as a much better description of how you are trying to connect and to what type of broadband adapter, and we might be able to help.

dave :)

---

