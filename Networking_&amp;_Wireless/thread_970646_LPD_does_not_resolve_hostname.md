---
title: "LPD does not resolve hostname"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by fiu on 2008-11-04
I upgraded to Interpid recently (a fresh installation) and tried to setup an LPD printer now. The printserver is called printman. The queue is set to "lpr://printman/hp", which was a working configuration using Ubuntu 8.04.
However, when I try to print now, I get the message "Stopped - Unable to locate printer 'printman'".
If I use the ip-address of printman instead, printing works. :???:

Entering ```
ping printman
``` seems to work correctly. Then the name resolution is successful and I get responses. :?:

Here's the debug-log, but at least I didn't find any line of it that could help..
```
D [04/Nov/2008:16:25:21 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:21 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:21 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:21 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:21 +0100] Get-Jobs ipp://localhost/jobs/
D [04/Nov/2008:16:25:21 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:21 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:21 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:21 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:21 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:21 +0100] Create-Printer-Subscription /
D [04/Nov/2008:16:25:21 +0100] cupsdCreateSubscription(con=0xb8cb9f48(7), uri="/")
D [04/Nov/2008:16:25:21 +0100] pullmethod="ippget"
D [04/Nov/2008:16:25:21 +0100] notify-lease-duration=86400
D [04/Nov/2008:16:25:21 +0100] notify-time-interval=0
D [04/Nov/2008:16:25:21 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [04/Nov/2008:16:25:21 +0100] Added subscription 12 for server
I [04/Nov/2008:16:25:21 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:21 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:21 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:22 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:22 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:22 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:22 +0100] Get-Notifications /
D [04/Nov/2008:16:25:22 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:22 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:22 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:35 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:35 +0100] cupsdReadClient: 7 POST /printers/hp HTTP/1.1
D [04/Nov/2008:16:25:35 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:35 +0100] Print-Job ipp://localhost/printers/hp
D [04/Nov/2008:16:25:35 +0100] add_job: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:35 +0100] Adding default job-sheets values "none,none"...
I [04/Nov/2008:16:25:35 +0100] [Job 7] Adding start banner page "none".
I [04/Nov/2008:16:25:35 +0100] Saving subscriptions.conf...
I [04/Nov/2008:16:25:35 +0100] [Job 7] Adding end banner page "none".
I [04/Nov/2008:16:25:35 +0100] [Job 7] File of type application/postscript queued by "lorenz".
D [04/Nov/2008:16:25:35 +0100] [Job 7] hold_until=0
I [04/Nov/2008:16:25:35 +0100] [Job 7] Queued on "hp" by "lorenz".
I [04/Nov/2008:16:25:35 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:35 +0100] [Job 7] job-sheets=none,none
D [04/Nov/2008:16:25:35 +0100] [Job 7] banner_page = 0
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[0]="hp"
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[1]="7"
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[2]="lorenz"
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[3]="Test Page"
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[4]="1"
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[5]="job-uuid=urn:uuid:79d69e9d-de53-3a74-7286-29cfa730993d"
D [04/Nov/2008:16:25:35 +0100] [Job 7] argv[6]="/var/spool/cups/d00007-001"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[9]="SERVER_ADMIN=root@lbox"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[10]="SOFTWARE=CUPS/1.3.9"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[12]="TZ=Europe/Copenhagen"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[13]="USER=root"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[16]="IPP_PORT=631"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[17]="CHARSET=utf-8"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[18]="LANG=en_US.UTF8"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[19]="PPD=/etc/cups/ppd/hp.ppd"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[20]="RIP_MAX_CACHE=8m"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[21]="CONTENT_TYPE=application/postscript"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[22]="DEVICE_URI=lpd://printman/hp"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[23]="PRINTER=hp"
D [04/Nov/2008:16:25:35 +0100] [Job 7] envp[24]="FINAL_CONTENT_TYPE=printer/hp"
I [04/Nov/2008:16:25:35 +0100] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 30461)
I [04/Nov/2008:16:25:35 +0100] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 30463)
I [04/Nov/2008:16:25:35 +0100] [Job 7] Started filter /usr/lib/cups/filter/foomatic-rip (PID 30466)
I [04/Nov/2008:16:25:35 +0100] [Job 7] Started backend /usr/lib/cups/backend/lpd (PID 30468)
I [04/Nov/2008:16:25:35 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:35 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:35 +0100] [Job 7] pstopdf argv[6] = 7 lorenz Test Page 1 job-uuid=urn:uuid:79d69e9d-de53-3a74-7286-29cfa730993d /var/spool/cups/d00007-001
D [04/Nov/2008:16:25:35 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:35 +0100] [Job 7] Getting input from file
D [04/Nov/2008:16:25:35 +0100] [Job 7] foomatic-rip version 4.0.0.177 running...
D [04/Nov/2008:16:25:35 +0100] [Job 7] Parsing PPD file ...
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option Resolution
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option PageSize
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option Model
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option PrintoutMode
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option InputSlot
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option Duplex
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option Quality
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option ImageableArea
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option PaperDimension
D [04/Nov/2008:16:25:35 +0100] [Job 7] Added option Font
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] Parameter Summary
D [04/Nov/2008:16:25:35 +0100] [Job 7] -----------------
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] Spooler: cups
D [04/Nov/2008:16:25:35 +0100] [Job 7] Printer: hp
D [04/Nov/2008:16:25:35 +0100] [Job 7] Shell: /bin/bash
D [04/Nov/2008:16:25:35 +0100] [Job 7] PPD file: /etc/cups/ppd/hp.ppd
D [04/Nov/2008:16:25:35 +0100] [Job 7] ATTR file:
D [04/Nov/2008:16:25:35 +0100] [Job 7] Printer model: HP LaserJet 4250 Foomatic/hpijs, hpijs 2.8.7
D [04/Nov/2008:16:25:35 +0100] [Job 7] Job title: Test Page
D [04/Nov/2008:16:25:35 +0100] [Job 7] File(s) to be printed:
D [04/Nov/2008:16:25:35 +0100] [Job 7] <STDIN>
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [04/Nov/2008:16:25:35 +0100] [Job 7] Pondering option 'job-uuid=urn:uuid:79d69e9d-de53-3a74-7286-29cfa730993d'
D [04/Nov/2008:16:25:35 +0100] [Job 7] Unknown option job-uuid=urn:uuid:79d69e9d-de53-3a74-7286-29cfa730993d.
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] ================================================
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] File: <STDIN>
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] ================================================
D [04/Nov/2008:16:25:35 +0100] [Job 7]
D [04/Nov/2008:16:25:35 +0100] [Job 7] Injecting PostScript: <</.HWMargins[18.00 14.40 18.00 14.40] /Margins[0 0]>>setpagedevice
D [04/Nov/2008:16:25:35 +0100] [Job 7] Page = 595x842; 18,14 to 577,828
D [04/Nov/2008:16:25:35 +0100] [Job 7] slow_collate=0, slow_duplex=0, slow_order=0
D [04/Nov/2008:16:25:35 +0100] [Job 7] Before copy_comments - %!PS-Adobe-3.0
D [04/Nov/2008:16:25:35 +0100] [Job 7] %!PS-Adobe-3.0
E [04/Nov/2008:16:25:35 +0100] [Job 7] No %%BoundingBox: comment in header!
I [04/Nov/2008:16:25:35 +0100] Saving subscriptions.conf...
E [04/Nov/2008:16:25:35 +0100] [Job 7] No %%Pages: comment in header!
I [04/Nov/2008:16:25:35 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:35 +0100] [Job 7] Before copy_prolog - <</.HWMargins[18.00 14.40 18.00 14.40] /Margins[0 0]>>setpagedevice
D [04/Nov/2008:16:25:35 +0100] [Job 7] Before copy_setup - %%Page: 1 1
D [04/Nov/2008:16:25:35 +0100] [Job 7] Before page loop - %%Page: 1 1
D [04/Nov/2008:16:25:35 +0100] [Job 7] Copying page 1...
D [04/Nov/2008:16:25:35 +0100] [Job 7] pagew = 559.0, pagel = 813.2
D [04/Nov/2008:16:25:35 +0100] [Job 7] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [04/Nov/2008:16:25:35 +0100] [Job 7] PageLeft = 18.0, PageRight = 577.0
D [04/Nov/2008:16:25:35 +0100] [Job 7] PageTop = 827.6, PageBottom = 14.4
D [04/Nov/2008:16:25:35 +0100] [Job 7] PageWidth = 595.0, PageLength = 842.0
D [04/Nov/2008:16:25:35 +0100] [Job 7] Wrote 1 pages...
D [04/Nov/2008:16:25:36 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] Get-Notifications /
D [04/Nov/2008:16:25:36 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdAcceptClient: 8 from localhost (Domain)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 8 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] Get-Jobs ipp://localhost/jobs/
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdCloseClient: 8
D [04/Nov/2008:16:25:36 +0100] cupsdAcceptClient: 8 from localhost (Domain)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 8 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] Get-Notifications /
D [04/Nov/2008:16:25:36 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 8 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] Get-Job-Attributes ipp://localhost/jobs/7
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdAcceptClient: 11 from localhost (Domain)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Printers
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Classes
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Default
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Printers
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Classes
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Default
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Printers
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdCloseClient: 8
D [04/Nov/2008:16:25:36 +0100] cupsdAcceptClient: 8 from localhost (Domain)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 8 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] Get-Notifications /
D [04/Nov/2008:16:25:36 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdCloseClient: 8
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Classes
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:36 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:36 +0100] CUPS-Get-Default
D [04/Nov/2008:16:25:36 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:36 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:36 +0100] [Job 7] Filetype: PDF
D [04/Nov/2008:16:25:36 +0100] [Job 7] Storing temporary files in /var/spool/cups/tmp
D [04/Nov/2008:16:25:36 +0100] PID 30461 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [04/Nov/2008:16:25:36 +0100] PID 30463 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [04/Nov/2008:16:25:36 +0100] [Job 7] File contains 1 pages
D [04/Nov/2008:16:25:36 +0100] [Job 7] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-u20uc8
D [04/Nov/2008:16:25:36 +0100] [Job 7] Starting process "kid3" (generation 1)
D [04/Nov/2008:16:25:36 +0100] [Job 7] Starting process "kid4" (generation 2)
D [04/Nov/2008:16:25:36 +0100] [Job 7] JCL: <job data>
D [04/Nov/2008:16:25:36 +0100] [Job 7]
D [04/Nov/2008:16:25:36 +0100] [Job 7] Starting process "renderer" (generation 2)
D [04/Nov/2008:16:25:37 +0100] [Job 7] renderer exited with status 0
D [04/Nov/2008:16:25:37 +0100] [Job 7] kid4 exited with status 0
D [04/Nov/2008:16:25:37 +0100] [Job 7] kid3 finished
D [04/Nov/2008:16:25:37 +0100] [Job 7] Kid3 exit status: 0
D [04/Nov/2008:16:25:37 +0100] [Job 7]
D [04/Nov/2008:16:25:37 +0100] [Job 7] Closing foomatic-rip.
E [04/Nov/2008:16:25:37 +0100] [Job 7] Unable to locate printer 'printman'!
I [04/Nov/2008:16:25:37 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:37 +0100] PID 30466 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
E [04/Nov/2008:16:25:37 +0100] PID 30468 (/usr/lib/cups/backend/lpd) stopped with status 4!
D [04/Nov/2008:16:25:37 +0100] [Job 7] File 0 is complete.
I [04/Nov/2008:16:25:37 +0100] [Job 7] Backend returned status 4 (stop printer)
I [04/Nov/2008:16:25:37 +0100] Saving subscriptions.conf...
I [04/Nov/2008:16:25:37 +0100] Saving subscriptions.conf...
I [04/Nov/2008:16:25:37 +0100] Saving printers.conf...
I [04/Nov/2008:16:25:37 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:38 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] Get-Jobs ipp://localhost/jobs/
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:38 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] Get-Notifications /
D [04/Nov/2008:16:25:38 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdAcceptClient: 8 from localhost (Domain)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 8 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] Get-Notifications /
D [04/Nov/2008:16:25:38 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Printers
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Classes
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Default
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Printers
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Classes
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Default
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdCloseClient: 7

D [04/Nov/2008:16:25:38 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] Get-Notifications /
D [04/Nov/2008:16:25:38 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Printers
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Classes
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdReadClient: 11 POST / HTTP/1.1
D [04/Nov/2008:16:25:38 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:38 +0100] CUPS-Get-Default
D [04/Nov/2008:16:25:38 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:38 +0100] cupsdCloseClient: 8
D [04/Nov/2008:16:25:46 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:46 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:46 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:46 +0100] Get-Job-Attributes ipp://localhost/jobs/7
D [04/Nov/2008:16:25:46 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:46 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:46 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:46 +0100] cupsdReadClient: 7 POST / HTTP/1.1
D [04/Nov/2008:16:25:46 +0100] cupsdAuthorize: No authentication data provided.
D [04/Nov/2008:16:25:46 +0100] Cancel-Subscription /
D [04/Nov/2008:16:25:46 +0100] cupsdIsAuthorized: requesting-user-name="lorenz"
I [04/Nov/2008:16:25:46 +0100] Saving subscriptions.conf...
D [04/Nov/2008:16:25:46 +0100] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [04/Nov/2008:16:25:46 +0100] cupsdCloseClient: 7
D [04/Nov/2008:16:25:46 +0100] cupsdAcceptClient: 7 from localhost (Domain)
D [04/Nov/2008:16:25:46 +0100] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1
D [04/Nov/2008:16:25:46 +0100] cupsdAuthorize: No authentication data provided.
```

Using the ip-address seems to be a workaround which is ok, but surely not the best solution. So is there anything I'm doing wrong or that I can change to make it work?

Thanks!

---

