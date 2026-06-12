---
title: "Need help with ubuntu network configuration please."
date: 2017-09-13
forum: Networking &amp; Wireless
---

### Post by avihaysh on 2017-09-13
Hy.
i do have a lil problem with my network configuration..
actually, i want to make a script, that can change the ip, gateway, netmask and dns1+dns2.
Ive already read all the posts and threads about scripts, but non of them works, or they just got an error.
this is how its gonna go down:
bash script thats allow to the user (me) only once (in the first start-up) to configure all the parameters that i mention before.

script will come up at the first running, ask for static ip, gateway, netmask, dns1+dns2.
when i'll enter all that info, it will configured it with my input, make a restart to the machine, and never come-up again.

yeah, its sound simple, but ive looking for it for weeks in the web in a ton's of forums, this is my last shot.

you can wright me also a message in private.

THANK YOU FOR HELP!

---

### Post by TheFu on 2017-09-14
Welcome to the forums.

For wired connections, this is trivial.  Create multiple "interfaces" files with whatever settings you want, then a script can copy the one you want into the real /etc/network/interfaces file and restart networking.  If the network config isn't complicated - no bridges - then the restart should **just work.**  OTOH, my bridge configs have caused systemd much confusion, so it was necessary to bring down the bridge and network devices, then bring them up and finally the bridge in reverse order.  This wasn't an issue before systemd was added in 16.04. 

For wifi connections, it is harder, so I just use wicd-curses to handle different wifi stuff.

---

