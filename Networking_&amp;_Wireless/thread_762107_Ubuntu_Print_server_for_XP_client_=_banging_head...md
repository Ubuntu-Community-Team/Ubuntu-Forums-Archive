---
title: "Ubuntu Print server for XP client = banging head..."
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by RoboF on 2008-04-21
Hi,

I'm having a hard time trying to setup a Ubuntu machine (currently using a fresh install of 7.10/Desktop ) as a print server to an XP client. I can print fine from the Ubuntu server machine but when I try from my networked XP machine, it doesn't work. (btw I'm a Windows veteran and Linux newbie).

I've added the http:// (IPP) address of my Epson 1290 printer through the XP 'add printer' wizard and chosen the correct XP driver. I can then see the printer in XP and status is ready. When I try and print I watch the job list in XP and it all goes well until it's finished spooling the print job and then displays 'Error'. Checking the /var/log/error_log on the Ubuntu Server I notice that there is the following error message:

E [21/Apr/2008:21:32:57 +0100] cupsdReadClient: 23 IPP Read Error!

I've also provided a section of the log with cupsd.conf LogLevel set to 'debug' (see below)

I can ping both ways with no issue (and even have a working SAMBA file share on the Ubuntu machine).
I would really appreciate some help from the Ubuntu community to get this working so I can ditch XP once and for all! Thanks in advance.

Robert


LogLevel debug output:
192.168.1.10 = XP client
192.168.1.11 = Ubuntu Server

Let me know if more of the output would help, here's some of the output leading to the error;

...etc...
D [21/Apr/2008:22:41:38 +0100] cupsdAcceptClient: 24 from 192.168.1.10:631 (IPv4)
D [21/Apr/2008:22:41:48 +0100] cupsdNetIFUpdate: "lo" = localhost...
D [21/Apr/2008:22:41:48 +0100] cupsdNetIFUpdate: "eth0" = 192.168.1.11...
D [21/Apr/2008:22:41:48 +0100] cupsdNetIFUpdate: "lo" = localhost...
D [21/Apr/2008:22:41:48 +0100] cupsdNetIFUpdate: "eth0" = [mac address removed]%eth0...
D [21/Apr/2008:22:41:48 +0100] cupsdReadClient: 24 POST /printers/Stylus_Photo_1290 HTTP/1.1
D [21/Apr/2008:22:41:48 +0100] cupsdAuthorize: No authentication data provided.
D [21/Apr/2008:22:41:48 +0100] Get-Printer-Attributes [http://192.168.1.11:631/printers/Stylus_Photo_1290](http://192.168.1.11:631/printers/Stylus_Photo_1290)
D [21/Apr/2008:22:41:48 +0100] cupsdProcessIPPRequest: 24 status_code=0 (successful-ok)
D [21/Apr/2008:22:41:48 +0100] update_cups_browse: Refused 153 bytes from 192.168.1.11
D [21/Apr/2008:22:41:48 +0100] cupsdReadClient: 27 POST /printers/Stylus_Photo_1290 HTTP/1.1
D [21/Apr/2008:22:41:48 +0100] cupsdAuthorize: No authentication data provided.
D [21/Apr/2008:22:41:48 +0100] Get-Printer-Attributes [http://192.168.1.11:631/printers/Stylus_Photo_1290](http://192.168.1.11:631/printers/Stylus_Photo_1290)
D [21/Apr/2008:22:41:48 +0100] cupsdProcessIPPRequest: 27 status_code=0 (successful-ok)
D [21/Apr/2008:22:41:49 +0100] update_cups_browse: Refused 190 bytes from 192.168.1.11
D [21/Apr/2008:22:41:50 +0100] update_cups_browse: Refused 190 bytes from 192.168.1.11
D [21/Apr/2008:22:41:50 +0100] cupsdReadClient: 24 POST /printers/Stylus_Photo_1290 HTTP/1.1
D [21/Apr/2008:22:41:50 +0100] cupsdAuthorize: No authentication data provided.
E [21/Apr/2008:22:42:00 +0100] cupsdReadClient: 24 IPP Read Error!
D [21/Apr/2008:22:42:00 +0100] cupsdSendError: 24 code=400 (Bad Request)
D [21/Apr/2008:22:42:00 +0100] cupsdCloseClient: 24
D [21/Apr/2008:22:42:00 +0100] cupsdReadClient: 27 POST /printers/Stylus_Photo_1290 HTTP/1.1
...etc...

---

### Post by blokkendoos on 2008-05-01
Hi,

Did you try to connect to the cups-server.

Take a browser and connect to

https://<servername>:631/printers/printername

Is your cups-version up-to-date??


Is your xp-user member of the linux group that can print?



goodluck!

pablo k

---

### Post by LukeKendall on 2008-05-25
I upgraded my home PC that runs the print server from SuSE 9.2
to Ubuntu 8.0.4, and discovered that I could no longer print from
my other PC on the network.  Looking in the cups log file, I also
had the "no authentication data provided" error.

I tried (as root) aa-complain cupsd (which I gather weakens the
pam security checking for cupsd), but that didn't help.

What *partly* worked for me was to re-run the system-config-printer
command on the server and change the Policy from allowing the listed
users, to denying nobody.  As soon as I did that, I was able to print
a test page from the system-config-printer program on the client PC.

But I couldn't print anything else from that PC - other jobs sent
from my normal account continued to fail with the "no authentication data
provided" message again. :-(

Hope this helps someone a little.

luke

---

