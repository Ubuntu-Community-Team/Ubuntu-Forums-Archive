---
title: "ipw2200 lost after suspend"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by joepnaus on 2008-08-23
Network card lost after is accidentally closed the lit of my Dell Inspiron 6000??? What does a system do then - suspend, hibernate, go to sleep? Well my labtop never returned fine after the break.

Never the less, I'm stuck with malfuntioning wireless adapter.

I'm a novice when it comes to Ubuntu in combination with wireless. After done some surge on the forum I come up with.

$ lshw -C network:  
....
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3

Thus no logical name and there seems no driver to be installed???

What is wrong. System of course rebooted

$ lspci 
last line reads:
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

There is a network card found.

System log reads that after lit has been closed:
Aug 23 19:29:44 joep-laptop kernel: [68689.599683] ACPI: PCI interrupt for device 0000:03:00.0 disabled

Can anyone help me out please?

---

