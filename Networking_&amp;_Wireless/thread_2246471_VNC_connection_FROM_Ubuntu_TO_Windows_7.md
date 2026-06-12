---
title: "VNC connection FROM Ubuntu TO Windows 7"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by kolibri on 2014-10-01
I have my computers set up to successfully connect FROM Ubuntu 14.04 to Windows 7 using RDP (Remmina client on Ubuntu), it was a bit of a headache, but I got it done.

However, I have one program on my Windows 7 box that won't start in a Remote Desktop environment.  If I am physically at the computer and start  the program running, I can continue using it when logging in remotely using RDP and Remmina.

I thought that the program (it's a license manager issue) wouldn't recognize a VNC connection.  So, I'd like to get a working VNC connection between my computers.

I've tried using Remmina and Remote desktop Viewer (which is Vinagre) to connect to my Windows 7 box with these clients:  TigerVNC, UltraVNC, and TightVNC.  I get one of two errors, "no password set" or "too many security errors" or just "connection refused".  I know the standard ports are open because RDP works, and pinging works.

Any suggestions on how to go FROM Ubuntu TO Windows?  My search here turned up mostly FROM Windows TO Ubuntu threads, or RDP threads.

(Alternatively help getting the license manager to ignore I'm RDP-ing into the Windows box would also work)

Thanks

---

### Post by TheFu on 2014-10-01
I've had a similar issue.  If you shared the exact license manager involved, perhaps someone can help with specifics?

---

### Post by weatherman2 on 2014-10-01
To be clear: you tried to install a VNC server on the Windows 7 machine, then tried vinagre (and other clients) on the Ubuntu machine but you still can't connect?

The ports for VNC (default 5900) and RDP (default 3389) are different FYI.  But if you test this on a local network, without a router firewall blocking you, open ports should not be important.

Also FYI, VNC itself is not secure - only the password is encrypted when you login.  Nothing else is.  If you use VNC over the public internet, it's not going to be secure unless you use a VPN.

---

