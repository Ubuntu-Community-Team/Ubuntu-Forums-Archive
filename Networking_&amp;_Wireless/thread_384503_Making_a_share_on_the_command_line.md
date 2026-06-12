---
title: "Making a share on the command line"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by Grout58 on 2007-03-14
I have a Dapper LAMP server and would like to set up shared drives so I can access them from other linux and windows boxes on my home network.  How can I set up a share from the command line?

---

### Post by cyberdork33 on 2007-03-14
if you want to access shares from windows, the best method would be to use a samba server... you need to edit the config file to setup the shares.

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server)

This guide assumes you have a full gnome desktop, but you can use nano in place of gedit to edit files, and sudo in place of gksudo

---

