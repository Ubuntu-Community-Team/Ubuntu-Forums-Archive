---
title: "Waking the sleeping printer"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-08-01
Just got a new printer HP OfficeJet Pro 8500 a910. Works very well....except when we do not print on it for a while...then it goes to sleep and does not wake to print.

Here is the debug report:
D [01/Aug/2011:20:10:32 +1200] cupsdIsAuthorized: requesting-user-name="pj"
D [01/Aug/2011:20:10:32 +1200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Aug/2011:20:10:32 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:32 +1200] cupsdReadClient: 18 WAITING Closing on EOF
D [01/Aug/2011:20:10:32 +1200] cupsdCloseClient: 18
D [01/Aug/2011:20:10:32 +1200] cupsdReadClient: 15 POST / HTTP/1.1
D [01/Aug/2011:20:10:32 +1200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [01/Aug/2011:20:10:32 +1200] cupsdAuthorize: No authentication data provided.
D [01/Aug/2011:20:10:32 +1200] cupsdReadClient: 15 1.1 Get-Notifications 1
D [01/Aug/2011:20:10:32 +1200] Get-Notifications /
D [01/Aug/2011:20:10:32 +1200] cupsdIsAuthorized: requesting-user-name="pj"
D [01/Aug/2011:20:10:32 +1200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [01/Aug/2011:20:10:32 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "lo" = localhost:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "eth0" = 10.1.1.28:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "ham0" = 5.39.96.225:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "lo" = localhost:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "eth0" = [v1.2001:db8:1:0:221:70ff:fee6:93d6]:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "eth0" = [v1.fe80::221:70ff:fee6:93d6+eth0]:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "wlan0" = [v1.2001:db8:1:0:221:6aff:fe29:e538]:631
D [01/Aug/2011:20:10:42 +1200] cupsdNetIFUpdate: "wlan0" = [v1.fe80::221:6aff:fe29:e538+wlan0]:631
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 POST / HTTP/1.1
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdAuthorize: No authentication data provided.
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [01/Aug/2011:20:10:43 +1200] Get-Job-Attributes ipp://localhost/jobs/32
D [01/Aug/2011:20:10:43 +1200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/32) from localhost
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 POST / HTTP/1.1
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdAuthorize: No authentication data provided.
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [01/Aug/2011:20:10:43 +1200] Get-Job-Attributes ipp://localhost/jobs/33
D [01/Aug/2011:20:10:43 +1200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/33) from localhost
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 POST / HTTP/1.1
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdAuthorize: No authentication data provided.
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 1.1 Cancel-Subscription 1
D [01/Aug/2011:20:10:43 +1200] Cancel-Subscription /
D [01/Aug/2011:20:10:43 +1200] cupsdIsAuthorized: requesting-user-name="pj"
D [01/Aug/2011:20:10:43 +1200] cupsdMarkDirty(-----S)
D [01/Aug/2011:20:10:43 +1200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdAuthorize: No authentication data provided.
D [01/Aug/2011:20:10:43 +1200] cupsdIsAuthorized: username=""
D [01/Aug/2011:20:10:43 +1200] cupsdSendHeader: 15 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [01/Aug/2011:20:10:43 +1200] cupsdCloseClient: 15
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdAcceptClient: 15 from localhost (Domain)
D [01/Aug/2011:20:10:43 +1200] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdAuthorize: Authorized as pj using PeerCred
D [01/Aug/2011:20:10:43 +1200] cupsdIsAuthorized: username="pj"
I [01/Aug/2011:20:10:43 +1200] Installing config file "/etc/cups/cupsd.conf"...
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Printing jobs and dirty files
D [01/Aug/2011:20:10:43 +1200] cupsdCloseClient: 16
D [01/Aug/2011:20:10:43 +1200] cupsdCloseClient: 15
D [01/Aug/2011:20:10:43 +1200] cupsdDeregisterPrinter(p=0yb9f43c40(HP-Officejet-Pro-8500-a910), removeit=1)
I [01/Aug/2011:20:10:43 +1200] Saving job cache file "/var/cache/cups/job.cache"...
I [01/Aug/2011:20:10:43 +1200] Saving subscriptions.conf...
D [01/Aug/2011:20:10:43 +1200] cupsdSetBusyState: Printing jobs
E [01/Aug/2011:20:10:43 +1200] Failed to update TXT record for HP Officejet Pro 8500 a910 @ pj-indulgence: -2

---

### Post by madmax75 on 2011-08-01
I have the same sort of "sleeping printer" problem in Linux Mint 9.

I just take off the printer power cord from the wall and plug it back in. Usually that works for me.

---

### Post by dunbrokin on 2011-08-01
Yep, that works for me too.....but, there must be a more elegant solution....I would have to pull the plug two or three times a day!

---

### Post by jtarin on 2011-08-01
Try turning on [printer sharing.]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

---

### Post by dunbrokin on 2011-08-01
> **jtarin said:**
> Try turning on [printer sharing.]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

HP-Officejet-Pro-8500-a910 (Idle, Accepting Jobs, Shared, Server Default)

From localhost.....already switched on....so that is not the problem?!

---

### Post by jtarin on 2011-08-01
> **dunbrokin said:**
> HP-Officejet-Pro-8500-a910 (Idle, Accepting Jobs, Shared, Server Default)

From localhost.....already switched on....so that is not the problem?!
I didn't offer it as a problem...but a solution.

---

### Post by dunbrokin on 2011-08-01
> **jtarin said:**
> I didn't offer it as a problem...but a solution.

Thanks, but it does not seem to be the problem as Shared is already implemented...is what I meant.

---

### Post by dcsoldschool53 on 2011-08-01
maybe the solution, is to update the driver if you can.

---

### Post by jtarin on 2011-08-01
The driver update might be the route to go first. Possibly your present kernel does not fully support your present driver. A kernel update could be a consideration also.

---

### Post by dunbrokin on 2011-08-01
Thanks all, I assume as I constantly keep up with updates, that my kernel is indeed up to date.

There are 3 drivers offered for my printer in cups, perhaps I will try them all to see which one works best.

---

### Post by jtarin on 2011-08-01
You kernel might well be up to date for your versions repository, however there are newer kernels available. Example....I'm running 10.10, but using the 3.0 kernel. There are now even newer versions of that one. I'm not saying you _**should**_ upgrade to a version out of yours, but if you keep an old one as backup to boot with.....it couldn't hurt. 
Are you using a laptop?

---

### Post by dunbrokin on 2011-08-02
Yes I am using a lap top.

---

### Post by jtarin on 2011-08-02
> **dunbrokin said:**
> Yes I am using a lap top.The reason I ask is my suspicion that is has something to do with hibernation. I'm not an expert on laptops though.

---

### Post by walt.smith1960 on 2011-08-02
I don't have that printer but if you don't have it installed, you might consider HPLIP-GUI (or something like that). it's a utility for HP printers.  I wonder if HPLIP would have a means to adjust the power saving mode so it doesn't sleep so soundly.  Or perhaps the control panel on the device would have something.

---

