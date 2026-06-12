---
title: "Network bridge with KVM"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by zeron00 on 2014-01-31
Hi!

I'm trying to set up a virtual machine with KVM and I have some  difficulty configuring the network bridge. I've found several guides on  the net and tried to follow the instructions, but I must be missing some  important detail, because my machine stubbornly refuses to follow the  settings. [IMG]https://www.kubuntuforums.net/images/smilies/scratchheadyellow.gif[/IMG]

In all the guides one is advised to set up a network bridge on the host  for the guestOS to use. In order to do that one is advised to edit the  /etc/network/interfaces file.

Here's my unedited /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp

```

After following the guides the file looks like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet manual

# Network bridge
auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

When I reboot the Network Manager icon appears crossed over, showing that I have no connection and update services also complain about the lack of connection. Yet the connection is working fine -- I can ping and use firefox without any difficulty.:confused:
So why is Network Manager lying to me? Is this some bug or am I missing some crucial detail?

I have Kubuntu 13.10 64bit, and my machine is on a home LAN, connected  to the net by a regular router. The router recieves an IP from my  Internet Provider, but this IP is static. The router has a working DHCP  that assigned IPs to devices on the home network. It is configured in  such a way that the machine I'm working on always receives the same IP:  192.168.1.4. The router's address on the home network is 192.168.1.1.

Some advice would be appreciated at this stage. Perhaps there are some CLI tools for creating a bridge instead of doing at manually? Or is the fault with the implementation of Network Manager?

---

### Post by Doug S on 2014-01-31
It is only recently that I finally got bridged networking going on my server that hosts my VM guests. Some guests I haven't converted yet. My interfaces file looks at little different than yours:```
doug@s15:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface and bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
``` Also, my host is a server computer with no GUI, so I don't have "Network Manager". I used the [Ubuntu Serverguide]("https://help.ubuntu.com/13.10/serverguide/network-configuration.html#bridging") as my "how to" reference. However, a recent change to this exact area of the document has not been published yet, where it says "sudo service networking restart" do "sudo ifup br0" instead, or just restart the computer.

There was [another thread]("http://ubuntuforums.org/showthread.php?t=2202732") just earlier today, where it was suggested Network Manager might not know about bridging.

---

