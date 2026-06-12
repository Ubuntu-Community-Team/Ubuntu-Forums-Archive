---
title: "routing trouble?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by squishywalrus on 2007-06-22
**EDIT**  Sorry to anyone who spent any time pondering this... for some reason I never thought to check the firewall on the red hat machine...:oops:  everything works now

Alright, so I have a machine running 7.04 connected via crossover to an older red hat box.  I've written a very simple tcp client/server program and am trying to test it.  When I try to connect to the red hat box(running my server) from ubuntu(running the client), I get:  "connect:  No route to host".  When I run the client on the red hat box, though, and the server on ubuntu, everything works just fine.  Now, the weird part about this is, I can ping the red hat machine just fine from ubuntu, and even ssh to it, I just can't connect using my own tcp program.

The networking should be fairly default on the ubuntu box, I've disabled network manager and configured it with a static ip (though it does have a second NIC connected to the internet that gets its ip from DHCP, though even with this unplugged and disabled, the problem persists).  The only real modifications I'd made are those in this thread:  [http://ubuntuforums.org/showthread.php?t=179472](http://ubuntuforums.org/showthread.php?t=179472) to try out tun/tap networking with qemu, though iptables is not running while this problem is going on.

any help would be greatly appreciated,
nick

---

