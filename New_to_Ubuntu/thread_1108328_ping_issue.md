---
title: "ping issue"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by ronin2307 on 2009-03-27
I am a total beginner so please bare with me.

I installed 8.10 as a VM on a Vista native host. No problems with the installation and everything seems to be running well out of the box. 
I would like to use RDP to establish connections to other windows machine from Ubuntu (this part works) and vice versa (this is where I am stuck)
Network description:
- office network
- all machines are on the same subnet
- ubuntu is getting valid IP info from a DHCP server (including gateway)
- from ubuntu I can go online and ping other windows machines on the network
- I cannot ping ubuntu machine from any other machine on the network (all windows)
- DHCP server indicates a valid and active lease for the ubuntu machine
- DNS server does NOT have an entry for the ubuntu machine

so obviously I cannot use the machine name for RDP yet (if anyone knows how to fix this, that would be great, since I don't know why the machine has not registered with DNS)
but I can't even ping the ubuntu machine. times out

so I tried to find some help online, but the best I could find was stuff related to firehol. I tried installing it and running it (with proper config changes) but it made no difference at all.


any help will be greatly appreciated as this time I am really trying to get a hang of Linux.

thanks

PS: iptables is not running. sudo service iptables status returns unrecognized service

---

### Post by mbzn on 2009-03-27
Check your windows network setup,
if the connection to the ubuntu VM has it's own network and the windows network on another (icon) you can select them both and 
[Right click]>[Bridge conections]...

This would be the first thing i would try
Hope it helps

---

### Post by ronin2307 on 2009-03-27
the VM settings indicate that the VM is using a bridged connection already

using VMware 6.5.1

---

### Post by ronin2307 on 2009-03-30
anybody?
Please?

---

