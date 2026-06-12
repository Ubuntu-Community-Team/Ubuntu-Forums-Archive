---
title: "Cisco VPN Client Software"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by A4orce84 on 2008-08-30
Hey Guys,

I am trying to load VPN software onto Ubuntu, I followed the directions located here:

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

And I pretty much got everything installed. However, on step #9, after modifying my profile and initiating the final sudo command, my terminal displays this:


Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.

I've done a bit of searching, but got confused with the 'kernal module' stuff. If anyone can offer any assistance, I would GREATLY appreciate it. Thanks!

--A4orce84

---

### Post by A4orce84 on 2008-08-30
Anyone?

---

### Post by casevh on 2008-08-30
Have you done step 7? 

Does it generate any errors?

casevh

---

### Post by eugen_nicoara on 2009-02-05
You might have to reinstall the CISCO VPN client (if that's your case) after you install a new kernel.

---

