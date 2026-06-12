---
title: "Samba extremely poor network performance"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by Jason_Burrell on 2014-10-06
I've installed an Ubuntu file server using Samba in a generic configuration. Unfortunately, while I can connect from my Windows machines just fine, the transfer rate tops out at around 640kb/s. Network performance using other protocols (ftp, http, ssh) is at least decent. The networking setup is a wireless laptop to a wireless access point to the wireless Ubuntu server. I tried this several years ago with a hard ethernet cable and had the same problem and basically gave up. However, I can't believe that CIFS performance is this ungodly bad. 

So two questions:
1) Any ideawhat is causing this? It looks like there's a metric buttload of overhead on the network from the Samba transfer, judging from how performance on everything else seems to go to hell when I use it. The performance can't be this horrible or nobody would use it.
2) Is there a way to just use NFS with Windows? Neither my Windows 7 machine nor my Windows 8.1 machine seem to have any support for it. (There is no "client for NFS" listed as a feature.)

---

### Post by TheFu on 2014-10-06
CIFS/samba performance can be fantastic.  I see 65+MB/s transfers in both directions here. Sure, sometimes the source or target system is busy and it will drop to 40MB/s and if the Windows machine is really busy then it can drop to 7MB/s, but that is really odd.

To get help with CIFS performance, you need to provide facts:
* You say that other protocols are "decent" - exactly what do you mean by that. EXACTLY.
* Wifi sucks. It always has.  When it works, I'm surprised.  Use wired connections if you care at all about performance. Wifi just has too many variables to troubleshoot, can't do it.
* Look at every part of the data chain from source to target. 
** source HDD performance (SSD/SATA/IDE/Flash/... )
** target HDD performance
** source HDD cable/connection performance - USB2 sucks.
** target HDD cable/connection performance - USB2 sucks.
** source file system performance
** target file system performance
** source network performance (drivers, connection speed, any errors, etc)
** target network performance
** source overall CPU/RAM/Disk IO use by other programs
** target overall CPU/RAM/Disk IO use by other programs
** hardware failures - often a bad SATA cable or bad network cable works slightly
** firewall or QoS settings
** Switch or router issues (HW, config)
** Samba config issues - post the clean, comments removed, /etc/samba/smb.conf file.

Gather your facts and post them.

So - last week I was trying to help someone else here with backup performance. For days we were trying to get his GigE capable network cards to connect at GigE speeds - about 5 days in, he finally posted the model switch being used 10/100, though previously saying it was GigE.  Then he clarified that he was backing up over the internet - so none of the GigE stuff mattered at all. He did mention office and home, but that doesn't always click since many, many, people have "home offices" and separate networks (I do).  Also, he was mixing MBps an Mbps - these ARE different by 8x transfer rates. Be exact, please.

Please share the exact network configuration and hardware sooner, so people trying to help don't wrongly assume something.

There is NFS services for Windows, but it isn't included until the Enterprise or Ultimate levels of the OS. Professional doesn't have it - at least I don't think so.  Home definitely doesn't have it.

---

### Post by gordintoronto on 2014-10-06
One thing which can really slow you down is if the Wi-Fi channel has a lot of interference. Inssider can help you see what is going on. My son lived in an apartment, and he could "see" 60 (!) WiFi networks.

---

