---
title: "VNC only works if &quot;Local connections only&quot; is unchecked"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by wastedfluid on 2008-06-11
Hi guys.

Ubuntu 8.04.. on a local network.  Server is 192.168.1.103, client is 192.168.1.102 (Windows Vista)

(SERVER) When I go to Preferences -> Remote Desktop, if I select "Local Connections Only" - VNC will not work!  It says failed to connect to server using VNCViewer from Client(Windows Vista)

However, if I go to Preferences -> Remote Desktop, and UNCHECK "Local connections only" - VNC works from the CLIENT.

:Update:

I have forwarded ports 5900-5999 TCP + UDP to the SERVER machine, and still - it will only work if you uncheck "Local Connections Only"

---

### Post by wastedfluid on 2008-06-11
Well, running a simple nmap, I have found:

"Allow Local Connections" - When it is checked, port 5900/tcp is opened.  When it is unchecked, port 5900/tcp is then closed for listening.

As long as I'm behind a router - I don't think it's too much to worry about.  The port isn't forwarded, so if someoen connected to 5900 - it would just not open.. no big deal.

I solved my own problem.

---

