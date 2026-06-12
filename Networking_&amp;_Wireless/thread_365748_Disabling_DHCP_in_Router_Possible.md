---
title: "Disabling DHCP in Router Possible?"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by true_friend on 2007-02-20
Hi folks
i use internet throuhg a shared ADSL. Basically there is a proxy server which connects all network to the internet but i only use internet directly from Router. The Setting is such that router cable comes to Network Hub and then it goes to proxy server. Server is working through DHCP but the Router is also working on DCHP.
now when there is a power failure after the recovery the router provides its ip through DHCP before the proxy server provides so it creates IP confilicts and problem to use internet. My Question IS This IS IT POSSIBLE TO DISABLE DHCP IN ROUTER SO A FEW PCS LIKE MINE AND PROXY SERVER ONLY COULD USE INTERNET THROUGH ROUTER DIRECTLY. and only proxy server work on DHCP.
Regards
True_Friend

---

### Post by gradedcheese on 2007-02-20
short answer: yes, you certainly can disable it.  I've never seen a router where you can't.

how?  'depends on your router, read the documentation or poke around its web interface.

---

### Post by true_friend on 2007-02-20
thnx i try to find some information on it.
Regards

---

### Post by Erlander on 2007-02-20
With my Belkin router I've had its DHCP server running until now.

Yesterday I turned it off and manually entered the necessary settings in each pc.

In Edgy System/Admin/Networking/Wired Connection/Properties

I'm doing it for fixed addresses for Mythtv and so I can set Samba to use a Wins server.

Rob

---

### Post by true_friend on 2007-02-25
Got it i disable router's DHCP.
working fine manually.

---

