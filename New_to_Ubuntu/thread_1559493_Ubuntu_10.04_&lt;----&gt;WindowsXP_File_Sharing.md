---
title: "Ubuntu 10.04 &lt;----&gt;WindowsXP File Sharing"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by zer010 on 2010-08-23
Firstly, there is a router setup between the two computers.  
ISP--->Cable Modem--->Router{______>Ubuntu10.04 {------->WinXP

As the Title indicates, I want to share and/or transfer files between the two computers.

GUI and Terminal explanations are both welcome.

Thanks!

---

### Post by mapes12 on 2010-08-23
The key to this solution is getting windoze to "share" correctly. I have XP. On the MS box go to the Folder/Printer/Whatever you want to share, right click and enable sharing. On the Ubu machine go Places>Network>[Name of your MS Workgroup]>[Name of the folder]

You should then be able to transfer stuff between the 2 boxes.

If you're running Ubu 10.04 there should be no need to install Samba or anything like that. Just simple sharing should do the trick.

---

### Post by zer010 on 2010-08-23
Cool! Thanks! That sounds a LOT easier than some of the other stuff I've read.  I'm surprised I won't have to install Samba.  Do I have to set any special IP addresses or anything?  This method works with a router?

---

### Post by pricetech on 2010-08-23
Your diagram isn't entirely clear.  Do both the windows box and the Ubuntu box connect to the router ??

Go ahead and install Samba, it's a piece of cake.
System - Administration - Synaptic Package Manager
Search for system-config-samba which will install both Samba and the GUI administration tool.  Once installed go to System - Administration - Samba to configure shares on your Ubuntu box.

After that the easiest way to connect is through Places - Connect to Server.  Call it a windows share, type in the IP and sharename and connect.

You'll need the credentilals you use on the windows box to connect to it.  Same with connecting to shares on the Ubuntu box from windows, you'll need your Ubuntu credentials for that.

If that doesn't do it, post back with any errors and we'll help you sort it out.

---

### Post by zer010 on 2010-08-23
Yes, both the WinXp box AND the Ubuntu box are wired to the router. Sorry, for the crappy diagram.:eek:

---

### Post by mapes12 on 2010-08-24
> **zer010 said:**
> Cool! Thanks! That sounds a LOT easier than some of the other stuff I've read.  I'm surprised I won't have to install Samba.  Do I have to set any special IP addresses or anything?  This method works with a router?If your router is providing your LAN with IP addresses via the DHCP service (most do) then you will not have to worry about IP addresses. If sharing is configured correctly on MS then your MS machine will be broadcasting the share to your private LAN IP addresses, but not outside the LAN.

Go into Control panel in MS and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in MS is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Then on the Ubu machine go the route I said in my last post. You should now be able to move stuff between the 2 machines.

---

