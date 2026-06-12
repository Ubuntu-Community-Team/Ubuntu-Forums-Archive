---
title: "Change network location via command line"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by mikec13 on 2007-06-25
Does anybody know if there is a way to change my network location via command line?  I've got two shell scripts set up already to change my xorg.conf file depending on if I'm plugged into my external monitor at my desk, or just to use the laptop screen, but I'd like the script to switch network locations as well.

Thanks!

---

### Post by Maxtorm on 2007-06-25
Not sure if it's the most efficient method, but I do this using two copies of the /etc/network/interfaces file.  Set Ubuntu up for your first network, then copy the interfaces file into your home directory as, for example, interfaces.network1.  Set it up for your second network, and do the same thing using a different file name; for example, use interfaces.network2.  When you want to switch between networks, copy the appropriate interfaces.networkX file into the /etc/network folder as "interfaces" and restart the network (either using ifdown and ifup on the appropriate interface or by using "sudo /etc/init.d/networking restart").  You could also build intelligence into the script so that it would switch between network setups without you having to specify which.

---

### Post by mikec13 on 2007-06-25
Thanks!

---

