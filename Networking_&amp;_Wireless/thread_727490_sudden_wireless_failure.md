---
title: "sudden wireless failure"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by jargon_ on 2008-03-17
I'm using Ubuntu 7.10 on a laptop with a Linksys WPC54G wireless adapter. I had problems getting the wireless network going in the first two days, but after I built a driver with ndiswrapper, my wireless worked fine for over a month with no failures whatsoever.

Just today, however, I switched on my laptop, and it failed to connect through the adapter. I click on the network manager applet and there was no longer a button for wireless networks. I tried using manual configuration, but the selection for wireless networks was missing completely. I only see the configurations for Wired Connection and Modem Connection.

I put iwconfig into the terminal and got the following:

lo        no wireless extensions.

eth0      no wireless extensions.

I honestly don't know what went wrong. I've already tried re-installing the network manager, but that didn't work. What's more, I'm a complete newb.

I hope you guys can help me get this fixed. I really like Ubuntu and I don't want to be forced back into WinXP by a technical difficulty. 

Thanks! :)

---

### Post by jargon_ on 2008-03-17
I remember that just before my last reboot, when everything was still working right, I went on the terminal and input <sudo apt-get purge>, and one of the items purged was something related to ndiswrapper. That may have been the cause of the problem. I'll try re-compiling ndiswrapper and the wireless driver again and see if that works.

---

