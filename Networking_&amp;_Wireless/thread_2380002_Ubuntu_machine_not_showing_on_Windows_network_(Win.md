---
title: "Ubuntu machine not showing on Windows network (Win7 + Win 10)"
date: 2017-12-12
forum: Networking &amp; Wireless
---

### Post by MobileTechie on 2017-12-12
I have my ubuntu box with samba shares working OK. I can access them as expected as long as I find them using the ip address: \\192.168.1.100\sharename

But browsing through Windows network on Win 7 or Win 10 boxes, I cannot see the Ubuntu machine. All machines are running off DHCP from my router, with the router's own IP being set as the DNS server. On the router's network map, the ubuntu box shows up with the correct name and IP, so the router appears to know where it is OK. Ubuntu does not appear to be running a firewall and turning the Windows one off makes no difference. They are both on the same WORKGROUP as per smb.conf settings.

I cannot ping the ubuntu box by name from windows.

---

### Post by MobileTechie on 2017-12-19
Solved myself now.

---

### Post by slickymaster on 2017-12-19
It would be nice of you to share with the rest of the community what was the solution you found to make it work.

---

