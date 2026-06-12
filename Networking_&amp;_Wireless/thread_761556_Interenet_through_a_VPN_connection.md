---
title: "Interenet through a VPN connection"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by NoRemorse on 2008-04-21
Hi, I'm new here (and to Ubuntu in general) so bear with me and my problems.

I recently set up a Ubuntu box to act as a samba/ftp/vpn server.

My issue is that my windows based VPN clients are unable to resolve domains into IPs when connected to the VPN.

I could allow split tunneling on  the clients, but then names of the computers and servers on the LAN don't get resolved.

Is there any way around this? I obviously have something set up incorrectly.

Best regards,
Brian

PS)I barely know what I am doing, I know about enough to get these services running, but the intricacies of networking aren't my thing unfortunately

---

### Post by SpaceTeddy on 2008-04-21
once you are connected to the VPN, can you stil reach your dns servers (this would be the most likely case why your name resolveing does not work).

on the windows box, once connected, open a command shell (cmd) and type > ipconfig /all

there should be something about dns servers in there. take the ip's and try to ping them. If that works, try what happens when you resolve something manually. Use this command to do so
```
nslookup www.google.de
```
and see what happens. 

The other possibility is that your VPN server does not allow ip_forwarding or does not perform NAT operations to hide your VPN. IN either case, your VPN would seem to be broken. Can you give me an example howto on how you setup the vpn ? or do you remeber anything about "enableing nat" or "enable masquerarding" or "enable ip forwarding " ?

lots of question - hope we can answer them all :)

btw: i have NEVER used windows VPN - always openvpn... so i might need to look some stuff up too.

---

### Post by NoRemorse on 2008-04-21
I actually found a solution. I am using guidedog for routing and ip forwarding, seems to have solved the issue.

---

### Post by Knightwise on 2008-07-01
Oh boy ! :) That saved my day. Installed Guiddog, setup nat and i'm good to go ! Thank you very much.:popcorn::popcorn:

---

