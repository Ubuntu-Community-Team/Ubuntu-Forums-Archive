---
title: "Once wireless is detected, the OS stops loading and freezes"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by jamarsh123 on 2015-05-10
The title is a bit unclear but is the best I could come up with. The laptop (14.04 lts) actually works fine at home, but I had to set it up to work at my office and these are the configuration changes I needed to make. 
1. I connected to the secure WiFi network. 2. I installed HPLIP (HP linux drivers) so that I could print on the HP network printer. 3. I installed SAMBA so I could scan to a network folder on my laptop.  

Everything seemed to be working well. I took the laptop home and it worked fine at home as well.  However, when I went back to the office and powered up the computer, the problems began.  I believe the OS does not fully load. Unity appears, but the mouse crawls across the screen and nothing can be activated, including terminal.  

I tried to shut down the WiFi and reboot, but obviously don't know how to do that.  Eventually, I went home (out of WiFi range) and uninstalled samba, went back to the office and everything worked, but I really need to be able to scan to a network folder, so I reinstalled it. Once again, everything seemed good, but then the problems reoccurred.  I suspect there is a conflict between cups and samba, but I'm not knowledgeable enough to know how to track down the issue. I have wondered if there is importance to the order in which applications load. Perhaps cups is confused trying to find a network share before samba has actually loaded?

---

### Post by ian-weisser on 2015-05-12
What do the logs in /var/log say?

---

### Post by jamarsh123 on 2015-05-12
> **ian-weisser said:**
> What do the logs in /var/log say?
I found 3 log files in the directory you mentioned with entries. I have pasted them below.

log.%m - Here are the last few entries

[2015/05/10 18:44:30.095812,  0] ../source4/smbd/server.c:370(binary_smbd_main)
  samba version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/10 18:44:31.332269,  0] ../source4/smbd/server.c:478(binary_smbd_main)
  At this time the 'samba' binary should only be used for either:
  'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpoint servers = remote'
  You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks
[2015/05/11 09:22:39.846471,  0] ../source4/smbd/server.c:370(binary_smbd_main)
  samba version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/11 09:22:41.279658,  0] ../source4/smbd/server.c:478(binary_smbd_main)
  At this time the 'samba' binary should only be used for either:
  'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpoint servers = remote'
  You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks
[2015/05/12 05:44:43.952674,  0] ../source4/smbd/server.c:370(binary_smbd_main)
  samba version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/12 05:44:45.256866,  0] ../source4/smbd/server.c:478(binary_smbd_main)
  At this time the 'samba' binary should only be used for either:
  'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpoint servers = remote'
  You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks

*************************************************************************************

log.nmbd

[2015/05/10 18:43:19.485708,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/05/10 18:44:33,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/10 18:44:56,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****

  Samba name server JOHN is now a local master browser for workgroup WORKGROUP on subnet 192.168.0.248

  *****
[2015/05/11 08:53:06,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/05/12 05:44:47,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/12 05:45:10,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****

  Samba name server JOHN is now a local master browser for workgroup WORKGROUP on subnet 192.168.0.248

**************************************************************************************

log.smbd

[2015/05/10 18:43:19.502631,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/05/10 18:44:30,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/10 18:44:30.534226,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/05/10 18:44:31.003635,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/05/10 18:44:31.003951,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2015/05/11 08:53:06.545062,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/05/11 09:22:40,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/11 09:22:40.714929,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/05/11 09:22:40.917621,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/05/11 09:22:40.917961,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2015/05/12 05:44:44,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/05/12 05:44:44.025154,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/05/12 05:44:45.049183,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/05/12 05:44:45.049480,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

---

### Post by jamarsh123 on 2015-05-18
Well, I've posted the samba logs if anyone can detect a problem with my configuration. In the mean time, I have been able get along at the office - no samba, no printing - by booting in a different OS (Fedora). However, from time to time, I do try again to boot with Ubuntu 14.04 LTS, and it works flawlessly. This really does add to the confusion. I am now wondering if the problem lies with the wireless network connection and NOT with Samba. To that end, I intend to bring in some cables and get a wired connection to the network. I will report my findings. I do hope that someone, besides me, is reading this thread.

---

### Post by jamarsh123 on 2015-05-29
I plugged in a wired connection to the network at the office and booted the computer. Everything starts up and works fine. I even unplugged the wired connection AFTER the completion of the startup process, when the I am connected to the network,  and the computer finds the WifFi with no problem. Meanwhile, the wireless works fine at home.  It seems that during the startup process (before the graphical environment loads), ubuntu attempts to connect to any available wireless networks. When it finds the office network, it tries to connect and then the OS freezes. The urgency is gone, since I am able to function at work, but it is annoying and puzzling why this is happening.

---

### Post by ian-weisser on 2015-05-29
> **jamarsh123 said:**
> It seems that during the startup process (before the graphical environment loads), ubuntu attempts to connect to any available wireless networks.

Ubuntu will attempt, before login, to connect to networks the user has previously connected to.
Is your system is unsuccessful at connecting to the office wireless network?
If so, the timeout is usually about 60-90 seconds.

If there a setting for the office network in Network Manager (because you have previously connected to it), go into the settings and uncheck the 'Automatically connect to this network' box.

---

