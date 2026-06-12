---
title: "24 color depth with tsclient"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Taleman on 2008-05-26
I was wondering if there is any way to get 24 bit color depth while doing a remote desktop to a windows box?

---

### Post by Novus on 2008-05-26
check out the display tab.. I guess it'll not work if your target machine isn't set to 24 or more

---

### Post by Taleman on 2008-05-26
> **Novus said:**
> check out the display tab.. I guess it'll not work if your target machine isn't set to 24 or more

well the machine is set to 32 bit color. but when i set the color depth 24 in the display tab I get an error message that says 

> Remote desktop does not support colour depth 24; falling back to 16

---

### Post by Cosimix on 2009-07-16
Use **tsclient** instead of rdesktop...

Follow these steps:
1. _Enable VRDP_ on Virtualbox
if the machine is already running in the background (VBoxHeadless), run:
**VBoxManage controlvm** *vmname* **vrdp on**
else if the VM is not running, enable VRDP on Virtualbox > Remote Display
to test it on the cli type "**telnet** hostip 3389"
if you get connection Established you are ok 
else open tcp port 3389 on your firewall

2. run tsclient (gui application)
Use protocol version 5 (RDPv5) and change color-depth to 24bit.
**Note** When connecting use the host IP and not the guest's (VM's)

---

