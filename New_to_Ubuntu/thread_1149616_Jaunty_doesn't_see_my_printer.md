---
title: "Jaunty doesn't see my printer"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by foilonfilling on 2009-05-05
Worked fine with 8.10 on another box, but this new system running 9.04 doesn't see the printer at all. In troubleshoot I got this message:

> Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': False}
Page 4 (Choose device):
{'cups_device_attributes': {'device-class': u'direct',
                            'device-id': u'MFG:Hewlett-Packard;MDL:OfficeJet  K80xi;CMD:MLC,PCL,PML;CLASS:PRINTER;DESCRIPTION:Hewlett-Packard OfficeJet K Series;1284.3M:f7f,f7f;1284.4DL:4d,4e,1;SERN:MY25SD627BOH;VSTATUS:$HB0$NC0,ff,DN,IDLE,CUT,K3,C0,SM,NR,KP000,CP056;AiO:0;DW-PCL;',
                            'device-info': u'HP OfficeJet  K80xi LPT #1',
                            'device-make-and-model': u'HP OfficeJet  K80xi'},
 'cups_device_listed': True,
 'cups_device_uri': 'parallel:/dev/lp0'}
Page 5 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

I guess it sees that there's something there, but it won't show up under sys/admin/printing. Does anyone have any advice?

---

### Post by LowSky on 2009-05-05
do you have hplip installed?

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by foilonfilling on 2009-05-05
> **LowSky said:**
> do you have hplip installed?

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

yes, and because I'm a doofus, I forgot to ask the computer to search for new printers afterward. Having done this, though, it sees the printer and knows what model the printer is, but when I try to print a test page I get a message saying that the printer isn't connected. Although we've already established that I am a doofus, the printer is plugged in, hooked up, and powered on. Further thoughts?

Might also add that in printer config, it says the printer is "connected to localhost".

---

### Post by IronOxide on 2009-05-07
Having a similar problem, I guess. But in my case, the printer installs fine and perfectly supposedly, the first test page prints out fine, and then it shits the bed immediately after that. Can't print anything. One time got an error message, didn't think to write it down before troubleshooting, now don't get anything but a blank sheet of paper.

