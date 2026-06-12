---
title: "multiple eth adpters, and routing"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by joe_lovick on 2008-11-10
hi,
     I have a complicated network setup due mainly to university constraints.... what i need is a way to automate setting up of the adapters and routes when i startup my machine.
     
i have 3 eth adapters in my machine....
         eth0 is not connected and is used to identify the computer to a license manager (lmhost), it uses the HW address to let me run unversity licensed software.

        eth1 is connected to a local router that provides in turn access to a 1TB lacie hard drive. university policy prohibts network drives or routers on the main network.

        eth2 connects the machine to the wider university network; and is used for all internet traffic

when i boot up the machine, it automatically runs dhclient on eth1 and grabs an address... 192.168.0.154, it then seems to ignore eth2.

so when the machine is booted, i have to then manually remove the route for default with something like this.... 

route del default eth1

then i run dhclient on eth2, and it connects the machine to the wider internet,

then finally i add a route like this
route add 192.168.0.0 netmask 255.255.0.0 dev eth1

which lets me once again connect ot the network drive. 

unfortunately it allways takes me serveral tries to get this all working, what i would like would be a way to get the machine to do all of this during bootup, such that my fstab could then automount nfs drives and shares on both the networks.

**** also could someone tell me how to specify extra lines to be added to my resolv.conf, (i need to add extra search domains, in addtion to the ones the dhclient provides)

thanks for any help!

Joe

---

