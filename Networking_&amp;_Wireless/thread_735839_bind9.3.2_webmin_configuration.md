---
title: "bind9.3.2 webmin configuration"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-26
Dear experts:
I use Webmin. I want to configure my two domains using bind 9 from my house. I can do this either with Webmin or the regular way that Linux professional. I just need to know where to start... I am familiar with DNS configuration using Windows AD. I have never configured bind.  I thank you for your help. M

---

### Post by Eiríkr on 2008-03-26
I wasn't familiar with any DNS configuration at all, but am comfortable with the CLI, and found [this DNS HOTWO]("http://tldp.org/HOWTO/DNS-HOWTO-5.html") to be most instructive.  The link here is to Chapter 5, which is where the author gets down to the brass tacks of configuration.  One thing I noted was that relative paths to zone files as used in the HOWTO don't seem to work under Gutsy, but absolute paths do just fine.  

HTH,

Eiríkr

---