EDIT: Found the error message in the trouble shooter, says '/usr/lib/cups/filter/foomatic-rip failed'
along with 
> D [07/May/2009:02:32:34 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:32:34 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:34 -0400] Get-Jobs ipp://localhost/printers/
D [07/May/2009:02:32:34 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:32:34 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:32:34 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:34 -0400] Get-Jobs ipp://localhost/printers/
D [07/May/2009:02:32:34 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:32:34 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:32:34 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:34 -0400] Create-Printer-Subscription /
D [07/May/2009:02:32:34 -0400] cupsdCreateSubscription(con=0x7f1ec1b326b0(6), uri="/")
D [07/May/2009:02:32:34 -0400] pullmethod="ippget"
D [07/May/2009:02:32:34 -0400] notify-lease-duration=86400
D [07/May/2009:02:32:34 -0400] notify-time-interval=0
D [07/May/2009:02:32:34 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [07/May/2009:02:32:34 -0400] Added subscription 61 for server
I [07/May/2009:02:32:34 -0400] Saving subscriptions.conf...
D [07/May/2009:02:32:34 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:32:35 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:32:35 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:35 -0400] Get-Notifications /
D [07/May/2009:02:32:35 -0400] cupsdIsAuthorized: requesting-user-name="adam"
D [07/May/2009:02:32:35 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:32:37 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:32:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [07/May/2009:02:32:37 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:37 -0400] CUPS-Get-Printers
D [07/May/2009:02:32:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [07/May/2009:02:32:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [07/May/2009:02:32:37 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:37 -0400] CUPS-Get-Classes
D [07/May/2009:02:32:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [07/May/2009:02:32:37 -0400] cupsdCloseClient: 7
D [07/May/2009:02:32:52 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:32:52 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [07/May/2009:02:32:52 -0400] cupsdCloseClient: 7
D [07/May/2009:02:32:52 -0400] cupsdReadClient: 9 POST / HTTP/1.1
D [07/May/2009:02:32:52 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:52 -0400] CUPS-Get-Printers
D [07/May/2009:02:32:52 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [07/May/2009:02:32:52 -0400] cupsdCloseClient: 9
D [07/May/2009:02:32:57 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:32:57 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [07/May/2009:02:32:57 -0400] cupsdCloseClient: 7
D [07/May/2009:02:32:58 -0400] cupsdReadClient: 9 POST / HTTP/1.1
D [07/May/2009:02:32:58 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:58 -0400] CUPS-Get-Printers
D [07/May/2009:02:32:58 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [07/May/2009:02:32:58 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:32:58 -0400] cupsdCloseClient: 9
D [07/May/2009:02:32:58 -0400] cupsdReadClient: 7 GET /printers/Photosmart-C4400-series.ppd HTTP/1.1
D [07/May/2009:02:32:58 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:32:58 -0400] cupsdCloseClient: 7
D [07/May/2009:02:33:01 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:33:02 -0400] cupsdReadClient: 7 POST /printers/Photosmart-C4400-series HTTP/1.1
D [07/May/2009:02:33:02 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:02 -0400] Print-Job ipp://localhost:631/printers/Photosmart-C4400-series
D [07/May/2009:02:33:02 -0400] [Job ???] Auto-typing file...
I [07/May/2009:02:33:02 -0400] [Job ???] Request file type is application/pdf.
D [07/May/2009:02:33:02 -0400] add_job: requesting-user-name="adam"
I [07/May/2009:02:33:02 -0400] [Job 130] Adding start banner page "none".
I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...
I [07/May/2009:02:33:02 -0400] [Job 130] Adding end banner page "none".
I [07/May/2009:02:33:02 -0400] [Job 130] File of type application/pdf queued by "adam".
D [07/May/2009:02:33:02 -0400] [Job 130] hold_until=0
I [07/May/2009:02:33:02 -0400] [Job 130] Queued on "Photosmart-C4400-series" by "adam".
I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...
D [07/May/2009:02:33:02 -0400] [Job 130] job-sheets=none,none
D [07/May/2009:02:33:02 -0400] [Job 130] banner_page = 0
D [07/May/2009:02:33:02 -0400] [Job 130] argv[0]="Photosmart-C4400-series"
D [07/May/2009:02:33:02 -0400] [Job 130] argv[1]="130"
D [07/May/2009:02:33:02 -0400] [Job 130] argv[2]="adam"
D [07/May/2009:02:33:02 -0400] [Job 130] argv[3]="Webern.jpg"
D [07/May/2009:02:33:02 -0400] [Job 130] argv[4]="1"
D [07/May/2009:02:33:02 -0400] [Job 130] argv[5]="DryTime=Zero PageSize=Letter Quality=FromPrintoutMode InputSlot=Default number-up=1 PrintoutMode=Normal Duplex=None job-uuid=urn:uuid:020bd675-7112-3ab4-58df-6412adb62107"
D [07/May/2009:02:33:02 -0400] [Job 130] argv[6]="/var/spool/cups/d00130-001"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[9]="SERVER_ADMIN=root@adam-laptop"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[10]="SOFTWARE=CUPS/1.3.9"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[12]="TZ=America/New_York"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[13]="USER=root"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[16]="IPP_PORT=631"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[17]="CHARSET=utf-8"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[18]="LANG=en_US.UTF8"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[19]="PPD=/etc/cups/ppd/Photosmart-C4400-series.ppd"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[20]="RIP_MAX_CACHE=8m"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[21]="CONTENT_TYPE=application/pdf"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[22]="DEVICE_URI=usb://HP/Photosmart%20C4400%20series?serial=CN86JFG22C0557"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[23]="PRINTER=Photosmart-C4400-series"
D [07/May/2009:02:33:02 -0400] [Job 130] envp[24]="FINAL_CONTENT_TYPE=printer/Photosmart-C4400-series"
I [07/May/2009:02:33:02 -0400] [Job 130] Started filter /usr/lib/cups/filter/pdftopdf (PID 9462)
I [07/May/2009:02:33:02 -0400] [Job 130] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9463)
I [07/May/2009:02:33:02 -0400] [Job 130] Started backend /usr/lib/cups/backend/usb (PID 9464)
I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...
D [07/May/2009:02:33:02 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [07/May/2009:02:33:02 -0400] [Job 130] Getting input from file
D [07/May/2009:02:33:02 -0400] [Job 130] foomatic-rip version 4.0.0.195 running...
D [07/May/2009:02:33:02 -0400] [Job 130] Parsing PPD file ...
D [07/May/2009:02:33:02 -0400] [Job 130] Added option Resolution
D [07/May/2009:02:33:02 -0400] [Job 130] Added option PageSize
D [07/May/2009:02:33:02 -0400] [Job 130] Added option Model
D [07/May/2009:02:33:02 -0400] [Job 130] Added option PrintoutMode
D [07/May/2009:02:33:02 -0400] [Job 130] Added option InputSlot
D [07/May/2009:02:33:02 -0400] [Job 130] Added option Duplex
D [07/May/2009:02:33:02 -0400] [Job 130] Added option DryTime
D [07/May/2009:02:33:02 -0400] [Job 130] Added option Quality
D [07/May/2009:02:33:02 -0400] [Job 130] Added option ImageableArea
D [07/May/2009:02:33:02 -0400] [Job 130] Added option PaperDimension
D [07/May/2009:02:33:02 -0400] [Job 130] Added option Font
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] Parameter Summary
D [07/May/2009:02:33:02 -0400] [Job 130] -----------------
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] Spooler: cups
D [07/May/2009:02:33:02 -0400] [Job 130] Printer: Photosmart-C4400-series
D [07/May/2009:02:33:02 -0400] [Job 130] Shell: /bin/bash
D [07/May/2009:02:33:02 -0400] [Job 130] PPD file: /etc/cups/ppd/Photosmart-C4400-series.ppd
D [07/May/2009:02:33:02 -0400] [Job 130] ATTR file:
D [07/May/2009:02:33:02 -0400] [Job 130] Printer model: HP Photosmart c4400 Series hpijs, 3.9.2
D [07/May/2009:02:33:02 -0400] [Job 130] Job title: Webern.jpg
D [07/May/2009:02:33:02 -0400] [Job 130] File(s) to be printed:
D [07/May/2009:02:33:02 -0400] [Job 130] <STDIN>
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [07/May/2009:02:33:02 -0400] [Job 130] Printing system options:
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'number-up=1'
D [07/May/2009:02:33:02 -0400] [Job 130] Unknown option number-up=1.
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'job-uuid=urn:uuid:020bd675-7112-3ab4-58df-6412adb62107'
D [07/May/2009:02:33:02 -0400] [Job 130] Unknown option job-uuid=urn:uuid:020bd675-7112-3ab4-58df-6412adb62107.
D [07/May/2009:02:33:02 -0400] [Job 130] Options from the PPD file:
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'DryTime=Zero'
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'PageSize=Letter'
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'Quality=FromPrintoutMode'
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'InputSlot=Default'
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'PrintoutMode=Normal'
D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'Duplex=None'
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] ================================================
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] File: <STDIN>
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] ================================================
D [07/May/2009:02:33:02 -0400] [Job 130]
D [07/May/2009:02:33:02 -0400] [Job 130] Printer using device file "/dev/usblp0"...
D [07/May/2009:02:33:02 -0400] [Job 130] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0x7f6d9e2d8c20)
I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...
D [07/May/2009:02:33:02 -0400] cupsdCloseClient: 7
D [07/May/2009:02:33:02 -0400] [Job 130] Filetype: PDF
D [07/May/2009:02:33:02 -0400] [Job 130] Storing temporary files in /var/spool/cups/tmp
D [07/May/2009:02:33:02 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:33:02 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [07/May/2009:02:33:02 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:02 -0400] Get-Notifications /
D [07/May/2009:02:33:02 -0400] cupsdIsAuthorized: requesting-user-name="adam"
D [07/May/2009:02:33:02 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [07/May/2009:02:33:02 -0400] cupsdCloseClient: 7
D [07/May/2009:02:33:02 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:33:02 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:02 -0400] Get-Notifications /
D [07/May/2009:02:33:02 -0400] cupsdIsAuthorized: requesting-user-name="adam"
D [07/May/2009:02:33:02 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:33:02 -0400] PID 9462 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [07/May/2009:02:33:03 -0400] [Job 130] File contains 1 pages
D [07/May/2009:02:33:03 -0400] [Job 130] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-h734rF
D [07/May/2009:02:33:03 -0400] [Job 130] Starting process "kid3" (generation 1)
D [07/May/2009:02:33:03 -0400] [Job 130] Starting process "kid4" (generation 2)
D [07/May/2009:02:33:03 -0400] [Job 130] JCL: %-12345X@PJL
D [07/May/2009:02:33:03 -0400] [Job 130] <job data>
D [07/May/2009:02:33:03 -0400] [Job 130]
D [07/May/2009:02:33:03 -0400] [Job 130] Starting process "renderer" (generation 2)
D [07/May/2009:02:33:04 -0400] [Job 130] Read 8192 bytes of print data...
I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...
I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...
I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...
D [07/May/2009:02:33:04 -0400] [Job 130] Wrote 8192 bytes of print data...
D [07/May/2009:02:33:04 -0400] [Job 130] unable to read client data err=-2
D [07/May/2009:02:33:04 -0400] [Job 130] renderer received signal 8
D [07/May/2009:02:33:04 -0400] [Job 130] Kid3 exit status: 1
E [07/May/2009:02:33:04 -0400] PID 9463 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [07/May/2009:02:33:04 -0400] [Job 130] Read 2968 bytes of print data...
D [07/May/2009:02:33:04 -0400] [Job 130] Wrote 2968 bytes of print data...
D [07/May/2009:02:33:04 -0400] PID 9464 (/usr/lib/cups/backend/usb) exited with no errors.
D [07/May/2009:02:33:04 -0400] [Job 130] File 0 is complete.
E [07/May/2009:02:33:04 -0400] [Job 130] Job stopped due to filter errors.
I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...
I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...
D [07/May/2009:02:33:04 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:33:04 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [07/May/2009:02:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:04 -0400] Get-Notifications /
D [07/May/2009:02:33:04 -0400] cupsdIsAuthorized: requesting-user-name="adam"
D [07/May/2009:02:33:04 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [07/May/2009:02:33:04 -0400] cupsdCloseClient: 7
D [07/May/2009:02:33:04 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:04 -0400] Get-Notifications /
D [07/May/2009:02:33:04 -0400] cupsdIsAuthorized: requesting-user-name="adam"
D [07/May/2009:02:33:04 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:33:05 -0400] [Job 130] Unloading...
D [07/May/2009:02:33:19 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:33:19 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:19 -0400] Get-Job-Attributes ipp://localhost/jobs/130
D [07/May/2009:02:33:19 -0400] [Job 130] Loading attributes...
D [07/May/2009:02:33:19 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:33:19 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [07/May/2009:02:33:19 -0400] cupsdAuthorize: No authentication data provided.
D [07/May/2009:02:33:19 -0400] Cancel-Subscription /
D [07/May/2009:02:33:19 -0400] cupsdIsAuthorized: requesting-user-name="adam"
I [07/May/2009:02:33:19 -0400] Saving subscriptions.conf...
D [07/May/2009:02:33:19 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [07/May/2009:02:33:19 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [07/May/2009:02:33:19 -0400] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1
D [07/May/2009:02:33:19 -0400] cupsdAuthorize: No authentication data provided.

Diagnostic output says:
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Photosmart-C4400-series (default)>,
 'cups_instance': None,
 'cups_queue': 'Photosmart-C4400-series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://HP/Photosmart%20C4400%20series?serial=CN86JFG22C0557',
                       'printer-info': u'HP Photosmart C4400 series',
                       'printer-is-shared': True,
                       'printer-location': u'adam-laptop',
                       'printer-make-and-model': u'HP Photosmart c4400 Series hpijs, 3.9.2',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167964,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Photosmart-C4400-series'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'DryTime': u'Zero',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:Photosmart C4400 series;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;1284.4DL:4d,4e,1;CLS:PRINTER;DES:Q8388A;SN:CN86JFG22C0557;S:038000C484001021002c1800046c288003c;J:                    ;Z:0102,0503c289012c09,0600,0c0,0e00000000,0f00000000,10000000000000,12000,143,150;\x1f\x7f',
                      'device-info': u'HP Photosmart C4400 series USB #1',
                      'device-make-and-model': u'HP Photosmart C4400 series'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 2518,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_job_status': [(True,
                           130,
                           'Photosmart-C4400-series',
                           'Webern.jpg',
                           'Stopped',
                           {'DryTime': u'Zero',
                            'Duplex': u'None',
                            'InputSlot': u'Default',
                            'PageSize': u'Letter',
                            'PrintoutMode': u'Normal',
                            'Quality': u'FromPrintoutMode',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/pdf',
                            'job-hold-until': u'no-hold',
                            'job-id': 130,
                            'job-k-octets': 1072,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/130',
                            'job-name': u'Webern.jpg',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'adam',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1241677999,
                            'job-printer-uri': u'ipp://adam-laptop:631/printers/Photosmart-C4400-series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/130',
                            'job-uuid': u'urn:uuid:020bd675-7112-3ab4-58df-6412adb62107',
                            'number-up': 1,
                            'printer-uri': u'ipp://localhost:631/printers/Photosmart-C4400-series',
                            'time-at-completed': None,
                            'time-at-creation': 1241677982,
                            'time-at-processing': 1241677982})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [07/May/2009:02:32:34 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:32:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:34 -0400] Get-Jobs ipp://localhost/printers/',
               'D [07/May/2009:02:32:34 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:34 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:32:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:34 -0400] Get-Jobs ipp://localhost/printers/',
               'D [07/May/2009:02:32:34 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:34 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:32:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:34 -0400] Create-Printer-Subscription /',
               'D [07/May/2009:02:32:34 -0400] cupsdCreateSubscription(con=0x7f1ec1b326b0(6), uri="/")',
               'D [07/May/2009:02:32:34 -0400] pullmethod="ippget"',
               'D [07/May/2009:02:32:34 -0400] notify-lease-duration=86400',
               'D [07/May/2009:02:32:34 -0400] notify-time-interval=0',
               'D [07/May/2009:02:32:34 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [07/May/2009:02:32:34 -0400] Added subscription 61 for server',
               'I [07/May/2009:02:32:34 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:32:34 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:35 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:32:35 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:35 -0400] Get-Notifications /',
               'D [07/May/2009:02:32:35 -0400] cupsdIsAuthorized: requesting-user-name="adam"',
               'D [07/May/2009:02:32:35 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:37 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:32:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [07/May/2009:02:32:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:37 -0400] CUPS-Get-Printers',
               'D [07/May/2009:02:32:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [07/May/2009:02:32:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:37 -0400] CUPS-Get-Classes',
               'D [07/May/2009:02:32:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:37 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:32:52 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:32:52 -0400] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [07/May/2009:02:32:52 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:32:52 -0400] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [07/May/2009:02:32:52 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:52 -0400] CUPS-Get-Printers',
               'D [07/May/2009:02:32:52 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:52 -0400] cupsdCloseClient: 9',
               'D [07/May/2009:02:32:57 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:32:57 -0400] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [07/May/2009:02:32:57 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:32:58 -0400] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [07/May/2009:02:32:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:58 -0400] CUPS-Get-Printers',
               'D [07/May/2009:02:32:58 -0400] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [07/May/2009:02:32:58 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:32:58 -0400] cupsdCloseClient: 9',
               'D [07/May/2009:02:32:58 -0400] cupsdReadClient: 7 GET /printers/Photosmart-C4400-series.ppd HTTP/1.1',
               'D [07/May/2009:02:32:58 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:32:58 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:33:01 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:33:02 -0400] cupsdReadClient: 7 POST /printers/Photosmart-C4400-series HTTP/1.1',
               'D [07/May/2009:02:33:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:02 -0400] Print-Job ipp://localhost:631/printers/Photosmart-C4400-series',
               'D [07/May/2009:02:33:02 -0400] [Job ???] Auto-typing file...',
               'I [07/May/2009:02:33:02 -0400] [Job ???] Request file type is application/pdf.',
               'D [07/May/2009:02:33:02 -0400] add_job: requesting-user-name="adam"',
               'I [07/May/2009:02:33:02 -0400] [Job 130] Adding start banner page "none".',
               'I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...',
               'I [07/May/2009:02:33:02 -0400] [Job 130] Adding end banner page "none".',
               'I [07/May/2009:02:33:02 -0400] [Job 130] File of type application/pdf queued by "adam".',
               'D [07/May/2009:02:33:02 -0400] [Job 130] hold_until=0',
               'I [07/May/2009:02:33:02 -0400] [Job 130] Queued on "Photosmart-C4400-series" by "adam".',
               'I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:33:02 -0400] [Job 130] job-sheets=none,none',
               'D [07/May/2009:02:33:02 -0400] [Job 130] banner_page = 0',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[0]="Photosmart-C4400-series"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[1]="130"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[2]="adam"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[3]="Webern.jpg"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[4]="1"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[5]="DryTime=Zero PageSize=Letter Quality=FromPrintoutMode InputSlot=Default number-up=1 PrintoutMode=Normal Duplex=None job-uuid=urn:uuid:020bd675-7112-3ab4-58df-6412adb62107"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] argv[6]="/var/spool/cups/d00130-001"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[9]="SERVER_ADMIN=root@adam-laptop"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[12]="TZ=America/New_York"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[13]="USER=root"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[16]="IPP_PORT=631"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[17]="CHARSET=utf-8"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[18]="LANG=en_US.UTF8"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[19]="PPD=/etc/cups/ppd/Photosmart-C4400-series.ppd"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[20]="RIP_MAX_CACHE=8m"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[21]="CONTENT_TYPE=application/pdf"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[22]="DEVICE_URI=usb://HP/Photosmart%20C4400%20series?serial=CN86JFG22C0557"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[23]="PRINTER=Photosmart-C4400-series"',
               'D [07/May/2009:02:33:02 -0400] [Job 130] envp[24]="FINAL_CONTENT_TYPE=printer/Photosmart-C4400-series"',
               'I [07/May/2009:02:33:02 -0400] [Job 130] Started filter /usr/lib/cups/filter/pdftopdf (PID 9462)',
               'I [07/May/2009:02:33:02 -0400] [Job 130] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9463)',
               'I [07/May/2009:02:33:02 -0400] [Job 130] Started backend /usr/lib/cups/backend/usb (PID 9464)',
               'I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:33:02 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Getting input from file',
               'D [07/May/2009:02:33:02 -0400] [Job 130] foomatic-rip version 4.0.0.195 running...',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Parsing PPD file ...',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option Resolution',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option PageSize',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option Model',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option PrintoutMode',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option InputSlot',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option Duplex',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option DryTime',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option Quality',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option ImageableArea',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option PaperDimension',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Added option Font',
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Parameter Summary',
               'D [07/May/2009:02:33:02 -0400] [Job 130] -----------------',
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Spooler: cups',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Printer: Photosmart-C4400-series',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Shell: /bin/bash',
               'D [07/May/2009:02:33:02 -0400] [Job 130] PPD file: /etc/cups/ppd/Photosmart-C4400-series.ppd',
               'D [07/May/2009:02:33:02 -0400] [Job 130] ATTR file:',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Printer model: HP Photosmart c4400 Series hpijs, 3.9.2',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Job title: Webern.jpg',
               'D [07/May/2009:02:33:02 -0400] [Job 130] File(s) to be printed:',
               'D [07/May/2009:02:33:02 -0400] [Job 130] <STDIN>',
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               "D [07/May/2009:02:33:02 -0400] [Job 130] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [07/May/2009:02:33:02 -0400] [Job 130] Printing system options:',
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'number-up=1'",
               'D [07/May/2009:02:33:02 -0400] [Job 130] Unknown option number-up=1.',
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'job-uuid=urn:uuid:020bd675-7112-3ab4-58df-6412adb62107'",
               'D [07/May/2009:02:33:02 -0400] [Job 130] Unknown option job-uuid=urn:uuid:020bd675-7112-3ab4-58df-6412adb62107.',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Options from the PPD file:',
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'DryTime=Zero'",
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'PageSize=Letter'",
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'Quality=FromPrintoutMode'",
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'InputSlot=Default'",
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'PrintoutMode=Normal'",
               "D [07/May/2009:02:33:02 -0400] [Job 130] Pondering option 'Duplex=None'",
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               'D [07/May/2009:02:33:02 -0400] [Job 130] ================================================',
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               'D [07/May/2009:02:33:02 -0400] [Job 130] File: <STDIN>',
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               'D [07/May/2009:02:33:02 -0400] [Job 130] ================================================',
               'D [07/May/2009:02:33:02 -0400] [Job 130]',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Printer using device file "/dev/usblp0"...',
               'D [07/May/2009:02:33:02 -0400] [Job 130] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0x7f6d9e2d8c20)',
               'I [07/May/2009:02:33:02 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:33:02 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Filetype: PDF',
               'D [07/May/2009:02:33:02 -0400] [Job 130] Storing temporary files in /var/spool/cups/tmp',
               'D [07/May/2009:02:33:02 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:33:02 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [07/May/2009:02:33:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:02 -0400] Get-Notifications /',
               'D [07/May/2009:02:33:02 -0400] cupsdIsAuthorized: requesting-user-name="adam"',
               'D [07/May/2009:02:33:02 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:02 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:33:02 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:33:02 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:02 -0400] Get-Notifications /',
               'D [07/May/2009:02:33:02 -0400] cupsdIsAuthorized: requesting-user-name="adam"',
               'D [07/May/2009:02:33:02 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:02 -0400] PID 9462 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [07/May/2009:02:33:03 -0400] [Job 130] File contains 1 pages',
               'D [07/May/2009:02:33:03 -0400] [Job 130] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-h734rF',
               'D [07/May/2009:02:33:03 -0400] [Job 130] Starting process "kid3" (generation 1)',
               'D [07/May/2009:02:33:03 -0400] [Job 130] Starting process "kid4" (generation 2)',
               'D [07/May/2009:02:33:03 -0400] [Job 130] JCL: \x1b%-12345X@PJL',
               'D [07/May/2009:02:33:03 -0400] [Job 130] <job data>',
               'D [07/May/2009:02:33:03 -0400] [Job 130]',
               'D [07/May/2009:02:33:03 -0400] [Job 130] Starting process "renderer" (generation 2)',
               'D [07/May/2009:02:33:04 -0400] [Job 130] Read 8192 bytes of print data...',
               'I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...',
               'I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...',
               'I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:33:04 -0400] [Job 130] Wrote 8192 bytes of print data...',
               'D [07/May/2009:02:33:04 -0400] [Job 130] unable to read client data err=-2',
               'D [07/May/2009:02:33:04 -0400] [Job 130] renderer received signal 8',
               'D [07/May/2009:02:33:04 -0400] [Job 130] Kid3 exit status: 1',
               'E [07/May/2009:02:33:04 -0400] PID 9463 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!',
               'D [07/May/2009:02:33:04 -0400] [Job 130] Read 2968 bytes of print data...',
               'D [07/May/2009:02:33:04 -0400] [Job 130] Wrote 2968 bytes of print data...',
               'D [07/May/2009:02:33:04 -0400] PID 9464 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [07/May/2009:02:33:04 -0400] [Job 130] File 0 is complete.',
               'E [07/May/2009:02:33:04 -0400] [Job 130] Job stopped due to filter errors.',
               'I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...',
               'I [07/May/2009:02:33:04 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:33:04 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:33:04 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [07/May/2009:02:33:04 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:04 -0400] Get-Notifications /',
               'D [07/May/2009:02:33:04 -0400] cupsdIsAuthorized: requesting-user-name="adam"',
               'D [07/May/2009:02:33:04 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:04 -0400] cupsdCloseClient: 7',
               'D [07/May/2009:02:33:04 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:33:04 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:04 -0400] Get-Notifications /',
               'D [07/May/2009:02:33:04 -0400] cupsdIsAuthorized: requesting-user-name="adam"',
               'D [07/May/2009:02:33:04 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:05 -0400] [Job 130] Unloading...',
               'D [07/May/2009:02:33:19 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:33:19 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:19 -0400] Get-Job-Attributes ipp://localhost/jobs/130',
               'D [07/May/2009:02:33:19 -0400] [Job 130] Loading attributes...',
               'D [07/May/2009:02:33:19 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:19 -0400] cupsdReadClient: 6 POST / HTTP/1.1',
               'D [07/May/2009:02:33:19 -0400] cupsdAuthorize: No authentication data provided.',
               'D [07/May/2009:02:33:19 -0400] Cancel-Subscription /',
               'D [07/May/2009:02:33:19 -0400] cupsdIsAuthorized: requesting-user-name="adam"',
               'I [07/May/2009:02:33:19 -0400] Saving subscriptions.conf...',
               'D [07/May/2009:02:33:19 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)',
               'D [07/May/2009:02:33:19 -0400] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [07/May/2009:02:33:19 -0400] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [07/May/2009:02:33:19 -0400] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'none']}
Page 11 (Locale issues):
{'job_page_size': u'Letter',
 'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

One more edit, never had this problem before Jaunty

---

