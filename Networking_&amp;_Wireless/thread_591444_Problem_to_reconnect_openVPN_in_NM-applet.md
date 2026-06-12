---
title: "Problem to reconnect openVPN in NM-applet"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by steamboatsailor on 2007-10-25
Hi, I have an interesting problem with nm-applet...
I set up my openvpn-connection to the office and runs it without problem. 
The interesting point is when I've rebooted and trying to select my vpn-connection again. I can see the name of the vpn-connection but when i click on it, nothing happens.
Ok, I goes into the configuration menu and exports my connection. After that I create a new connection in which I import the the above export. I name it 'office-2' and the new connection runs fine.
Then when i've rebooted the machine the same thing occurs again. But now I have two connection that don't work.
Could someone please give me some ideas of where to begin troubleshooting?

---

### Post by jfrorie on 2007-10-26
> **steamboatsailor said:**
> Hi, I have an interesting problem with nm-applet...
I set up my openvpn-connection to the office and runs it without problem. 
The interesting point is when I've rebooted and trying to select my vpn-connection again. I can see the name of the vpn-connection but when i click on it, nothing happens.
Ok, I goes into the configuration menu and exports my connection. After that I create a new connection in which I import the the above export. I name it 'office-2' and the new connection runs fine.
Then when i've rebooted the machine the same thing occurs again. But now I have two connection that don't work.
Could someone please give me some ideas of where to begin troubleshooting?

Are you getting any errors in the syslog?

Jim

---

### Post by steamboatsailor on 2007-10-28
No, nothing in the syslog or other logs.
The application is "alive" in the meaning that I can configure a new vpn connection and I can also see the cursor marker when I'm moving the cursor over the window.

---

### Post by jfrorie on 2007-10-28
> **steamboatsailor said:**
> No, nothing in the syslog or other logs.
The application is "alive" in the meaning that I can configure a new vpn connection and I can also see the cursor marker when I'm moving the cursor over the window.

This is sounding buggy. I'm seeing some traffic to this conclusion.

Some people were having success in turning off ipv6.  Beyond that, I'm out of ideas.

---

### Post by steamboatsailor on 2007-10-28
I've tried that too. But no success. I guess it's time to download the source and run in under debugging then...  Thanks for advices so far.

---

### Post by RecoveringWindowsAddict on 2007-10-29
I suspect I am suffering the same problem, but am not sure. I only recently got nm-applet & openVPN working and connecting to my office IPCop. I upgraded to Gutsy last night, and now I am in trouble. Creating a new connection does not help, and nm-applet gives no feedback as to what is not working. I, being a novice, eventually figured out how to start OpenVPN from the command-line, but it is tedious and leaves many issues in an unsatisfactory state, like routing, etc...

I also tried a couple of other VPN GUIs, none of which helped...

---

