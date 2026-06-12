---
title: "virtualbox networking question"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by -Outlaw- on 2011-05-10
H
Can you have a vm in dmz?

Ive installed Damn Small Linux VM and would like to put it in my DMZ. Is that pobbible or not?
I would like it to have a static ip of 192.168.0.200 if someone would like to instruct me on that too.

Any help would be appreciated.

---

### Post by taseedorf on 2011-05-11
Sure you can.  Just make sure that your vm DOES NOT use a NAT and have it on the subnet you want....

---

### Post by -Outlaw- on 2011-05-11
> **taseedorf said:**
> Sure you can.  Just make sure that your vm DOES NOT use a NAT and have it on the subnet you want....
Thanks for the reply

Do i set the static ip in DSL-VM or on the Host machine? and then set the VM to DHCP?

I have it bridged to the host adapter at the mo

---

