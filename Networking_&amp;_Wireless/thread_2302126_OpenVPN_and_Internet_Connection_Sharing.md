---
title: "OpenVPN and Internet Connection Sharing"
date: 2015-11-07
forum: Networking &amp; Wireless
---

### Post by marco121 on 2015-11-07
By following the guide at "https://help.ubuntu.com/community/Internet/ConnectionSharing", specifically following the part for "Ubuntu Internet Gateway Method (iptables)", I succeeded in setting up the shared connections from one machine running Linux to other machines connected to a switch, which was connected also to the Linux machine. It worked just as described, and I used the same IP addresses as those used in the example. All went well.

However, I wanted to take it one step further, but I ran into a problem.  After setting everything up and verifying the functionality, I then turned off the secondary machines, those with which I was sharing.  At that point I enabled an OpenVPN connection on the primary machine, the one from which I was sharing, and verified that it was functioning correctly. Then I reenabled the connections between the secondary machines attached to the switch, but they cannot establish an Internet connection while OpenVPN is running on the primary machine.  

On one of these secondary machines running Windows, I tried troubleshooting the connection to see what it found.  It advised that the DNS server isn't being found.  These secondary machines had been assigned static IP data, and I included two DNS servers: one for OpenDNS and one of those that appears to get pushed down from the VPN server to which I connected on the Internet. When it is connected, the DNS servers in the primary machine get changed temporarily in "/etc/resolv.conf". So I made sure that one of these two temporary DNS values is in the Windows machine along with one of the OpenDNS servers. I cannot understand why the DNS fails to get shared as well as the Internet whenever OpenVPN is running.  Any ideas would be appreciated. Thanks.

---

### Post by SeijiSensei on 2015-11-07
What is the OpenVPN tunnel connected to?  Is it now the default gateway for the machines behind the Linux box?  That gets tricky because you need to send the packets to the machine where the tunnel terminates over the public Internet but route everything else through the tunnel.

You need to tell us precisely what you're trying to accomplish with OpenVPN here because it's not obvious from your description.

---

### Post by marco121 on 2015-11-08
Hi, SeijiSensei.

> "what you're trying to accomplish with OpenVPN"

I want the Internet Connection Sharing via the OpenVPN tunnel to propagate to the machines behind the Linux box, which are connected to it with a switch. As I stated, and as the link indicated, Internet Connection Sharing works fine in my LAN configuration from the Linux box to the machines behind it when I do not have OpenVPN running on the Linux box; but the Internet does not work on these machines behind the Linux box if I have the OpenVPN running on it although the OpenVPN is functioning fine for the Linux box itself in either case.

My OpenVPN client on the Linux box is connected to an OpenVPN server on the Internet.


> "you need to send the packets to the machine where the tunnel terminates  over the public Internet but route everything else through the tunnel"

This statement is not clear to me. It sounds as though you are saying that, when an OpevVPN tunnel exists between a client machine, for example on my LAN, and an OpenVPN server on the Internet, part of the data from my LAN will go through the tunnel but another part must go across the Internet to the server in order for it all to function properly.  Is that what you meant to say? Thanks.

---

### Post by SeijiSensei on 2015-11-08
Yes.  In order for the tunnel to be established, your client and the OpenVPN server must be able to communicate over the public Internet to exchange the packets that contain the encrypted tunnel traffic.  You must therefore have a route to that server out through your router and over the public Internet.  Suppose your router has the address 192.168.1.1, and the OpenVPN server's public address is 10.10.10.10.  Finally let the server's tunnel address be 172.16.1.1. Your routing table would have these rules:
```

ip route add 10.10.10.10 via 192.168.1.1
ip route del default
ip route add default via 172.16.1.1

```
The first statement tells the Linux box to use your Internet router to reach the OpenVPN server over the Internet.  The second command deletes the "default" route that handles all other traffic so it can be redirected through the tunnel by the third command.

If you do not have the first rule, the client will try to send the packets that contain the tunnel traffic through the tunnel itself and fail.

I don't know how you are setting routes.  The conventional method is to invoke a script from the .conf file with the "up" directive.  If you take that approach you may already have one or both "default" rules in that file.  If so, you can add the first rule above them.  You could alternatively add the first rule at the end of the boot sequence by putting the first command in /etc/rc.local.  This script runs with root privileges so you don't need "sudo".

---

