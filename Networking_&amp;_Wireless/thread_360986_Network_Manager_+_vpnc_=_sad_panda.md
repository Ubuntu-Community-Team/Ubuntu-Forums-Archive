---
title: "Network Manager + vpnc = sad panda"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by PhyerFly on 2007-02-13
Okay, I've been struggling with this for a few days now and I haven't been able to find a straightforward solution for my problem on these forums or elsewhere on the net. I'm frustrated because I would like to be able to work in Ubuntu rather than Windows - so please, bear with me as I try to explain.

**Here's the question:**
How do I establish a cisco vpn connection using Network Manager and vpnc giving myself full access to my company's network (all ranges) without losing access to the internet through my local network? 

**Here's the details**
I'm running edgy with **network manager vpnc** installed and I'm trying to connect to my company's vpn server so that I can work from home. I was given a keychain VPN authenticator key (I type a pin number and it gives me a network password) and .PCF file to use with my windows cisco vpn client. I was able to import the pcf file at the time of creating a new VPN connection from the network manager gui and I extracted and decrypted my "group password" from the file. 

When I open the vpn connection I input the group password and the network key I get from my authenticator I'm  able successfully log in and receive my company's warning message about this being a private network etc. Thats when the fun happens.

From there I **lose all connection to the internet** and I'm not able to access anything on my companys internal network either (no ssh, no pinging of local ip's). After talking to a friend who's pretty network savvy, he told me that my routing table was probably messed up. He said that I needed to change it so it only uses the VPN connection for private IP ranges on my company's network.

I found this guide and used it as an example (look at fig. 13 and 14)
[http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml)

After supplying the range 10.0.0.0/8 in the "Only use VPN connection for these addresses" box  in the Network Manager vpn editor I'm able to connect and get access to "some" of the things on my company's network but anything outside of that 10.x.x.x range gets routed through my local network connection which obviouslly doesn't resolve correctly.

When I use the Cisco VPN client in windows it "just works" and I don't need to modify routing tables or decrypt passwords. I tried installing the linux version of the Cisco client back when I was using dapper but I had trouble even getting it installed, much less getting it configured correctly. 

Is there something I'm missing here? If you want to help, please be definitive with your answers as I've gotten enough "go read the man pages" from people already.

---

### Post by PhyerFly on 2007-02-20
Anyone? Are self bumps allowed here? :confused:

---

### Post by drahcir192 on 2007-03-03
I have used kvpnc successfully.  What I needed to to was add a route to my company's network  #route add -net 192.56.76.0 netmask 255.255.255.0 dev tun0 now the important part of this is the device. vpnc creates a tunnel between your computer and you work network. this is created as an other network  device called tun if you run ifconfig you will see it. so you have to tell it about you work network.

Richard

---

