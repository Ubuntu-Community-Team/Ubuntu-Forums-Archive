---
title: "Redundant Ubuntu dhcp in a Windows environment"
date: 2018-11-24
forum: Networking &amp; Wireless
---

### Post by deheugden on 2018-11-24
Hello  , i am trying to create  a redundant Ubuntu dhcp in a Windows lab environment, but i cant get that done. 

Offcourse i searched the Internet, but i cant find a clear answer. It is not forwork, just for fun. My goal is to create 2 Ubuntu redundant dhcp servers and, if possible, let those setting be backupped to a (iscsi) storage. It already took me a lot of hours searching, testing and looking but i dont have the knowledge to get this done alone. Anyone who can tell me if this can be done and, if so, are there any tutorials available? Many thanks for reading and maybe replying, Johan.

---

### Post by TheFu on 2018-11-24
There shouldn't be multiple DHCP servers on a LAN segment because the one that happens to answer first will be the one controlling the settings for each client.
You can setup an active-standby solution 
or
a virtual machine failover solution,
however.

By using iSCSI, multiple VM hosts can have access to the same backed storage, so if a VM fails on 1 VM host, a monitoring process could easily restart it on a different VM host.

If I were attempting this, I'd setup ansible scripts to manage the configurations for the DHCP server. Having a DHCP server down for 30 minutes really shouldn't matter much.  In my lab, I setup DHCP leases to last a week, so already running systems won't be impacted unless there is extremely bad luck in the timing. I've never seen a Linux-based DHCP server, once setup, fail.

If your needs are more towards a 60 min lease period, then the DHCP server would become much more critical, clearly.

Installing a fresh Server VM takes about 10 minutes, then pushing out settings using Ansible would be 2-5 minutes and you'd have a fresh DHCP box ready.  If you need quicker solutions, you could have a cold system setup, just powered down, waiting to be started.  30 seconds of downtime isn't much.

---

### Post by deheugden on 2018-11-25
Manymthanks for the reply. The active standby solution sounds interesting, found this blog [https://www.madboa.com/geek/dhcp-failover/](https://www.madboa.com/geek/dhcp-failover/).  But what about backup up those settings, it cant be done through the regular Windows backup software , so what would be a nice solution to do that?

---

### Post by TheFu on 2018-11-25
Sorry - I wouldn't in any way, no how, use Windows for a server.

Backing up Linux systems is a solved problem.  Depending on your needs, you can make an image or do a full system backup at the file level or do a selective backup of only the important things or follow DevOps techniques to simply rebuild a fresh server as needed with custom settings.  

Image-based backups are for noobs, IMHO. I don't have enough storage to retain 60 days of daily backups and versioning in the backups just don't work.

Complete file system based backups are for people who require simple over everything else, without regard for storage needs. Do I really need to backup 30 server OS installs?  That's 2-6G of the same files on each box.

Selective backups only backup those things needed to reproduce the server at that point in time. I do this. I don't get the OS, but I do get the settings, data, and installed packages. With those things, getting back to the working service is an OS install, layered with settings, data, then fresh installations of the previously installed packages.

DevOps methods are best when you have a highly automated setup, managed by a professional team.  The settings are maintained as code and in version control systems.

So, I do selective backups, daily, automatic.  On systems with zero data like a DHCP server, those backups are FAST and keeping 120 days of versioned backups requires under 200MB of storage. I have an email gateway server - no data - it is just a gateway.  
 ```
$ more inc-sizes-spam2-2018-11-18 
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Nov 18 02:11:05 2018          114 MB            114 MB   (current mirror)
Sat Nov 17 02:11:04 2018         12.1 KB            114 MB
Fri Nov 16 02:11:05 2018         1.11 KB            114 MB
Thu Nov 15 02:11:04 2018         1.33 KB            114 MB
Wed Nov 14 02:11:04 2018         3.34 KB            114 MB
...
Thu Jul 26 02:11:05 2018         10.9 KB            114 MB
Wed Jul 25 02:11:04 2018       569 bytes            114 MB
Tue Jul 24 02:11:04 2018         10.9 KB            114 MB
Mon Jul 23 02:11:05 2018         10.5 KB            114 MB
Sun Jul 22 02:11:04 2018         10.3 KB            114 MB
```
I generate that report weekly on Sunday mornings. Trust me, the backups happened all this week too.  So, that data, versioned, would let me bring up a replacement email gateway in about 20 minutes.  I've done it.  

The real email server is a different backup completely. It takes longer, uses more storage, and restoring to a working setup takes about 45 minutes.  I've restored this system too - after a few blunders during an upgrade effort that failed.  It isn't a simple postfix+dovecot box running. It is an MS-Exchange replacement + much more. Fairly complex.  We all make mistakes. ;)

---

