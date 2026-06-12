---
title: "Lan not working on dell inspiron 1545"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Gorgonkernel on 2010-01-08
Hey it seems like the problems keep following me. I connect to the internet using a lan cable. I configured pppoe in the terminal using sudo pppoe..everything works fine for 1 minute or so and then I get if I type plog in the terminal "Jan  8 10:32:53 flopgeek-dell pppd[16269]: Connection terminated.
[16269]: Modem hangup
[17077]: No response to 4 echo-requests
[17077]: Serial link appears to be disconnected.
[17077]: Connect time 2.5 minutes.
[17077]: Sent 49219 bytes, received 0 bytes.
: Connection terminated.
 Modem hangup
What can I do? This problem is really anoying...

---

### Post by mikewhatever on 2010-01-08
MTU (minimal transfer unit) can be the problem. You can change it in the network manager settings, but first try asking your ISP about the correct value. Searching for your ISP + mtu might also help.

---

### Post by Gorgonkernel on 2010-01-09
I have received the mtu number but where exactly do I go to write it? Thanks for your reply!

---

### Post by mikewhatever on 2010-01-09
Right click on the network manager in the top panel, select 'Edit Connections', select your connection and click 'Edit', MTU value is in the leftmost tab, set to 'automatic' by default.

---

