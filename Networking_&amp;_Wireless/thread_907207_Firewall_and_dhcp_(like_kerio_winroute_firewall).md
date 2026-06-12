---
title: "Firewall and dhcp (like kerio winroute firewall)"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by tof233 on 2008-09-01
Hi,
I would like to find a system to manage a firewall with an account system for a school residence like kerio winroute firefwall.
For exemple we create the account 'test' allowing 80 110
When the guy wants to access to internet, he goes to a login page. He type his login (test) and his password and the he has the access for 80 110 ...
Does someone now a system like that?
Thanks

---

### Post by nicedude on 2008-09-01
I suppose by this 80 110 you mean you want a test account that has access to ports 80 and 110 to use web and pop email. If that is so then you can make an account called test and then the built in linux firewall is IPtables but it is command line only so you will need to install a frontend program to have a GUI to control it. I use guarddog as my frontend and it is easy to use and I believe you could make per user permissions in there rather easily. guarddog is in the repositories so is easy to install.


Hope that helps you do what you need to do.

---

### Post by tof233 on 2008-09-02
Thanks for your help
I tried it but I can't create account.

More precisely, this is what I'm seeking:
"User-specific access management
Each user in the network can be required to log in to Kerio WinRoute Firewall before connecting to the Internet. That allows for restrictive security and access policies to be applied based on the specific user, rather than the IP address"

Doe someone know another one?

---

