---
title: "Ubuntu Server w/ Ubuntu Desktop Clients (user auth.)"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by mvip on 2007-03-18
Hi Ubuntu folks,

With the Desktop improvements of the latest releases of Ubuntu Desktop I'm seriously considering migrating on of the offices I administrate completely over to Linux. All the software that is not available for Linux will run under Wine, so no problems as far as that is concerned. 

My thoughts is to install a server with Ubuntu Server, and then Ubuntu Desktop on the clients (a handful of them). The only thing I really need from the server is to share files, but I would also like to have central user management. 

Now, as far as I know, there are two ways to go when it comes to central user authentication; Kerberos or Samba w/ PDC. Kerberos seems to be the hardcore Unix-way to do it, while Samba PDC is more like a mixed-enviroment solution. Both of these solutions may use OpenLDAP as a backend, which is great. And as for the file-sharing, I guess NFS goes with Kerberos, while obviously Samba takes care of the Samba file-sharing.

What I really want to know is what kind of experience people have when it comes to this. Which is the most 'ubuntu:ish' way to go, and what would work with the least amount of tweaking/hacking?

I know Fedora supports PDC user-logins out of box, but i'm not sure if Ubuntu Desktop does the same.

---

