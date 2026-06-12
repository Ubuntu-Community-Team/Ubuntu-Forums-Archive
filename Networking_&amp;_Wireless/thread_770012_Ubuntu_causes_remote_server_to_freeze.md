---
title: "Ubuntu causes remote server to freeze"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by xynamax on 2008-04-27
I really want to use Ubuntu at work, but I've had the same problem for a couple of years now.  I have a SCO OS 5 server that I connect to via Telnet and FTP to work and transfer files.  When I connect to the server via FTP from Ubuntu to transfer large files (over 50 megs) Nearly every time the SCO server's networking services will crash.  The rest of the server will be unaffected but I don't know how to restart the networking services in SCO so i just end up having to reboot it.

The way i connect to the SCO server is I open up a nautilus window and enter in the address bar "ftp://user:pass@192.168.2.200/" It connects fine and i can navigate the server and move small files on and off, but When i go to move large files i generally crash the networking on the SCO box :confused:

I've tried to use gFTP to do the large file transfers as well but I get the same problem.

When I connect from WinXP or Vista machines I dont have this problem no matter if i connect via windows explorer or via an FTP client.

I've tried ubuntu installations on several different computers and managed to reproduce the same results so i'm sure its not just the hardware on the Ubuntu machine causing the problem.

Any help would be greatly appreciated. Thanks

---

