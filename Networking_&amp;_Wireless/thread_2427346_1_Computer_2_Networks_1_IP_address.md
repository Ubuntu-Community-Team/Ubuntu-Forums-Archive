---
title: "1 Computer 2 Networks 1 IP address"
date: 2019-09-20
forum: Networking &amp; Wireless
---

### Post by webmiester on 2019-09-20
Hi everyone,

I have a computer with 2 LAN ports.

SERVER 1 has 2 LAN ports:
LAN port 1 will connect to LAN "A"
LAN port 2 will connect to LAN "B"

The Computers connected to LAN "A" are different from the computers connected to  LAN "B"...

My question:

Can I setup the 2 LAN ports so that they will have the same IP address?  In this way if I transfer a computer from LAN "A" to LAN "B", I don't need to change their settings, they will continue looking for the same server address and it should work.

I think this will work but my IT says it will create a conflict so he doesn't want to go with it.  However, thanks to your help in previous posts, I was able to disprove him on a few topics regarding our network.

Thanks so much.

---

### Post by Skaperen on 2019-09-20
if you mean the same network subnet for both LANs, such as 192.168.6.0/24, while every computer has a unique IP address, and can be switched between the 2 LANs without any network reconfiguration on anything, then the answer is yes, if you set up bridging on the machine connected to both of them.

---

### Post by fragglebliss on 2019-09-21
For this you'd be better setting up a separate independent system in a virtual machine on the server and task it with acting as a simple router which can link the systems. I recommend Zeroshell. It's what I use.

---

### Post by SeijiSensei on 2019-09-21
Are the computers in LAN A in the same IP address space as LAN B?  If they both share the same subnet, and addresses are allocated by a router or server running DHCP, you shouldn't need to use the two ports at all. If you want the computer to have the same address when connected to LAN A as it has connected to LAN B, use an address-reservation on the DHCP server based on the computer's MAC address.

If the LANs have separate IP address spaces, like 192.168.1.0/24 for LAN A and 192.168.2.0/24 for LAN B, then the DHCP servers for each subnet should give you the right address when you connect to either.  Again there is no need to use both LAN ports on the computer.

---

### Post by The Cog on 2019-09-21
If they are separate networks (not connected to each other), then no. It would not know which interface to send out on, because they are both on the same network in IP terms (same address space). Don't even think about trying to do that.

---

### Post by webmiester on 2019-09-21
Hi the cog, yes.  Basically they will be on the same subnet but different network. I think your answer makes the most sense.  Thank you. I will try something else then.

---

