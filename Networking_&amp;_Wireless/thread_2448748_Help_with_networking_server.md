---
title: "Help with networking server"
date: 2020-08-13
forum: Networking &amp; Wireless
---

### Post by doehurden on 2020-08-13
Hello all,

Thank you for reading this and thanks in advance for any help i may get.

I am working with some old hardware to try and set up a HPC at school. As it stands i have built up two machines, one machine as a head node and one as a slave or worker node, and id like to get these working before i start to expand my little project.

Both machines, lets call them HAL0 and HAL1, have ubuntu server installed on them as well as network-manager.

I have physical access to the hardware however i am trying to work from home where i can.

HAL0 has two ethernet ports (eno1 and eno2). eno1 is connected to a switch on the institutions network, called ENGnet. There is a static IP address for this port along with a gateway address, subnet and DNS address provided by IT. I edited the interfaces file on HAL0 to include this information and I am now able to SSH from the school network to this machine.

The second ethernet port on HAL0 (eno2) is physically connected to a second network switch (lets call this HALnet) that i intend to use for the HPC networking. HAL1 also has an ethernet cable to HALnet and is not physically connected to the larger ENGnet.

My largest problem at the moment is that when i turn on eno2 on HAL1 (using [sudo ifup eno2] or activating the connection in the network manager tui) I loose the SSH connection to HAL1 through the eno1 port. This has been hugley frustrating as i then have to travel into school, plug in a monitor and keyboard to HAL1 and shut down eno2 to regain access through SSH. 

I have been reading online etc. but i wonder if anyone knows of a good wright up of how to set up this kind of network. 

kind regards,

Leon

---

### Post by TheFu on 2020-08-13
[LIST]
[*]a) servers have static IPs.  No need for network-manager.  Don't. Just don't. Don't use DHCP.
[*]b) to work on servers from remote locations, use ssh. If going over the internet, never use passwords, only ssh-certs or ssh-keys.  Also, setup fail2ban on all ssh-servers, regardless of where they are - LAN or WAN - doesn't matter.  Best to use it over a non-standard port - let the router do port translations from WAN/63022/TCP ---> LAN-IP/22/TCP on the server.  If you can't get IT to do this port forwarding, stop now.  Talk with them about either providing a VPN (openvpn or wireguard) into the school server LAN or opening 1 port to one of these "servers."
[*]c) interfaces file has been deprecated. Use netplan on 18.04 and later releases.  Hopefully, you are deploying 20.04.1 today. That's definitely using netplan.
[/LIST]

To get help, you need to provide actual facts.  Real IPs. Real subnets. Real routing tables for all the systems AND label them clearly.  So, login to each system and run these commands:
```
route -n
ip addr
```
That should be enough.

The system that has 2 subnets connected. If you want those to be bridged, that is now a "router" and you'll need to setup that ... or it would be easier to get a cheap $10, used linksys from goodwill and use that as a router between these 2 networks.  The double or triple NAT needed from the internet is just an extra layer of ports to manually open for ssh into the ENG LAN.

I'm assuming you aren't confusing network switches with network routers. If you are, things become harder. You could rent a VPS from Vulr or DO for $4/month, setup a VPN server there and have one of your "servers" connect into that. Then setup inbound connection access from the VPN to one of the "servers." If you do this in a corporate environment without approval, expect to be fired.  At a University, who knows what will happen?

---

### Post by doehurden on 2020-08-13
Hi TheFu,

Thank you for your response. I have no doubt you can tell i am new to this, so i will need to spend some time with google to decipher much of your response. 

Regarding some of what you sagest i will provide a little more information about what i know thus far.

Your suggestions regarding my remote access and VPNs, maybe i am confusing switches for routers in that instance (ill have to google the difference to know). I have tried and tried to get direct access to the ENGnet from home to enable me to ssh from my home machine straight to this cluster. i am simply not allowed this though. We do have another cluster that is on a different university network, i can ssh straight to this cluster, however i am told that this is simply not allowed to use this hardware on the UNInet. I also know that some of the software i intend to run on this cluster requires licensing that is only accessible on the ENGnet. 

To communicate with this cluster, i am using a VPN to gain access to my my office pc, a windows machine, and then putty to ssh through the ENGnet to the head node. This is working fine as long as i don't tern on the second network port on the head node. As soon as i do i lose access and as stated, i have to travel to school to rectify my mistake. 

Re point a), I assume by this you are referring to the editing of the etc/network/interfaces file. I have been given a static address for the port eno1 that I am told to use or IT will shut down that access point to ENGnet. In this file, i have the iface set as static and have defined the address, netmask, gateway and dsn-server for eno1. there is also a line above this information that reads 'auto eno1'.

I was then instructed to define eno2 in the same file. I did this with all the same information except the IP address as i was told to use a different ip address. I was told to use anything i liked as this second port (eno2) would never connect directly to ENGnet. As i read more on the subject, i suspect i need to use a different netmask, subnet. Can these be made up numbers? I suspect not but.....

Re providing actual ip addresses etc. . When i look online at others posts it seems people don't share actual details. Is there not a security risk with providing these numbers?. I sincerely hope you don't take offence but i must check with IT before i share any of this information, its above my paygrade to do so when i don't understand exactly what i am sharing without there consent. So i guess, watch this space. 

The switch i am using for the cluster is a 3com Switch 3824

Thanks again, so very much, for your help.

---

### Post by TheFu on 2020-08-13
Less describing what you believe and please post command output proving what you believe. Wrap all commands with any options used AND output in "code tags" so it is readable here, columns line up.  For any output over 1 pg long, please use paste.ubuntu.com and post the URL.  
Reading what someone new believes usually isn't helpful. Sorry, but that is just true. Facts are required. Those come from running commands on the systems and posting the output.

IPs are never private.  They are all public. Hiding them makes no sense, especially if they are non-routable subnets. I have a few LANs here - 172.22.22.0, 172.22.21.0, 10.x.x.x and 192.168.22.0.  I keep them all with /24 networking to make routing needs easy in my head.  One of my public IPs is 50.73.91.147.  Knock yourself out with that data. It isn't any security risk.  If you look at my posts here, you'll see I'm one of the most security aware posters - to the point of being considered paranoid.

The /etc/network/interfaces file has been deprecated. Don't use it. Use /etc/netplan/.... file(s). These are YAML.
What kind of cluster are you using?  Or is it just a group of servers?

Anyway, if you don't want to provide the requested data, that's 100% fine. Doubt I can help without it.

---

### Post by falloutboy2 on 2020-08-13
A couple of questions:
What is the make and model of the machine with the two Ethernet ports that you are setting up?

I ask as if it is a rack device or a server board it possibly has an IPMI port which to all extents and purposes looks like an Ethernet port but has a dedicated use case.

Generally the IPMI port will be separated from 1 or more Ethernet ports by physical distance, a good example of a server board with this type of configuration is the Supermicro X8DTH-IF.

A little more info on your hardware might provide some clarity, it might be as simple as you only have two ports and one of them is IPMI in which case you will need another NIC.

Sorry, I am not wanting to assume anything so I am presuming that this hardware is new to you.

---

