---
title: "nvidia issues for fresh 8.10 install (i think)"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by dobbsjr on 2008-12-23
ill try this one again. any help is greatly appreciated. im pretty new to linux so here are my issues...

i recently bought a new MB and a new HD. i did a fresh .iso install of 8.10. the only expantion card i have in the MB is the GEForce 9400 GT. after an hour or so of random surfing the audio stops and video (including flash) only plays about 2 seconds worth. if i restart FF  it no longer responds and i have to do a force quit, and restart the system to start over. im tired of rebooting every hour or so. any ideas?

ps....this is the terminal output for a request from earlier....

this is the terminal output

d@d-desktop:~$ sudo lshw -C display
[sudo] password for d:
*-display
description: VGA compatible controller
product: nVidia Corporation
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia

---

### Post by jimmy the saint on 2008-12-24
when firefox stops responding see if there is a process called npviewer.bin.  if there is, right click and kill it.  If you have the same issue as me, it should solve your problem instantly.  The only caveat is that you have to do it every time.

---

### Post by dobbsjr on 2008-12-24
> **jimmy the saint said:**
> when firefox stops responding see if there is a process called npviewer.bin.  if there is, right click and kill it.  If you have the same issue as me, it should solve your problem instantly.  The only caveat is that you have to do it every time.
i know how you can check processes w/in terminal but when can you right click as you mentioned? ctrl-alt-del (which i assumed probably mistakenly) just switches user....

---

