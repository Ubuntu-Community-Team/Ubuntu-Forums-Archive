---
title: "Logging on to Windows Domain"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by Tropicalbound on 2014-08-06
OK. I can now log on with my Active Directory domain account! However, it appears the domain account does not have administrative priveleges. Here is what I have done:


Installed OpenSSH server
Installed PowerBroker Identity Services
Joined the domain
Installed krb5-user
Added the Domain Admins group to /etc/sudoers


At this point, I can log with the domain account. However, I cannot install the VirtualBox add-ins (cannot mount drive). I have confirmed that the account is set up as an Administrator and I have duplicated the group membership that the local account has. Still, no joy.


Can anyone help getting admin priveleges for the domain account?


Thanks!!


TB

---

