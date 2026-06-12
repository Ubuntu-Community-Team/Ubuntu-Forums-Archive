---
title: "Trying to diagnose mystery problem remotely...(VNC)"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by jorwex on 2008-04-14
So I'm trying to fix my cousin's VNC server on his computer in another state cuz he's going out of the country for a year and would like to use his pc once and a while.  I've been dictating things on the phone for his mother to check, but I'm really stumped this time...

We had things working on the laptop that he took to Korea. He was on a wireless network from a WRT54G or GS (not sure), but he took that with him. He left another WRT54G (or GS) with him to run his desktop on that he wants to access. 

His WAN IP changed during his setup of the new router (which I thought was a little odd, but maybe it isn't). His desktop is 192.168.102 and the laptop that he took was .103. 

In my mind, all that should have changed was to make a new entry in "Applications and Gaming" (port forwarding) for 192.168.102 for port 5900 (VNC), and to go and change the settings in the Remote Desktop menu in Ubuntu (which i've had his mom do for me on the phone). 

I can ping his new IP fine, but the VNC requests keep timing out.


Are there any other wrt54g settings to check? I've unchecked "Block Anonymous Internet Requests" and don't know what else to do. I'm 90% sure he doesnt have any ubuntu firewalls. I'll find that out while I get some replies :)

thanks!

---

### Post by jorwex on 2008-04-15
Anyone?

---

