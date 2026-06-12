---
title: "NFS with multiple routes to server"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by johanngoetz on 2007-10-23
The problem I am running into is that there are multiple routes to the NFS-server for the certain computers in our cluster. I can ping the nfs-server from either subnet's computers, but NFS seems only to work on one of the subnets.

Is there an option in the NFS export /etc/exports file to specify an ethernet device when exporting to specific subnets?

I need something like this on the server:
### /etc/exports file
/export/large-dir    192.168.0.*(rw,sync,device=eth0) 192.168.1.*(rw,sync,device=eth1)

Thank you,
Johann

---

### Post by Lambert on 2007-10-24
What you want to do is route traffic at the application level and I'm 95% sure that's not possible.

Your file should look something like this and I'm sure there's probably another way to list this.

/export/large-dir 192.168.0.0/255.255.255.0(rw,sync) 
/export/large-dir 192.168.1.0/255.255.255.0(rw,sync)

This will allow any client on subnets 192.168.0 or 192.168.1 access to the nfs share and the path/interface used will be handled at the network level.

When you say you can ping from either subnet, it should automatically be going to the different nics as the iproutes designate. Have you used traceroute, this will show the path taken to and from server which should show both nics being used.

---

### Post by johanngoetz on 2007-10-24
Thanks for the quick reply! I think maybe permanent routing might work but I'm not sure how to implement that. At any rate, maybe there is a better way to do things so here is the description of my computing cluster:

My attempt at some ascii art (my cluster):
```

 /---*queue-master*
 |   exporting /export/home directories
 |   dhcp/NAT server for slave-net
 |        \
 |         \
 |          \
 |           \--{slave-net}
 |               |||   |
 |               |||   |
 |   *slave0* ---/||   |
 |   *slave1* ----/|   |
 |     .      -----/   |
 |     .               |
 |     .               |
 |   *slave-special* --/
 |   exporting /export/large-dir
 |      |
 |      |
 \---[workstation-subnet]
        \ \ \
        | | |
     *workstation0*
     *workstation1*
        .
        .

```

I have *slave-special* exporting /data/large-dir to the world (*) at the moment. *queue-master* is a NAT routing dhcp server for all the slaves.

both *slave-special* and *queue-master* have an IP for the {slave-net} (192.168.0.X) and an IP for the [workstation-subnet] (IP via NIS/DNS).

Notice that there are two routes the slaves can take to talk to the slave-special. It could talk direct via the slave-net but it can also go through the NAT router in queue-master and the workstation-subnet. It seems to prefer the latter but I don't want to tie up unnecessary resources like that.

What I wish to accomplish:
I would like two directories (home and large-dir) to be seen by both slaves and workstations. Furthermore, when any computer looks at the home directories, they talk directly to queue-master; when any computer looks at the large-dir, they talk directly to slave-special. The home directory is not a problem because it is on the dhcp/NAT server (queue-master). The large-dir on the other hand seems to only export on a specific subnet (the workstation subnet).

I need slave-special to export via both the slave-net and the workstation-subnet.

OR: anyone have a better solution?

Thank you for reading all this,
Johann

---

### Post by Lambert on 2007-10-24
You need to research setting up routing tables for your cluster. Because of the set up, I suggest searching for more detailed answers.

As a simple answer (and I could be missing some detail or there is a better method I'm unaware of), on slave special if you have eth0 attached to slave-subnet(192.168.0.x) and eth1 attached to workstation-subnet(192.168.1.x), you would set up a route like this.

```

route add -net 192.168.1.0 netmask 255.255.255.0 dev eth1

```

this will set up the routes on slave-special so all ip traffic for subnet 192.168.1 goes through eth1 direct to workstation-subnet and not through your nat router. All other traffic would go through your nat router.

Then on the workstation-subnet, you could set up the route so just traffic with an ip of your slave-special goes direct to slave-special, but not all 192.168.0x goes that path. My guess is you would still want all other slave-subnet traffic to go through the nat router.

Hopefully this will get you going in the right direction.

You can look at this site for some detailed answers. There are others out there you will find in a search.

[http://www.lartc.org/](http://www.lartc.org/)

---

### Post by johanngoetz on 2007-10-24
O.K.! Your first post put me in the right direction with using route and traceroute.

With the setup as described prior, I originally thought I would only have to specify the routes to the various IPs for the slave-special (serving the large-dir). But I also had to specify the IP address of slave-special on the other slaves as they got the IP for slave-special through DNS/NIS on the workstation-subnet and thus had to go through the workstation-subnet.

SOLUTION: I merely listed all the slaves' IPs in slave-special's /etc/hosts file. And I then put slave-special's slave-subnet IP (192.168.0.X) in slave-special's /etc/hosts file which will superceed the NIS/DNS IP the slaves would normally get.

Thus the routing from slave-special to the slaves is on the slave-subnet and the routing to everything else is done through the NIS (workstation subnet).

Thanks for your help!
Johann

---

