---
title: "wireless"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by ti479 on 2007-07-08
hello i am new to this forums and  linux as well. i have a dell 1505 laptop that uses the ipw3945 driver for my wireless. now i have downloaded the driver but have absolutely no idea how to compile it to make it work.

i have looked around for a precompiled version to no avail and i really just want a wireless that works. i am using ubuntu edgy because 7.04 wouldnt work.--it kept looking for a microcode bm43xx or something like that.

can someone please tell me how to fix this? i mean i am not a huge fan of microsoft but at least it works! and so
far i am batting 0 here with linux.

scott

[email]ti479@yahoo.com[/email]

---

### Post by fredj on 2007-07-09
Open a terminal, (go to Applications - Accessories - Terminal).
Type 'sudo lshw -class network' (without the quote marks), enter your password 
and hit return.
Post the output from that here. In general you shouldn't need to install 
a driver for your Intel wireless chipset.It should be detected automatically.

---

