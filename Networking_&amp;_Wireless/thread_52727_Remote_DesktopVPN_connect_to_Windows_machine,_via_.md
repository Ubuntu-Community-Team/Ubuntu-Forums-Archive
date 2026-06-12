---
title: "Remote Desktop/VPN connect to Windows machine, via Ubuntu?"
date: 2005-07-28
forum: Networking &amp; Wireless
---

### Post by amrust on 2005-07-28
Hello, everyone.

I've been enjoying playing around with my new Ubuntu install ( over 2 weeks now, and no problems yet!), and I'm wanting to get down to some actual work integration with this laptop. My question:

How do I get my Ubuntu laptop to connect to a Windows 2000 machine at work? I can access the machine remotely via Windows, using a VPN program. I guess I need the "Linux equivelants", whatever they may be. Can anyone help me find out what I need to set up or what packages I need to install, to connect to a Windows machine from home, using my Ubuntu? I'd like to actually try doing some work from home on my Linux machine, if I can connect to the Windows network at the office, that is.

Once this process is completed, will I really be able to navigate in a Windows desktop window, on my Linux machine? If so, that's exactly what I need to permanently make the switch.

Thanks in advance!

---

### Post by cwaldbieser on 2005-07-28
"krdc" or "rdesktop" are the remote desktop programs-- I think Ubuntu has one of them installed by default-- might be called something like "Terminal Server Client" in the menu?

For your VPN connection, do you use a Microsoft VPN or a Cisco VPN?  For a Cisco VPN, you can try "vpnc".  For a Microsoft VPN, I use the "pptp" driver.

---

### Post by amrust on 2005-07-28
Cisco VPN seems to be what I need. 

I have installed the vpnc package, but I can't find it anywhere in the menus.

Edit: I see now it is command-line driven. I will try building a .conf file tomorrow, when I get back to look up the required settings.

Are there any GUI-based Cisco VPN clients? Or is vpnc the best option?

Thank you!

---

### Post by gruepig on 2005-07-29
I've installed vpnc on a number of Linux systems. My setup instructions are here: 
[http://yellowpigs.net/computers/vpn](http://yellowpigs.net/computers/vpn).

---

