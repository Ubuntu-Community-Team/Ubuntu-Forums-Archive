---
title: "Dual Static Networks, Dual NIC's works, then down"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by dvl62 on 2008-05-29
I have a new Dell R200 server with two Broadcomm integrated NIC's.  I am trying to configure the server with a public IP on eth0 208.xxx.xxx.131 and on the second NIC a private address on eth1 of 128.1.1.5

During the initail base install of Ubuntu 8.x (by the way had the same issue with 7.x), I configured the primary interface ent0 as follows:
Address 208.xxx.xxx.131
netmask 255.255.255.224
network 208.xxx.xxx.128
broadcast 208.xxx.xxx.129
gatewat 208.xxx.xxx.129
dns-nameservers 209.xxx.xxx.2 209.xxx.xxx.2

The machine is able to access the internet, I am able to configure, updage and upgrade just fine.

I then edit the /etc/network/interfaces file by adding additional interface eth1 as follows:
auto eth1
iface eth1 inet static
        Address 128.1.1.5
        netmask 255.255.255.0
        network 128.1.1.0
        broadcast 128.1.1.255
        gateway 128.1.1.254
        dns-nameservers 209.xxx.xxx.2 209.xxx.xxx.2

The machine is able to access bioth networks just fine for a period of time, and then it looses one (usually the 208.xxx.xxx.128 network.  I can bring down the interface and restart it, and it comes right back, but then dies.  I have put this in a production invironment as well as a controlled private environment to isolate the networks with the same results.

If anyone can tell me what I am missing, I would appriciate it.

---

### Post by dvl62 on 2008-05-29
Thought I would post the resolution to this as to help someone in the future.  A a special shout out to an "andyjenkins" who initially posted the base information.

You do not want the gateway set on any internal NIC. "Gateway" means that if your computer cannot figure out what interface to send a packet on, it sends it to the gateway and lets it handle it. So, on eth0, the gateway points to the ISP's router, which knows "this packet is for google -> send it towards Cali" or "this packet is for CNN.com -> send it towards Georgia (i think)." Obviously more complicated, but this is the general idea.

How your computer decides if it "knows" where to send a packet is based on the IP and subnet masks of the interfaces, so, with the setup I listed in the intial post, any packet destined for 208.xxx.xxx.* (*=anything) goes out eth0, any packet destined for 128.1.1.* goes out eth1, and after this (i.e. the packet is not for 208.xxx.xxx.* or 128.1.1.*), it looks at its gateways. If both interfaces are up, then there are two gateways defined, and I think it gets to pick either (maybe every other packet goes out eth0/eth1?). What you want is for all the packets that arent 208.xxx.xxx.* or 128.1.1.* to go out eth0, for your gateway 208.xxx.xxx.129, which will then send them the correct way.

So I, removed 'gateway 128.1.1.254' from eth1 and it works correctly. You don't need gateways defined for every interface. You can check out your routing tables at any time by doing 'route -n' from the command line - as you turn eth0, and 1 on and off, you can see this table change.  :) :popcorn: :)

---

