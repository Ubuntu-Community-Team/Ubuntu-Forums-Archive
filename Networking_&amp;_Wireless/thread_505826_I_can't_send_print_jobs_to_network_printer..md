---
title: "I can't send print jobs to network printer."
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by uncleclinto on 2007-07-20
Greetings,

I have a network printer attached to a win2k box.  When I look for it using the add printer dialog, it show up under Samba and it's host box.  The driver is even listed in the list-o-hp drivers in the drop-down menu.  I install it.  It says it's successful, but I can't print to it.  Every time it pauses itself.  I hit resume, and it pauses itself again.  What am I missing?

Confused Clint 

ps: mye error log... (all greek to me)

E [20/Jul/2007:14:19:12 -0400] Resume-Printer: Unauthorized
E [20/Jul/2007:14:19:24 -0400] [Job 8] No %%BoundingBox: comment in header!
E [20/Jul/2007:14:19:25 -0400] [Job 8] Session setup failed: NT_STATUS_LOGON_FAI LURE
E [20/Jul/2007:14:19:25 -0400] [Job 8] No ticket cache found for userid=1000
E [20/Jul/2007:14:19:25 -0400] [Job 8] Can not get the ticket cache for admin
E [20/Jul/2007:14:19:26 -0400] [Job 8] Session setup failed: NT_STATUS_LOGON_FAI LURE
E [20/Jul/2007:14:19:26 -0400] [Job 8] Tree connect failed (NT_STATUS_ACCESS_DEN IED)
E [20/Jul/2007:14:19:26 -0400] [Job 8] Unable to connect to CIFS host, will retr y in 60 seconds...
E [20/Jul/2007:14:20:30 -0400] [Job 8] Session setup failed: NT_STATUS_LOGON_FAILURE
E [20/Jul/2007:14:20:31 -0400] [Job 8] No ticket cache found for userid=1000
E [20/Jul/2007:14:20:31 -0400] [Job 8] Can not get the ticket cache for admin
E [20/Jul/2007:14:20:31 -0400] [Job 8] Session setup failed: NT_STATUS_LOGON_FAILURE
E [20/Jul/2007:14:20:32 -0400] [Job 8] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [20/Jul/2007:14:20:32 -0400] [Job 8] Unable to connect to CIFS host, will retry in 60 seconds...

---

### Post by mitch.c on 2007-07-23
> **uncleclinto said:**
> Greetings,

I have a network printer attached to a win2k box.  When I look for it using the add printer dialog, it show up under Samba and it's host box.  The driver is even listed in the list-o-hp drivers in the drop-down menu.  I install it.  It says it's successful, but I can't print to it.  Every time it pauses itself.  I hit resume, and it pauses itself again.  What am I missing?

Confused Clint 

ps: mye error log... (all greek to me)

<--snip-->
E [20/Jul/2007:14:19:26 -0400] [Job 8] Session setup failed: NT_STATUS_LOGON_FAI LURE
E [20/Jul/2007:14:19:26 -0400] [Job 8] Tree connect failed (NT_STATUS_ACCESS_DEN IED)
<--snip-->
.

Pretty clear... the user account you use to connect to the Windows PC does not have access to the PC and/or printer. It appears you are using a user named 'admin'... does this user exist on the Windows PC? Have you changed a password since setting up the printer?

---

