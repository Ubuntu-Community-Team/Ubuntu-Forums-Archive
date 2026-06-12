---
title: "Edubuntu terminal server"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by doctor13 on 2007-06-30
Terminal server is presumably installed with Edubuntu install, but I cannot find it. How can I see that it is installed and working?  

My DHCP server is working, but on another linux box as authoritative DHCP server. Does the Edubuntu install with terminal server require a second (non authoritative?) DHCP server?  Is some modification of sysconfig necessary?    

 Many thanks!

---

### Post by dbott67 on 2007-07-01
The 2 servers are probably conflicting with each other (see italicized part below).  I've been fiddling with Edubuntu over the last week or so and found that having another DHCP server on the network can create problems, as Edubuntu ships with it's own DHCP server and configures itself at 192.168.0.254 by default.

If your thin client PCs obtain an IP address from a different DHCP server, they will fail to find the Edubuntu server.

Anyhow, here's what I did for testing purposes:

1. Installed Edubuntu on an old P3-500 machine I had lying around.

2. After installation, I manually configured the network settings on the Edubuntu server to static IP 192.168.1.254 (because my home network is already configured using 192.168.1.xxx).

3. On my desktop PCs, I downloaded & installed VMware server (free download for Windows from [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/) and also in the Ubuntu repos).

4. After installing VMWare server on my other computers, I created an empty VM machine and did a 'network boot' (aka PXE boot).

5. Upon booting, the VMWare machine detected the Edubuntu server, obtained an IP, downloaded the PXE/etherboot image and then abruptly hung up.  After scouring through some Google posts on LTSP & DHCP, I came across this [link]("http://gentoo-wiki.com/LTSP_Server").
[quote=Snippet from above link]
The ugliest solution is to set up two conflicting DHCP servers on the network with the default settings. This has some drawbacks - [COLOR=Red]*the thin clients most probably will be able to get the pxe/etherboot -image from the network since their first dhcp request is a bit special in a way that the client requires the server to send a bootrom image. But the second request (made by the booting kernel) has to choose between two competing servers.*[/COLOR] 
[COLOR=Red]*Usually the dumb DHCP server is authoritative and "wins" most of the requests made by the clients*[/COLOR]. If it isn't, you can improve the bets of your #2 server by making it authoritative. The drawback here is that all non-thin clients will also receive their addresses from your #2 server if you don't limit the operation to specific MAC addresses. IMHO conflicting servers is definitely not a proper way to do this.[/quote]
[COLOR=Purple]*(italics & colour added by me)*[/COLOR]

[COLOR=Black]6. The link above does offer some solutions, but what I did was blacklist the MAC address of the various VMware machines so that my D-Link router would not assign an IP to the VMware clients.  After doing that, the Edubuntu server worked perfectly.[/COLOR]


Some useful links I've found:


_**1. Multiple DHCP Networks:**_
- [http://gentoo-wiki.com/LTSP_Server](http://gentoo-wiki.com/LTSP_Server)

_**2. Getting the remote viewer & shared desktop working:**_
- [http://ubuntuforums.org/archive/index.php/t-406220.html](http://ubuntuforums.org/archive/index.php/t-406220.html) 

_**3. Etherboot for computers without PXE-enabled NICs**_ 
- [http://rom-o-matic.net/5.4.3/](http://rom-o-matic.net/5.4.3/) 

_**4. Ubuntu-specific stuff:**_
- [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP) (note: FL_TeacherTool is not supported in the most recent version of Edubuntu 7.04)

_**5. LTSP Official Docs:**_
- [http://wiki.ltsp.org/twiki/bin/view/Ltsp/](http://wiki.ltsp.org/twiki/bin/view/Ltsp/)
- [http://wiki.ltsp.org/twiki/bin/view/Ltsp/Clients](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Clients)

Hope this helps.  If you have any more questions, I'd be happy to share what little I've learned so far.  I've also added a few screenshots:

1. VMware client (aka ltsp-1)
2. Edubuntu server (showing the /var/log/daemon.log file indicating the DHCP lease, etc.)
3. Thin Client Manager Application
4. VNC from server to ltsp-1 client

-Dave

---

