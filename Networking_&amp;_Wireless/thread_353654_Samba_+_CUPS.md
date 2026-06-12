---
title: "Samba + CUPS"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by mahlib on 2007-02-05
Hi,

I'm trying to get CUPS (1.2.4) to work with Samba (3.0.22) on an Ubuntu 6.10 (Edgy Eft) machine (hereafter referred to as "Machine"). "Machine" is in a Windows-centric network.
"Machine" has Samba setup properly as smb.conf is crucial to authenticating users using pam_winbind on login.

"Machine" is setup to print on a network printer hereafter referred to as "Printer."

"Printer"'s configuration file (/etc/cups/printer.conf) follows:
<DefaultPrinter Printer>
Info HP LJ4000N
Location Some location
DeviceURI smb://SERVER/PRINTER
State Idle
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
AllowUser @Students
OpPolicy default
ErrorPolicy abort-job
</Printer>

The following command:

smbspool smb://networkusername:password@SERVER/PRINTER 1 networkusername Test 1 Test.txt

results in (/var/log/cups/error_log):

E [04/Feb/2007:19:09:39 -0800] [Job 13] No ticket cache found for userid=31337
E [04/Feb/2007:19:09:39 -0800] [Job 13] Can not get the ticket cache for networkusername
E [04/Feb/2007:19:09:39 -0800] [Job 13] Session setup failed: NT_STATUS_LOGON_FAILURE
E [04/Feb/2007:19:09:39 -0800] [Job 13] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [04/Feb/2007:19:09:39 -0800] [Job 13] Unable to connect to CIFS host, will retry in 60 seconds...
E [04/Feb/2007:19:10:39 -0800] [Job 13] No ticket cache found for userid=31337
E [04/Feb/2007:19:10:39 -0800] [Job 13] Can not get the ticket cache for networkusername
E [04/Feb/2007:19:10:39 -0800] [Job 13] Session setup failed: NT_STATUS_LOGON_FAILURE
E [04/Feb/2007:19:10:39 -0800] [Job 13] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [04/Feb/2007:19:10:39 -0800] [Job 13] Unable to connect to CIFS host, will retry in 60 seconds...
E [04/Feb/2007:19:11:39 -0800] [Job 13] No ticket cache found for userid=31337
E [04/Feb/2007:19:11:39 -0800] [Job 13] Can not get the ticket cache for networkusername
E [04/Feb/2007:19:11:39 -0800] [Job 13] Session setup failed: NT_STATUS_LOGON_FAILURE
E [04/Feb/2007:19:11:39 -0800] [Job 13] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [04/Feb/2007:19:11:39 -0800] [Job 13] Unable to connect to CIFS host, will retry in 60 seconds...
E [04/Feb/2007:19:12:39 -0800] [Job 13] Unable to connect to CIFS host after (tried 3 times)
E [04/Feb/2007:19:12:39 -0800] PID 10134 (/usr/lib/cups/backend/smb) stopped with status 1!
E [04/Feb/2007:19:12:39 -0800] PID 10133 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!

The user's print queue is seen from other Windows computers on the network, but it is set by default to be paused.

The Domain Controller running Windows Server 2003 detected a username of "cupsys" printing from "Machine" instead of "networkusername."

If "networkusername" is used to login to any of Windows XP Professional machines, "networkusername" will be seen in the print queue, but "networkusername" cannot unpause, restart, or cancel the print job.

How do I fix this?

Regards,

mahlib

---

### Post by mahlib on 2007-02-06
So I figured out the problem: CUPS doesn't like whitespace inbetween <Printer> tags.

I'm glad that the issue was resolved, but it has brought about another issue:

How can I pass Samba credentials to CUPS? User log into the Ubuntu machines through Winbind. Is there a way to get the Winbind authentication passed to CUPS automagically? The goal is to ultimately allow for a window manager / desktop environment / [word / graphics] processing independent printing system.

Currently, users have to manually enter in their username and password combination to each program that utilizes CUPS. The username and password combination is then sent over the network in **cleartext**. This is clearly not acceptable, especially when multiple users may be on the same machine at the same time.

I have heard that CUPS 1.3 allows for Kerberos support so credentials may be passed from Winbind to CUPS seamlessly. However, CUPS 1.3 is not yet stable.

Thanks in advance for any and all suggestions.

---

### Post by Offoffoff on 2007-05-28
Hello! I have absolutely the same problem. I have Windows domain local net and earlier I printed from my notebook with domain's printer HP1320 while I was on Windows platform. But now I can't do like that. My Ubuntu made printer settings right, asked me for a username and password. But! I can't print with that printer situated at Windows box, even can't print test page. Spooler talking: wait-until-job-specified.  By the way, printer is connected with ordinary WindowsXP-workstation. Also just printing in the access boxes my domain username and password I can reach all resources (opened folders) of my Windows domain net, except printers. I have installed krb5*.debs (I heard in Windows these are used for that), but it doesn't help.

Here is logs form cups_error.log:
E [28/May/2007:09:56:38 +0700] CUPS-Add-Modify-Printer: Unauthorized
E [28/May/2007:09:57:04 +0700] [Job 227] No %%BoundingBox: comment in header!
E [28/May/2007:09:57:05 +0700] [Job 227] Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)
E [28/May/2007:09:57:05 +0700] [Job 227] No ticket cache found for userid=1000
E [28/May/2007:09:57:05 +0700] [Job 227] Can not get the ticket cache for mylinuxaccount
E [28/May/2007:09:57:05 +0700] [Job 227] Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)
E [28/May/2007:09:57:05 +0700] [Job 227] Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)
E [28/May/2007:09:57:05 +0700] [Job 227] Unable to connect to CIFS host, will retry in 60 seconds...
E [28/May/2007:09:58:27 +0700] [Job 228] No %%BoundingBox: comment in header!
E [28/May/2007:09:58:27 +0700] [Job 228] Session setup failed: NT_STATUS_LOGON_FAILURE
E [28/May/2007:09:58:27 +0700] [Job 228] No ticket cache found for userid=1000
E [28/May/2007:09:58:27 +0700] [Job 228] Can not get the ticket cache for mylinuxaccount
E [28/May/2007:11:59:38 +0700] cupsdAuthorize: Local authentication certificate not found!
E [28/May/2007:11:59:38 +0700] cupsdAuthorize: Local authentication certificate not found!
E [28/May/2007:11:59:38 +0700] cupsdAuthorize: Local authentication certificate not found!
E [28/May/2007:11:59:38 +0700] cupsdAuthorize: Local authentication certificate not found!
E [28/May/2007:11:59:43 +0700] cupsdAuthorize: Local authentication certificate not found!
E [28/May/2007:11:59:43 +0700] cupsdAuthorize: Local authentication certificate not found!
and so on...

What I have to do? Where can I get that ticket? What is  %%BoundingBox:? Where I have to run? I feel myself helpless....

Moderator mark this post [SOLVED], because I got a decision! 
I have done everything above, but:
1. I change workgroup=domainnamewithoutlocal in smb.conf sudo 
2. I have made 
<code>sudo gnome-cups-manager</code>
I got three authorize request from my Ubuntu (I fill in my domain's name and password):
1. request for workgroup
2. request for domain
3. request for printer-machine
And I found  in gnome-cups-manager that the name of my remote printer changed from "hplaserj" to "hp".
AND... It works!!! Slow, but works... And I can see cupsd.log without any kind of mistakes!!!

---

