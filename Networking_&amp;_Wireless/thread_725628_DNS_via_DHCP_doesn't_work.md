---
title: "DNS via DHCP doesn't work"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by click170 on 2008-03-15
I'm having a problem where Ubuntu (7.10) isn't getting it's DNS information from the DHCP server.  

I verified the server is handing out the correct DNS addresses, all the other computers on the network are fine, but Ubuntu does not seem to clue in to the DNS servers that are passed with the DHCP info.

When I checked the Ubuntu Network config it looks like it was using some strange DNS server from a competing local ISP, the search domain was also set to an incorrect domain.  It seems like somehow Ubuntu configured itself for the competitor's (Shaw Communications) service instead of my ISP's (TELUS).  How this happened, I do not know, I have never connected this machine to a Shaw network since last installing the OS, so I'm not even sure how those incorrect settings got in there to begin with.

If anybody knows a solution to making Ubuntu properly get it's DNS information from the DHCP server I would be very appreciative.
Thanks in advance.

PS.  I have another Ubuntu machine on the network that does not seem to be having these connectivity problems.  Baffling.

---

### Post by Iowan on 2008-03-17
Check **/etc/dhcp3/dhclient.conf**. (hope I got the path/filename right).

---

### Post by chilinski on 2008-03-17
When using DHCP, the dns servers in /etc/resolv.conf will get overwritten every time. You can add them to /etc/dhcp3/dhclient.conf and it will always use those.

I know that doesn't explain why you don't get them from the DHCP server, I've had similar problems and added them to dhclient.conf and don't worry about it any more.

---

