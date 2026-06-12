---
title: "Problem Printing from Network"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by arbulus on 2008-03-26
I just started having this problem yesterday.  Everything has been working fine for months, and then the power went out for a few minutes yesterday and when the machine came back up, this is my problem.

I have a file/print server running Ubuntu Gutsy.  On it are installed two printers that are shared across my network.  I have 2 clients, a Macbook Pro, a lappy dual booted with Gutsy and Vista.  I've been sharing the two printers from the server for ages and never had a problem.  But when the machine rebooted after the power outtage yesterday, I coudln't print from the clients.  I went to the server and found that I CAN print directly from it.  But printing across the network to the server no longer functions. 

I pulled up localhost:631 in Firefox on the server and looked at the error log file and this is what it says:

```
E [26/Mar/2008:21:32:17 -0400] [Job 3] No %%BoundingBox: comment in header!
E [26/Mar/2008:21:40:27 -0400] DNSServiceRegister failed with error -65537
E [26/Mar/2008:21:40:27 -0400] DNSServiceRegister failed with error -65537
E [26/Mar/2008:21:46:09 -0400] DNSServiceRegister failed with error -65537
E [26/Mar/2008:21:54:54 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [26/Mar/2008:21:55:30 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:30 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:30 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:30 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:30 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:32 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:32 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:32 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:55:32 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:02 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:02 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:02 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:02 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:02 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [26/Mar/2008:21:57:03 -0400] cupsdAuthorize: Local authentication certificate not found!
```

I have no idea what any of this means. I haven't changed anything at all. Like I said, printing has been working for ages and suddenly doesn't now. All of my settings are as they should be: I'm sharing the printers from the server, there's no firewall on any of my machines that could be blocking it, both printers are working and published and I can print directly from the server. 

Is anyone familiar with this problem or have an idea what I can do to fix it?

---

### Post by arbulus on 2008-03-28
Bump

---

### Post by arbulus on 2008-03-29
Ok, so I unplugged the printers from the server, deleted them in "Printing" and rebooted the machine. Then I plugged the printers back in, added them and tried again.  It still doesn't work. 

Here is the newest error log from CUPS:

```
E [29/Mar/2008:18:37:23 -0400] Pause-Printer: Unauthorized
E [29/Mar/2008:18:37:33 -0400] Pause-Printer: Unauthorized
E [29/Mar/2008:18:37:49 -0400] CUPS-Delete-Printer: Unauthorized
E [29/Mar/2008:18:38:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:38:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:38:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:40:32 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [29/Mar/2008:18:40:37 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [29/Mar/2008:18:40:46 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [29/Mar/2008:18:40:48 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [29/Mar/2008:18:41:11 -0400] CUPS-Set-Default: Unauthorized
E [29/Mar/2008:18:42:01 -0400] [Job 5] No %%BoundingBox: comment in header!
E [29/Mar/2008:18:42:12 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:12 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:12 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:12 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:12 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:13 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:13 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:13 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [29/Mar/2008:18:42:16 -0400] cupsdAuthorize: Local authentication certificate not found!
```

I'm really at my wits end here.  I'm about to just re-install the OS on the server to see if that will fix it, which I REALLY do not want to do, but I have to be able to print and this is driving me crazy.

Any ideas?

---

