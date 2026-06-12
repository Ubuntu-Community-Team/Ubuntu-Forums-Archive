---
title: "Home network layout / Virtual machine query"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Maxymillion on 2008-06-27
Hello, seeking some advice my home networks layout

Setup: I have 4 nics in my server.   eth0, eth1, eth2 are trunked as bond0.   eth3 is my cable connection.

Just 1 smart switch. With local computers / 3x bond0 plugged into it.

Now the server is to provide a firewall/net sharing for local computers (gaming rig / tv box), as well as some guest virtual machines hosted on the server (VM's require host networking). Ubuntu Hardy as Host, Ubuntu Jeos VM's as guest's



Where I'm getting stuck is with the host networking. Seperately things work perfectly, aka bond0 works, and shares cable to all localclients and VM if i don't bridge bond0 to setup host networking. Alternatively if I've setup host networking, the VM's can see each other perfectly and my server. However as bond0 is the device being bridged to the virtual machines, bond0 then lose's connection to local computers. Also not internet since bond0 is set as the gateway IP.



What I'm thinking is 
- maybe check out more about bridging?! To allow both 
- Only use 2 nics in the trunk, and have an extra spare nic with its own IP to treat as gateway IP?
- bridge eth3 my cable device instead of bond0? Tried and lost itnernet in host and guests.
- What i was keen on in the first place, tie eth3 to a virtual machine ONLY!, and have my virtual machine act as the gateway. Sharing internet to original Ubuntu host, guest VMs, and local computers.


Suggestions?! 
Any advice appreciated 

(and yes I love having 3 gigabit cards trunked to pipe me data from my raid at ludicrous speeds :P)

---

