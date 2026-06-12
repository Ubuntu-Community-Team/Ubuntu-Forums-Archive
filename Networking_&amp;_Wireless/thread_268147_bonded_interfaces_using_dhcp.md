---
title: "bonded interfaces using dhcp"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by draven on 2006-09-29
Hey gang,

I'm trying to setup a bonded interface on an Ubuntu 6.06 machine. Everything works fine from the command line, and everything works fine if I use static IPs in /etc/network/interfaces. But it does NOT work with dhcp.

Examples:

# modprobe bonding
# ifconfig bond0 up
# ifenslave bond0 eth0 eth1
# dhclient bond0

The above works fine. But, if you try to put that into the scripts, it refuses to DHCP an IP.

> /etc/network/interfaces
> auto bond0
> iface bond0 inet dhcp
> slaves eth0 eth1

It appears to me that the slaves are not being slaved. If you try to DHCP a bonded interface with no slaves, it will obviously fail. So what is the proper way to get slaves to work?

I referenced both of these articles and neither method works for me:

[http://www.linuxquestions.org/questions/showthread.php?t=434826](http://www.linuxquestions.org/questions/showthread.php?t=434826)
[http://pmjdebruijn.blogspot.com/2006/04/ubuntu-bonding.html](http://pmjdebruijn.blogspot.com/2006/04/ubuntu-bonding.html)

The problem with the technique in the second article is that it assumes you want static. If you bring up the interface in dhcp before it slaves, it will fail. If you try to bring up the interface with the IP of 0.0.0.0 and then add "post-up dhclient bond0" it still fails.

Who knows the answer? It must be possible with out writing my own script to do it.

---

### Post by kevin_fu on 2006-10-09
i met the same problem, and i think it can be solved this way:
iface bond0 inet dhcp
    pre-up /etc/netscript/bond-init

bond-init is as follow:

#!/bin/sh
list_eths()
{
    ifconfig -a | awk '/^eth[0-9]/ { print $1 }'
}

for card in `list_eths`
do
        cards="$cards $card"
done

ifconfig bond0 up
ifenslave bond0 cards

yes, you can do it without writing script, it's nothing different.

---

