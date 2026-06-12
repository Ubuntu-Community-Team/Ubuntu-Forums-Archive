---
title: "Networking with 2 cards, router, hub and Samba!"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by sam_i on 2006-11-25
Hi all,

My first post in a decent linux distro forum, would like to say hi and go easy on me ;)

What ill do is give you a run down of what i have, what i would like, what the issues are, and what i think would solve it (but some questions i would like answering anyway for future reference).

What i have:

I have a cable connection, comming into a DSL/cable router, which then plugs to one machine and then wireless to another machine. The router is set up to not use DCHP as each machine has a static IP address. 
-Wireless windows machine is set to 192.168.1.40
-wired downstairs windows machine is set to 192.168.1.10
-Router is currently set to 192.168.1.1 (but sure to change at some point)

Those machines are running fine, and both detect each other on the MSHOME (ick) workgroup.

One port from the router also goes upstairs to the loft, which is connected to this my machine, which has 2 network cards. The second card goes to a hub (as the hub doesn't have a uplink port), which then connects to a further machine.
-the loft main machine is Linux (the problem machine), which has an IP address of 192.168.1.30 on first Ethernet (eth2) and 192.168.1.31 (eth3) on second. Both are currently set to use 192.168.1.1 at their gateways.
-the middle floor machine is windows and has an IP address of 192.168.1.20. This is currently the machine that needs to access the loft machine. It is set on the MSHOME workgroup, and currently uses 192.168.1.31 (eth3) as gateway.
-the hub will be used later to expand the amount of machines on the sub-network hence the need for it.

What i had before the router:

A direct connection to each machine for the internet using a USB Ethernet converter. This used to also work fine on the loft machine as eth1, and eth0 used to be another network card which i have since removed, which used to connect to hub and samba used to work. 

What i would like:

All machines loft, ground floor to have internet access, all machines to have access to the Samba file share on loft machine, and middle floor machine to only have samba access and not internet (as its not needed).

What the issues are:

-Internet connection on loft machine doesn't work without swapping over router connection over to other Ethernet on each boot up. 
-Samba now doesn't work on any machine

What i think would solve it:

-firstly, i would like to be able to reset the network configurations and restore back to their original settings as this is part of it. I would like these cards to be eth0 and eth1, but im not sure where these are defined. If someone could guide me as how to ether reset, or reconfigure all my network cards that would be excellent.
-Secondly, the samba config is fine as i haven't changed that file, and it does include all interfaces. But this may be of an issue. Is samba set to only work on certain interfaces when initially installed? Is it a good idea to re-install samba? if so, whats the best method to do that?
-finally any other configurations of the network suggestions would be great - thank you for your time.

Cheers in advance, your help would be very appreciated (once i get this set up its gonna remain like this as long as possible lol.)

---

### Post by dmizer on 2006-11-25
okay ... you have a couple of issues i see.

first of all a hub does not hand out ip's.  it merely routes traffic.  so your loft machine is going to have to do one of two things:
1) act as a router and hand out DHCP ip addresses (on a different subnet) to all the computers that will connect to the hub in the loft.  this is done with nat through the configuration of iptables.

2) you can configure your ubuntu desktop in the loft with a network bridge where the connections from the hub are invisible to the ubuntu machine and attach ip addresses to the router downstairs instead.

i've never successfully configured a bridged network connection so i'm not too sure where to point you for that.  but there's a ton of information on internet connection sharing using NAT.

you'll have problems with samba until you get the sub network in the loft configured correctly.  part of the problem is that your loft computer has both eth2 and eth3 configured with ip addresses on the same subnet (an ip conflict).

there are advantages and disadvangages to each.  if you configure nat for your loft network, none of the computers in the loft (except the ubuntu machine) will be able to share files or information with the computers on the rest of your network (main floor).  though sometimes this is a desireable situation.

bridged connections are quite complicated to set up.  i've tried unsuccessfully several times, and there really are not a lot of how to's around which give good information on how to enable this.

---

### Post by sam_i on 2006-11-27
Excellent work, you have helped me set up my router side now as changing subnet made that work. Ill look into bridging, but i thought this was relitivly simple when i read about it before - just editing the DNS table so that anything comming from 192.168.1.20 would get forwarded onto the router. That said i havent set this up in linux, but i have in window$, so ill let u know if i have any luck at a later date. Cheers for the help however!

---

