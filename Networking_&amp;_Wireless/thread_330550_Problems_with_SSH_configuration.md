---
title: "Problems with SSH configuration"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by oliver369 on 2007-01-03
I am having a problem with the configuration of my SSH (client I think). Basically I am using two machines with Edgy installed. I am able to connect with through the terminal and with putty to the distant PC however, when I connect through the terminal it closes the connection after about 150 seconds of inactivity.  > Connection to <host>:<port> closed by remote host..
With putty if I set the "Seconds between keepalives" to 1 it works with putty. Could somebody please help me do the same with the SSH configuration I have had a look around at the ssh_config files and tried out a few things without success...
Please help me!:(

---

### Post by Jussi Kukkonen on 2007-01-03
The option ServerAliveInterval should do what you want. Use it in ~/.ssh/config (*man ssh_config* should tell you more) or using the -o command line option.

---

### Post by oliver369 on 2007-01-04
Jussi,

This certainly seems to help by increasing it but it doesnt remove the problem it still disconnects after a certain period...

Thanks for your help!

---

