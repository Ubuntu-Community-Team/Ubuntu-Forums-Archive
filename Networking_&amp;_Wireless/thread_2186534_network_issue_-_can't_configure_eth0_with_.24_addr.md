---
title: "network issue - can't configure eth0 with .24 address as gateway"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by robert.d.munn on 2013-11-07
I am configuring a server on my network. I have an IPv4 address block xxx.xxx.xxx.24/29 riding on top of a /30 block. My router has an address on the /30 block as the WAN interface, and .24/29 (255.255.255.248) as the DMZ interface, per instructions from the network engineer, which in theory gives me .25-.29 as available addresses for servers. 

This configuration works fine in Windows Server. I add an ip address (xxx.xxx.xxx.25) net mask (255.255.255.248) and gateway (xxx.xxx.xxx.24) and the network is up. In Ubuntu, when I assign the address xxx.xxx.xxx.27 and net mask 255.255.255.248, the OS assigns .24 as the network address of the IP block. If I manually assign .30 as the network address and .24 as the gateway, I can ping the .25 server, but everything else is cut off. 

I had a similar problem when changing routers. My current router running OpenWRT handles the .24 gateway fine, but the router I originally wanted to run (a Ubiquiti EdgeMax router) refused to work with .24/29 configured as the DMZ interface. On that router I had to use .30/29, and the gateway on the servers became xxx.xxx.xxx.30, which worked OK when configured. 

Has anyone seen this problem before? I am not a networking guru and have no idea why different OS / network stacks would treat the same block differently. 

Any help is appreciated.

---------

EDIT: I just changed the DMZ interface to .30/29 and tried these settings for eth0 on my server:

address: xxx.xxx.xxx.27
netmask: 255.255.255.248
gateway: xxx.xxx.xxx.30

These settings did not work. This is a Supermicro server with Intel Gige nics, Ubuntu seems to recognize the nics fine but I am going to check the driver situation anyway.

Incidentally, I had this same issue trying to run an Ubuntu VM on top of Windows Hyper-V on identical hardware.

----- 
EDIT: Further investigation: the server is running Intel 82574L GigE NICs. An older thread: [http://ubuntuforums.org/showthread.php?t=1700367](http://ubuntuforums.org/showthread.php?t=1700367) reports problems with the supplied driver for this chipset, and a solution using kernel ppa. I am going to check the advice from this thread, any suggestions otherwise are appreciated.

-----
EDIT: OK, so I typed 
route add default gateway xxx.xxx.xxx.30
ifconfig eth0 xxx.xxx.xxx.27 

and now the NIC is working.  I want to make this change permanent, but these settings in /etc/network/interfaces does not seem to work from boot. Suggestions?

---

