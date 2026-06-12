---
title: "Dynamic DNS services and enom"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by poundjd on 2008-12-05
Hello All,
         OK i stood up my ubuntu 8.04 server, loaded eBox-Platform on it and I wnat to configure e-mail.


I have a domain (pound.us) from enom, and they provide a fair amount of service.  But I want to have all e-mail to pound.us sent to my home e-mail server (in the ebox server).  So I set the box up as ebox.home.pound.us.  Also my IP is dynamic.  So I want to be able to have enom hold the DNS records for pound.us, and an mx record  that sends all e-mail of the form [email]user@pound.us[/email] to the ebox.  I think I have to do two things, 1 get the ebox to keep my dns entries up to date at enom, and then update the MX record on a regular basis.  also other than the one DNS entry for ebox i don't wnat any of the home.pound.us addresses identified outside of my local network.

---

