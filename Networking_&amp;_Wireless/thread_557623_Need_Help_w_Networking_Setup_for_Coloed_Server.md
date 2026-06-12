---
title: "Need Help w/ Networking Setup for Coloed Server"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by sog on 2007-09-22
hi there - 

trying to help a friend get a Sun x64 server setup and configured on Dapper and am running into some trouble. i've done it successfully before on an older Sun server for our business, but this one has some issues. 

here's the situation: 

1. Machine: X2200, i think, with 3 NICs (which are, importantly, read incorrectly by Ubuntu - 0 = 1 and so on)

2. /etc/networking/interfaces:
auto lo
iface lo inet loopback

# the primary network interface
auto eth2
iface eth2 inet static 
address [the machine's intended IP]
netmast [the machine's intended netmask]
broadcast [the machine's intended broadcast]
gateway [the machine's intended gateway]

3. route -n:

Kernel IP routing table
Destination    Gateway     Genmask     Flags    Metric    Ref    Use    IFace
[the machine's intended IP] 0.0.0.0 [the machine's intended netmask]  eth1
[the machine's intended IP] 0.0.0.0 [the machine's intended netmask]  eth2
[the machine's intended IP] 0.0.0.0 [the machine's intended netmask]  eth0
0.0.0.0 [the machine's intended gateway] 0.0.0.0                               eth0
0.0.0.0 [the machine's intended gateway] 0.0.0.0                               eth2
0.0.0.0 [the machine's intended gateway] 0.0.0.0                               eth1

summary:

basically, networking (DNS or direct by IP), doesn't work. can't reach outside. because of the misnumbering thing mentioned in 1 above, i thought a simple change to the /etc/networking/interfaces file - adding 1 to the eth number - would suffice, but instead i'm not getting the following:

/etc/init.d/networking start
* Configuring networking interfaces...
SIOCADDRT: file exists
Failed to bring up eth0 (or eth1/eth2)

any ideas as far as how i begin getting this fixed?

i know at least one of the NICs works, because before we shipped it to the colo we were able to get it setup and configured (after figuring out the misnumbering thing).

---

### Post by noob12 on 2007-09-23
Some suggestions:  

Do an **ifconfig -a** and get the mac addresses of the cards.

Then edit **/etc/iftab** and make sure the interface name  from mac addrs mappings match what you want.  Reboot.

I can't tell anything from the edited output on the other commands.

---

### Post by sog on 2007-09-23
awesome, thanks for the suggestions. i'll give that a shot first thing in the morning - i don't have the bandwidth at home to get in over the KVM virtualization setup they use. 

that, incidentally, is the reason for the edited listings - i can't cut and paste from the Java console they use as a remote terminal. 

thanks again - will post back once i have those details.

---

### Post by sog on 2007-09-23
ok, finally got back into the box. 

did an ifconfig -a, got the listings. 
did a nano /etc/iftab, and it matches the ifconfig -a. 

not sure what i'd change. verified with the colo that the cable is plugged into a NIC labeled eth1, which may or may not mean that eth1 has it - it could be eth2. 

what i'm not clear on is why it should matter. if i try to fire up networking on eth1, and it doesn't work, shut it down, then try it on eth2, why do i get the:

SIOCADDRT: file exists

error?

does anyone know?

---

### Post by noob12 on 2007-09-24
OK.  Maybe I misunderstood.  I thought you wanted numbering to start at 0 and it wasn't.

The only times I've seen "SIOCADDRT: File exists" is when setting the same route multiple times.  If multiple interfaces are on the same net, try omitting the gateway on one config.

---

### Post by sog on 2007-09-24
that's what i figured as well. the last thing to try i guess is to bounce the machine, see if that clears the existing routing table, and then try from there. 

will give that a whirl next. 

thanks, 

sog

---

### Post by noob12 on 2007-09-24
You shouldn't have to reboot.  You can delete routes with the **route** command.  Caution from one who's been there: if you're coming in on the net, be careful not to delete a route on which your ssh traffic depends :-)

---

### Post by sog on 2007-09-24
well, some progress. completely cleared the routing table - which is good - and attempted to restart networking. the good news is that i'm not getting "file exists" any longer. 

the bad news is that i'm getting:

SIOCADDRT: Network is unreachable
Failed to bring up eth1 (also tried eth2, due to the misnumbering i mentioned)

at a loss as to further steps.

---

### Post by noob12 on 2007-09-24
This is another routing error message (SIOCADDRT is a system call (ioctl) to add a route). You'll get the "Network is unreachable message" if you are trying to add a route using a gateway address that is not directly on a subnet you are on, or to which you do not already have a defined route.

As an example, if you had a single interface on the net 192.168.1.0/255.255.255.0 and no other routes, and then you tried to add a gateway 192.168.2.1, you would get this message.

I'm still quite confused about what you mean by the interfaces being misnumbered.  If you want them numbered differently, you should be able to change the mappings in **/etc/iftab** and reboot.

Maybe if you post your /etc/network/interfaces file together with a description of how you want the addresses, subnets, and gateways, readers might be able to suggest corrections to avoid the routing error messages you are getting.

---

