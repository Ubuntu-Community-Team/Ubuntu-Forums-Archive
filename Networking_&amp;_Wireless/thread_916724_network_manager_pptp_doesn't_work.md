---
title: "network manager pptp doesn't work"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by ieduarte73 on 2008-09-11
I have installed network manager pptp with the objective to gain connectivity to my workplace's VPN, however, I can't see the "VPN Connections" on my Network Settings window.

I am running Ubuntu 8.04.1 (Hardy Heron) 64-bit on a Dell Dimension XPS 710 with 2X320GB HD, 4 GB RAM, nVidia 7900GS 256MB, SoundBlaster XFi Xtreme Audio, Cordless Logitech EX110 Keyboard and Mouse.

Any Ideas ?

---

### Post by Steve H on 2008-09-20
I seem to be having the same problem. No "VPN Connections" in my Network Manager menu.

:(

I need to get this sorted to do some work...boo!

---

### Post by Steve H on 2008-09-20
I've got it sorted now, You have to "Unlock" Network manager using your admin password then "Manual Configuration" then "Enable Roaming", then the shortcuts appear on Network Managers LEFT-click menu....

Still can't connect though!!

:D

---

### Post by Isoss on 2008-10-06
Hi,
I am having a similar problem, before my VPN used to work when m ISP allowed automatic (roaming mode) configurations. I only enabled roaming mode, then chose the VPN connection that appeared on the list and the network Icon changed indicating that it's connected. But now my ISP forced static configuration that I had to use Static IP and gateway and DNS ...
For that I have to disable roaming mode, and so when I save config, I am able to login to my LAN (that is by seeing the ISP website and all websites allowed by the LAN),  but I am not able to connect to VPN at all! The connection is still listed in the network manager's menu, but when I click on it nothing happens, icon doesn't change and I don't even get a prompt that VPN failed to connect. When I enable roaming again, and try to connect to VPN, the icon goes around as if connecting, then I am prompted that connection failed, which is obviously due to the static IP forced by the ISP. Any help on this will be appreciated!

---

