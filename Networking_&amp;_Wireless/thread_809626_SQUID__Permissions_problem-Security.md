---
title: "SQUID  Permissions problem-Security"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by chrismarsh on 2008-05-27
Scenario:

Software Development firm. Users are allowed internet access, but to prevent taking source code out of the company, all mails sites, chat sites, File sharing sites and P2P sites are blocked through squid. This is done through ACLs in squid and this thing is working very fine. Server has no proxy set, so all sites are accessible in the server. Machines over the LAN are connected to this squid server, and hence, all the above said sites and job search sites are disabled.

The problem:

Some users do need to access gmail or orkut for any genuine purpose, or the work allotted to him is over, so they can do whatever they want. In this case, the present solution is remove that IP address from the ACL and restart squid. This is not a good solution as a network administrator needs to sit with this all the time. Moreover, the user has still access to the source code and the risk still exists. (Or the files needed to be moved from the system before allowing these sites, which is not fair and practical).

Solution(wat i thought was):

 All users get only allowed sites. However, if they need access to mail sites, they should logout and login as guest. Guests can access all sites without any ACL restrictions. Guest account normally does not have access to home folder of other users or to /var/www, so that he can email the source code. However, the risk here is that while logged in as normal user, he could copy files to /tmp and then login as guest and mail them from /tmp. 

So what I need to get is:

1) Load different set of Squid ACLs based on remote user logins.
2) Keep a separate temp area for guest with 777 permission to guest and 000 permission to normal user. (I don't know how to change temp path)
3) I want to know which are the other locations other than temp folder, that are accessible by both. (Write by guest and read by others is OK. I just want to prevent write by others and read by guest).
4) How can a geek bypass this security restriction

---

### Post by Monicker on 2008-05-27
4)

Physical access restrictions?  What would stop someone from copying the information to a thumb drive and walking out with it?

Egress filtering?  An ssh tunnel to an external server, via a port not blocked at the firewall, and transfer to your heart's content.

---

### Post by chrismarsh on 2008-05-27
-->physical restrictions
usb disabled
cdrom disabled


can i  have a separate /tmp folder for the guest

---

