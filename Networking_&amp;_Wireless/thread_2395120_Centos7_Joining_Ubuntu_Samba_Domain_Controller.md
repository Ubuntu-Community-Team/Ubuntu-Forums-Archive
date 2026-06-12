---
title: "Centos7 Joining Ubuntu Samba Domain Controller"
date: 2018-06-27
forum: Networking &amp; Wireless
---

### Post by erudes91 on 2018-06-27
Hello everyone!

I have an Ubuntu Samba Server AD style, that I use to centralize my  logins for windows clients, and it works just fine, Windows machine have  full access to the domain and can login and even share files, also I  can manage the AD through RSAT.

I've been trying for a while to get a CentOS7 client machine to join the  domain and I have succesfully done it, but when trying to login using:

su - [EMAIL="domainuser@domain.lan"]domainuser@domain.lan[/EMAIL], it tells me the user does not exist.

I installed Winbind Client, trying to run wbinfo -u, and it tells Error Looking Up Domain Users WBC ERR WINBIND NOT AVAILABLE.

As an additional piece of information, the only way I could joined the  machine to the domain was by adding manually through /etc/hosts the IP  of domain controller and their name. I have correctly configured DNS on  Samba Sever with correct records, and also resolv.conf from Centos  client points there.

Any ideas why this can be happening? If anything like screenshots or config data is needed let me know!

Thank you!

---

