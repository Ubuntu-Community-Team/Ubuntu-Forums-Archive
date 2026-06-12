---
title: "Router DNS resolving issues"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by ash71 on 2007-10-19
This one is strange and happens in many other distros.
My router is D-LINK DSL 500T it works fine in windows,
But in most linux distros resolving dns fails when using the router ip  address
(192.168.1.1) the only program able to resolve dns is konqueror for some reason or another.

I can set the dns to the ones set in the router and it works fine i can also connect using ip addresses.
But setting the dns manually is a bad workaround since the dns address might change and then i need to set them again.
(i know how to make them stay and not change to the ones in the router thats not the problem)

Network specs:
Router: D-LINK DSL 500T using NAT And DHCP for home lan.
Network card: NVIDIA OnBoard network card (NVIDIA nForce Networking Controller)

---

### Post by _samba_ on 2007-10-19
Isn't your router supposed to pick up the external DNS IP from your ISP? Try to  flash your router with  a new firmware from DLink and see what happens.

---

### Post by ash71 on 2007-10-19
My router allready has the latest firmware (v2.0)
and it does receive the dns servers from the isp
then it sets itself has the dns server via dhcp and handles the dns resolving.

---

### Post by noob12 on 2007-10-19
Yes.  I have noticed this issue with the Linux and the DNS proxies in some popular routers; resolution fails with Linux whereas it works fine with Windows.  You can use the technique in this posting to workaround that by going directly to the ISP's DNS servers or to other servers (like OpenDNS):  
[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

You may also be able to disable the DNS proxy in the router.

---

### Post by ash71 on 2007-10-19
These are workarounds which should allow to use ubuntu untill this is fixed, Still they are not perfect, If someone wants to use is isp dns and they are dynamic he will have to set them again each time they change since he cant use the dhcp to set them. (unless the router supports sending the dns servers instead of sending is own ip and acting as a dns proxy/relay.
and if there are many linux machines on that network this is surely bad.

The question now is to find what is causing it to fail and hope for a possible fix.

Edit: i cant find how to disable the dns proxy/relay in the router i dont think this is possible...

---

### Post by noob12 on 2007-10-19
You might want to file a bug on launchpad.  I suspect it is a bug in the implementation of the DNS proxy in the router but there might be tweaks one can do on the resolution side to be more resilient.

---

