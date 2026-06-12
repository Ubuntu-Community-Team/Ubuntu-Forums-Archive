---
title: "DNS Changes on Ubuntu Server 12.04?"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by danappleby2114 on 2015-03-27
Hi Everyone here's the low down.

I am in the process of migrating our ubuntu 12.04 lts web server from an old copper connection to a faster fibre optic connection on a cisco meraki firewall. 

It has multiple websites hosted within apache2 with different domain names and sub domains configured. 

The webserver is a virtual machine on a vmware esxi server (192.168.0.206) and the web server has an address of 192.168.0.30.

I am planning on a 1:1 address mapping within the meraki firewall (outermost device before router) of the web server to a new public IP address and then update this within our DNS settings on the domain providers website. 

My question is, is there anything that needs doing on the ubuntu server itself? As in IP changes to reflect the new one?

Many Thanks in advance.

---

### Post by slickymaster on 2015-03-27
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by SeijiSensei on 2015-03-27
Apache virtual hosts determine which site to display based on the textual hostname in a URL (the site's ServerName or ServerAlias).  As long as the public DNS mappings and packet forwarding are correctly configured, you shouldn't experience any problems.

---

### Post by danappleby2114 on 2015-03-27
Thanks for your reply!!

Thought so. I've configured ServerNames/Aliases and sub domains on my own ubuntu forum but this is my first corporate migration so checking all corners!

---

