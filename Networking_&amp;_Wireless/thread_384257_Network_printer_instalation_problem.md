---
title: "Network printer instalation problem"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by erasmo.da.rotterdam on 2007-03-14
HI!!:KS 
I am working into a lan. I have a network printer Epson EPL 6200 with IP 192.168.8.25
I have a proxy with IP 192.168.8.3
My PC is 192.168.8.7
browsing [http://192.168.8.25](http://192.168.8.25) on my desktop with firefox I can see the printer

GENERAL INFORMATION

Administrator Name  	 
Location 	 

Interface Card Model Name 	EIPS2 
MAC Address 	00:00:48:BC:71:FA 
Hardware Version 	Ver. 01.00 
Software Version 	Ver. 02.30 
Model Name 	EPL-6200 

Network Status 	100BASE-TX, Full Duplex 

Printer Status 	Ready or Printing

Current Time 	2000-01-01 02:21:02 GMT+00:00 

IPP INFORMATION

IPP URL  	[http://192.168.8.25:631/EPSON_IPP_Printer](http://192.168.8.25:631/EPSON_IPP_Printer) 
Printer Name 	EPSON_IPP_Printer 
Location 	 

so I did this
System -> administation -> Printing
New Printer
Network printer -> CUPS (IPP)
in URI -> [http://192.168.8.25:631/EPSON_IPP_Printer](http://192.168.8.25:631/EPSON_IPP_Printer)
In Manufacturer Epson
Model Epson EPL 6200L
in Driver I have 'epl6200l (recommended)'

Forward (supposing this driver is already available, am I correct?)

Name: EPSON_IPP_Printer
Description: Epson EPL 6200
Location: 192.168.8.25

Apply

Now in printers I see my EPSON_IPP_Printer ready

However if I try to print a Test Page nothing happens in the queue I can read 'printing: job-printing'
Trying from a text editor doesn't change the situation only the state this time is 'Pending none'

I even tried to add a line in ports.conf in /etc/cups/cupsd/
Listen 192.168.8.25:631
and restarting cups with sudo /etc/init.d/cupsys restart
but I cannot solve my problem

Any Idea?:confused:

---

### Post by Jose Catre-Vandis on 2007-03-14
Try [http://localhost:631](http://localhost:631) in your browser, and configure your printer from there. If asked for a password this should be the one you use for login/sudo

---

### Post by erasmo.da.rotterdam on 2007-03-15
I found the instruction on this page

[http://localhost:631/help/overview.html](http://localhost:631/help/overview.html)

PASSWORD PROBLEM

I read this

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I browsed a little...

sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

username and password now work :popcorn: 

I have this printer now

Description: Epson EPL 6200L
Location: sopra zelda
Make and Model: Epson EPL-6200L Foomatic/epl6200l (recommended)
Printer State: processing, accepting jobs, published.
Device URI: [http://192.168.8.25:631/Karmela](http://192.168.8.25:631/Karmela)

But the test page cannot be printed
The job has been sent but the status 'processing' doesn't change :confused: 
I set LogLevel to debug in cupsd.conf

tail -50 /var/log/cups/error_log

D [15/Mar/2007:10:14:01 +0100] [CGI] show_printer(http=0x8089068, printer="Karmela")
D [15/Mar/2007:10:14:01 +0100] cupsdReadClient: 8 POST / HTTP/1.1
[COLOR="Red"]D [15/Mar/2007:10:14:01 +0100] cupsdAuthorize: No authentication data provided.[/COLOR]
D [15/Mar/2007:10:14:01 +0100] Get-Printer-Attributes ipp://localhost/printers/Karmela
D [15/Mar/2007:10:14:01 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [15/Mar/2007:10:14:01 +0100] [CGI] cgiCopyTemplateLang(tmpl="header.tmpl")
D [15/Mar/2007:10:14:01 +0100] [CGI] locale="en_us"...
D [15/Mar/2007:10:14:01 +0100] [CGI] Template file is "/usr/share/cups/templates/header.tmpl"...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 0...
D [15/Mar/2007:10:14:01 +0100] [CGI] "{title}" at 205...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting "{refresh_page?" at 374, result=1...
D [15/Mar/2007:10:14:01 +0100] cupsdReadClient: 8 POST / HTTP/1.1
D [15/Mar/2007:10:14:01 +0100] cupsdAuthorize: No authentication data provided.
D [15/Mar/2007:10:14:01 +0100] Get-Jobs ipp://localhost:631/printers/Karmela
D [15/Mar/2007:10:14:01 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [15/Mar/2007:10:14:01 +0100] [CGI] Output first part...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 374...
D [15/Mar/2007:10:14:01 +0100] [CGI] "{refresh_page}" at 424...
D [15/Mar/2007:10:14:01 +0100] [CGI] Returning at file position 427 on character ':'...
D [15/Mar/2007:10:14:01 +0100] [CGI] Skip second part...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 427...
D [15/Mar/2007:10:14:01 +0100] [CGI] Returning at file position 428 on character '}'...
D [15/Mar/2007:10:14:01 +0100] [CGI] Finished "{refresh_page?", out=0xb7e9b0e0...
D [15/Mar/2007:10:14:01 +0100] [CGI] "{title}" at 671...
D [15/Mar/2007:10:14:01 +0100] [CGI] "{title}" at 952...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting "{SECTION=admin" at 1411, result=0...
D [15/Mar/2007:10:14:01 +0100] [CGI] Skip first part...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 1411...
D [15/Mar/2007:10:14:01 +0100] [CGI] Returning at file position 1412 on character ':'...
D [15/Mar/2007:10:14:01 +0100] [CGI] Output second part...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 1412...
D [15/Mar/2007:10:14:01 +0100] [CGI] Returning at file position 1415 on character '}'...
D [15/Mar/2007:10:14:01 +0100] [CGI] Finished "{SECTION=admin", out=0xb7e9b0e0...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting "{SECTION=classes" at 1678, result=0...
D [15/Mar/2007:10:14:01 +0100] [CGI] Skip first part...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 1678...
D [15/Mar/2007:10:14:01 +0100] [CGI] Returning at file position 1679 on character ':'...
D [15/Mar/2007:10:14:01 +0100] [CGI] Output second part...
D [15/Mar/2007:10:14:01 +0100] cupsdReadClient: 6 GET /cups.css HTTP/1.1
D [15/Mar/2007:10:14:01 +0100] cupsdReadClient: 6 Browser asked for language "en-us.utf-8"...
D [15/Mar/2007:10:14:01 +0100] cupsdAuthorize: username="emotiv"
D [15/Mar/2007:10:14:01 +0100] write_file: 6 file=10
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 1679...
D [15/Mar/2007:10:14:01 +0100] [CGI] Returning at file position 1682 on character '}'...
D [15/Mar/2007:10:14:01 +0100] [CGI] Finished "{SECTION=classes", out=0xb7e9b0e0...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting "{SECTION=help" at 1938, result=0...
D [15/Mar/2007:10:14:01 +0100] [CGI] Skip first part...
D [15/Mar/2007:10:14:01 +0100] [CGI] Starting at file position 1938...

Now I am browsing looking for a solution
Any suggestion?

---

