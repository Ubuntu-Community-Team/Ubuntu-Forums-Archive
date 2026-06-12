---
title: "ICS and network setup"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by chris_avery on 2010-01-13
Hello,
    I need some help in setting up a simple small network at my house using Ubuntu.  This is how the network is going to be set up starting with the connection to the net (1) and ending with the individual PC's on the network

1) Internet comes in through mobile broadband card
2) mobile broadband card connected to windows vista computer
3) vista computer has cat5e to connect the NIC to a switch
4) switch receives internet feed from vista computer and distributes feed to the other 2 computers on the network

I can not seem to get this working!  When everything is set up I can get the other computers to ping the switch OK; I also can browse the web on my vista computer but it seems like there is no internet "feed" going from my vista computers NIC to the switch.  I have enabled connection sharing on the vista computer and have everything plugged in.  What else am I missing?

Is it a problem with the vista comp setup?
Is it a problem with the switch setup?
Is it a problem with the ubuntu computer(s) setup?

let me know what information you need.

Chris

---

### Post by Iowan on 2010-01-14
I'm not familiar with switches having "ping-able" addresses (mine are pretty primitive). Can you ping the "gateway" computer from the others?

---

### Post by chris_avery on 2010-01-14
Well it's actually a router but I am using it as a switch.  Maybe I have to disable DHCP on the router?  Anyway this is the "flow" of the internet

wireless broadband->vista computer->router->2nd & 3rd computer

I have also noticed that 1) the subnet mask of the router was different than the subnet mask of the gateway computer's LAN and 2) the IP addresses of the gateway LAN and the router were the same. (192.168.0.1)

I have not been back yet to fix these and see if that will fix the problem or not but will do so at the first opportunity I get.

---

