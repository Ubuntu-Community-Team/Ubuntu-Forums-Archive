---
title: "Failed Wired Connection"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Tekmo on 2008-09-27
Here's a summary of my problem.  My apartment offers high-speed internet, which uses PPPoE.  My ISP gives me an account to authenticate with which I use to get internet.  I try this in windows and it works, so I then try to set it up in Linux.

I switch to Ubuntu and it (randomly) will fail, but usually only at startup.  If it works the connection usually stays up for a while, although it occasionally will fail while running.  After doing some troubleshooting, I find out that there is a router between my wall connection and whatever modem is connecting me to my ISP.  I can actually log into this router using the factory defaults, but haven't changed anything.  This router is a NETGEAR WGT624 v3.

Every time the connection fails it is because I cannot connect to the router.  I cannot ping it, all DHCP requests get no response, nothing.  However, when it is working I can turn the PPPoE connection off and still access the router.

I don't think it is a problem with the router or the physical connection because Windows never fails to work, ever.  I'm guessing it has something to do with an Ubuntu problem in controlling the ethernet adapter, but I have no experience in how to troubleshoot this kind of thing.

So my question is how can I verify if it really is a problem with the ethernet adapter?

---

### Post by cariboo on 2008-09-27
If you can log on to your router, it isn't a problem with your nic. Just to cover the bases have you:

1 Installed the pppoe driver.
2. Run pppoeconf

You will have to run pppoeconf as root if you haven't run it.

Jim

---

