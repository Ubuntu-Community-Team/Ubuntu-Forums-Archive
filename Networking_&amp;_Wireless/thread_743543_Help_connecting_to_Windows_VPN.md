---
title: "Help connecting to Windows VPN"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2008-04-02
I've read through dozens of threads and howtos and websites but can't seem to find a solution for how to connect my Kubuntu box to a corporate VPN.

From Windows, I'd do the following:

* Use Network Connection Wizard to create a VPN
* Give it a name
* Enter the VPN server IP
* Open it for all users
* Double-click the VPN connection and enter username and password, click Properties
* Options tab - tick all boxes
* Network Management tab - Select Automatic, then TCP/IP, Properties, Advanced
* General tab - untick the box so as to allow normal internet connection as well
* DNS tab - add 10.0.0.2 and the DNS suffix COMPANY.LOCAL
* WINS tab - add 10.0.0.2 and activate NetBIOS with TCP/IP

Using network-manager or the pptpconfig tool I can't find all the same options and the connection fails with a MSCHAP authentication error.

Can anyone help?

---

### Post by gordintoronto on 2008-04-03
MS-Chap is a Microsoft encryption algorithm.  I think the host needs to use a different encryption type in order for you to log on.

Good luck,
Gord


> **pickarooney said:**
> I've read through dozens of threads and howtos and websites but can't seem to find a solution for how to connect my Kubuntu box to a corporate VPN.

From Windows, I'd do the following:

* Use Network Connection Wizard to create a VPN
* Give it a name
* Enter the VPN server IP
* Open it for all users
* Double-click the VPN connection and enter username and password, click Properties
* Options tab - tick all boxes
* Network Management tab - Select Automatic, then TCP/IP, Properties, Advanced
* General tab - untick the box so as to allow normal internet connection as well
* DNS tab - add 10.0.0.2 and the DNS suffix COMPANY.LOCAL
* WINS tab - add 10.0.0.2 and activate NetBIOS with TCP/IP

Using network-manager or the pptpconfig tool I can't find all the same options and the connection fails with a MSCHAP authentication error.

Can anyone help?

---

