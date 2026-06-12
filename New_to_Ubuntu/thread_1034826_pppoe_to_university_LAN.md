---
title: "pppoe to university LAN"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by sharat87 on 2009-01-09
I have been using pppoeconf to configure and connect to internet with a modem at my home. Now I am back to my university with my laptop and the connection here is running through a proxy.

The connection is working on live-cd without any configuration... just the proxy address. I am writing this from there.

It shows as 'Auto eth0' when i click on the tray icon (network icon). but in my installation which was previously configured with pppoe, it shows as 'device is unmanaged' in the same place as 'Auto eth0' was shown in the live-cd.

Please help...

---

### Post by sahmed001 on 2009-01-09
> **sharat87 said:**
> I have been using pppoeconf to configure and connect to internet with a modem at my home. Now I am back to my university with my laptop and the connection here is running through a proxy.

The connection is working on live-cd without any configuration... just the proxy address. I am writing this from there.

It shows as 'Auto eth0' when i click on the tray icon (network icon). but in my installation which was previously configured with pppoe, it shows as 'device is unmanaged' in the same place as 'Auto eth0' was shown in the live-cd.

Please help...


The easiest fix is to edit the file 
 /etc/NetworkManager/nm-system-settings.conf

And change the section

[ifupdown]
managed=true


It probably says managed=false now

---

