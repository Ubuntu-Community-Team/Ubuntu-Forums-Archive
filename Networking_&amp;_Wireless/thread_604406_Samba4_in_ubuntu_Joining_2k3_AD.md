---
title: "Samba4 in ubuntu? Joining 2k3 AD?"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by zarya0 on 2007-11-06
I have downloaded and compiled samba4 today and I'm trying to join our Windows 2003 Server Active Directory here at work.

our domain: melhus.vgs
win2k3 server:melhus.melhus.vgs
dns server: same as 2k3 server.
root@meheb-stiek:/# ./usr/bin/net ads join -U [email]Administrator@MELHUS.VGS[/email]
[email]Administrator@MELHUS.VGS[/email]'s password: 
Using short domain name -- MELHUS-VGS
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Deleted account for 'MELHUS-STIEK' in realm 'MELHUS.VGS'
Failed to join domain: Type or value exists
---------------------------------------------------------------------------------------------------------------
One noticeable thing is that my computer name is meheb-stiek, and it should join the AD with meheb-stiek not MELHUS-STIEK!
Is samba4 suppost to have it's own LDAP AD server? I only wish to join ubuntu computers to an existing Windows Active Directory!

There is not enough sufficient information on joining an existing AD with Ubuntu.

Please help me! :P

---

