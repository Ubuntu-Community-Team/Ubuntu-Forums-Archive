---
title: "Cisco VPN Client/DNS issue"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by ubnoob17 on 2008-07-24
Hi, I'm UbNoob17, and I'm a Windowsaholic...

However, I'm trying to learn here...please be gentle :)

I've just loaded the Cisco VPN Client 4.8.2 on my Heron 8.04 workstation at home. Everything is working great, and I'm using the TS client to remote back to my Windows PC in the office using RDP.

However, the DNS info on my local machine just stopped working while I was connected to the VPN, and I don't know how to troubleshoot, much less fix the issue.

What I CAN do:
[LIST]
[*]Sucessfully log onto my work VPN
[*]RDP to my office Windows PC
[*]Launch a local session of Firefox on my Ubuntu box and surf the web.
[/LIST]

However, after using the VPN connection for a couple of hours, DNS could no longer resolve (my work's, via the VPN tunnel) on my local machine and my local browser stopped working. I verified that DNS was still working at the office by hitting the internet on the Windows box I was remote controlling.  Therefore, it is a DNS issue on my local box, not at the office itself.

Closing and reopening my VPN connection resolved the issue, however, is there anything I could have done locally to fix it without closing then relaunching the VPN client?

Thanks in advance!!!

---

### Post by superprash2003 on 2008-07-24
you could permanently set your DNS servers to the one which you use when not connected to the VPN.. cause the office dns servers dont seem to be working.. 
read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. opendns servers used here, but you could replace it with whatever dns servers you wish

---

