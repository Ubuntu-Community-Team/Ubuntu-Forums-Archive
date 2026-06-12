---
title: "VPN - multiple classes for employess"
date: 2023-01-03
forum: Networking &amp; Wireless
---

### Post by autominus on 2023-01-03
I have an idea to use a VPN to facilitate network management. I was thinking of using OpenVPN server.

I need multiple classes for employess such as management, administrators, accountants, other employees etc. I have an idea to use a different subnet for each class. 
- management (10.0.2.0/24)
- administrators (10.0.3.0/24)
- accountants (10.0.4.0/24) 
- other employees (10.0.5.0/24)

I want to use a different subnet for each class, because some groups require a public IP. I have the ability to provides a one-to-one mapping of private IP addresses to public IP addresses.

My organization has radius server (FreeRadius) integrated with Active Directory. **Is it possible assigning the user to the appropriate class using radius server?**

Perhaps you have experience of how this could be accomplished. I want to move away from vlans because there are too many of them used. Thus, network management has become too complicated. In addition, there is frequent employee turnover between rooms and buildings.

A VPN would allow users to be mobile. The access switch would have a configured port with vlans for VoIP and Intranet. Internet access only via VPN (IP mapping on gateway with firewall). Of course, for each of the classes, the appropriate access rules on the firewall.

---

### Post by TheFu on 2023-01-14
I control which subnet a VPN user is placed onto through their VPN credentials.  

They get the same a static IP per device.  Each device has different credentials. I issue 2 per user, one for their phone and one for their laptop.  

Phones don't get complete access to the same end-user subnets.  Around 2010, the company CEO had 2 smartphones stolen on a single overseas trip. He wasn't locking the phones even with a pin. Claimed it was too inconvenient.  For months, everyone in his contacts got phishing attempts, even after immediately locking his accounts from any remote use. After that amount of embarrassment, for months, it didn't take anything to get him using a pin.

We don't use MSFT anything and switched from openvpn to wireguard about a year ago.

---

