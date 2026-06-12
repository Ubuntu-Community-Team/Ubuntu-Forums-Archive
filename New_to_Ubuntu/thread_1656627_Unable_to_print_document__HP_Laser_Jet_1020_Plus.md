---
title: "Unable to print document : HP Laser Jet 1020 Plus"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by pavanmatham on 2010-12-31
Hi,

I shifted from windows to Ubuntu 10.10 recently. I have been facing a problem in printing now.
Earlier, I used to print the documents through the printer (HP Laser Jet 1020 Plus) installed on another desktop( in network). 
Now, since this morning while I was trying to print a document I am getting error.
Can any one pl. help me.

 Here is the Error log.
----
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:37:47 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:37:47 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:37:47 +0530] cupsdReadClient: 12 1.1 Get-Jobs 1
D [31/Dec/2010:14:37:47 +0530] Get-Jobs ipp://localhost/printers/
D [31/Dec/2010:14:37:47 +0530] [Job 20] Loading attributes...
D [31/Dec/2010:14:37:47 +0530] [Job 21] Loading attributes...
D [31/Dec/2010:14:37:47 +0530] [Job 22] Loading attributes...
D [31/Dec/2010:14:37:47 +0530] [Job 23] Loading attributes...
D [31/Dec/2010:14:37:47 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:37:47 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:37:47 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:37:47 +0530] cupsdReadClient: 12 1.1 Get-Jobs 1
D [31/Dec/2010:14:37:47 +0530] Get-Jobs ipp://localhost/printers/
D [31/Dec/2010:14:37:47 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:37:47 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:37:47 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:37:47 +0530] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [31/Dec/2010:14:37:47 +0530] Create-Printer-Subscription /
D [31/Dec/2010:14:37:47 +0530] cupsdCreateSubscription(con=0x211ba3c0(12), uri="/")
D [31/Dec/2010:14:37:47 +0530] pullmethod="ippget"
D [31/Dec/2010:14:37:47 +0530] notify-lease-duration=86400
D [31/Dec/2010:14:37:47 +0530] notify-time-interval=0
D [31/Dec/2010:14:37:47 +0530] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [31/Dec/2010:14:37:47 +0530] Added subscription 19 for server
D [31/Dec/2010:14:37:47 +0530] cupsdMarkDirty(-----S)
D [31/Dec/2010:14:37:47 +0530] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [31/Dec/2010:14:37:47 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:37:49 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:37:49 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:37:49 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:37:49 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [31/Dec/2010:14:37:49 +0530] Get-Notifications /
D [31/Dec/2010:14:37:49 +0530] cupsdIsAuthorized: requesting-user-name="pavan"
D [31/Dec/2010:14:37:49 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [31/Dec/2010:14:37:49 +0530] cupsdSetBusyState: Dirty files
I [31/Dec/2010:14:38:13 +0530] Generating printcap /var/run/cups/printcap...
I [31/Dec/2010:14:38:13 +0530] Saving subscriptions.conf...
D [31/Dec/2010:14:38:13 +0530] cupsdSetBusyState: Not busy
D [31/Dec/2010:14:38:29 +0530] cupsdAcceptClient: 13 from localhost (Domain)
D [31/Dec/2010:14:38:29 +0530] cupsdReadClient: 13 POST /printers/HP-LaserJet-1020 HTTP/1.1
D [31/Dec/2010:14:38:29 +0530] cupsdSetBusyState: Active clients
D [31/Dec/2010:14:38:29 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:29 +0530] cupsdReadClient: 13 1.1 Print-Job 1
D [31/Dec/2010:14:38:29 +0530] Print-Job ipp://localhost/printers/HP-LaserJet-1020
D [31/Dec/2010:14:38:29 +0530] [Job ???] Auto-typing file...
I [31/Dec/2010:14:38:29 +0530] [Job ???] Request file type is application/vnd.cups-banner.
D [31/Dec/2010:14:38:29 +0530] cupsdMarkDirty(----J-)
D [31/Dec/2010:14:38:29 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:29 +0530] add_job: requesting-user-name="pavan"
D [31/Dec/2010:14:38:29 +0530] Adding default job-sheets values "none,none"...
I [31/Dec/2010:14:38:29 +0530] [Job 24] Adding start banner page "none".
D [31/Dec/2010:14:38:29 +0530] cupsdMarkDirty(-----S)
D [31/Dec/2010:14:38:29 +0530] cupsdMarkDirty(----J-)
I [31/Dec/2010:14:38:29 +0530] [Job 24] Adding end banner page "none".
I [31/Dec/2010:14:38:29 +0530] [Job 24] File of type application/vnd.cups-banner queued by "pavan".
D [31/Dec/2010:14:38:29 +0530] [Job 24] hold_until=0
I [31/Dec/2010:14:38:29 +0530] [Job 24] Queued on "HP-LaserJet-1020" by "pavan".
D [31/Dec/2010:14:38:29 +0530] cupsdMarkDirty(----J-)
D [31/Dec/2010:14:38:29 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [31/Dec/2010:14:38:29 +0530] cupsdMarkDirty(-----S)
D [31/Dec/2010:14:38:29 +0530] [Job 24] job-sheets=none,none
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[0]="HP-LaserJet-1020"
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[1]="24"
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[2]="pavan"
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[3]="Test Page"
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[4]="1"
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[5]="job-uuid=urn:uuid:9375bf99-abd0-312c-4a05-6cc2aaa98d0c job-originating-host-name=localhost"
D [31/Dec/2010:14:38:29 +0530] [Job 24] argv[6]="/var/spool/cups/d00024-001"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[8]="HOME=/var/spool/cups/tmp"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[10]="SERVER_ADMIN=root@pavan-Presario-C700-Notebook-PC"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[11]="SOFTWARE=CUPS/1.4.4"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[13]="USER=root"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[16]="IPP_PORT=631"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[17]="CHARSET=utf-8"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[18]="LANG=en_IN.UTF-8"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[19]="PPD=/etc/cups/ppd/HP-LaserJet-1020.ppd"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[20]="RIP_MAX_CACHE=auto"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[22]="DEVICE_URI=smb://wdf/HPLaserJ"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[23]="PRINTER_INFO=HP LaserJet 1020"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[24]="PRINTER_LOCATION="
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[25]="PRINTER=HP-LaserJet-1020"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[26]="CUPS_FILETYPE=document"
D [31/Dec/2010:14:38:29 +0530] [Job 24] envp[27]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-1020"
I [31/Dec/2010:14:38:29 +0530] [Job 24] Started filter /usr/lib/cups/filter/bannertops (PID 2313)
I [31/Dec/2010:14:38:29 +0530] [Job 24] Started filter /usr/lib/cups/filter/pstopdf (PID 2314)
I [31/Dec/2010:14:38:29 +0530] [Job 24] Started filter /usr/lib/cups/filter/pdftopdf (PID 2315)
I [31/Dec/2010:14:38:29 +0530] [Job 24] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2316)
I [31/Dec/2010:14:38:29 +0530] [Job 24] Started backend /usr/lib/cups/backend/smb (PID 2317)
D [31/Dec/2010:14:38:29 +0530] cupsdMarkDirty(-----S)
D [31/Dec/2010:14:38:29 +0530] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-LaserJet-1020) from localhost
D [31/Dec/2010:14:38:29 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [31/Dec/2010:14:38:29 +0530] [Job 24] Getting input from file
D [31/Dec/2010:14:38:29 +0530] [Job 24] foomatic-rip version 4.0.5.223 running...
D [31/Dec/2010:14:38:29 +0530] [Job 24] Parsing PPD file ...
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option Resolution
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option PageSize
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option Model
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option PrintoutMode
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option MediaType
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option InputSlot
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option Quality
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option ImageableArea
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option PaperDimension
D [31/Dec/2010:14:38:29 +0530] [Job 24] Added option Font
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:29 +0530] [Job 24] Parameter Summary
D [31/Dec/2010:14:38:29 +0530] [Job 24] -----------------
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:29 +0530] [Job 24] Spooler: cups
D [31/Dec/2010:14:38:29 +0530] [Job 24] Printer: HP-LaserJet-1020
D [31/Dec/2010:14:38:29 +0530] [Job 24] Shell: /bin/bash
D [31/Dec/2010:14:38:29 +0530] [Job 24] PPD file: /etc/cups/ppd/HP-LaserJet-1020.ppd
D [31/Dec/2010:14:38:29 +0530] [Job 24] ATTR file:
D [31/Dec/2010:14:38:29 +0530] [Job 24] Printer model: HP LaserJet 1020 hpijs, 3.10.6, requires proprietary plugin
D [31/Dec/2010:14:38:29 +0530] [Job 24] Job title: Test Page
D [31/Dec/2010:14:38:29 +0530] [Job 24] File(s) to be printed:
D [31/Dec/2010:14:38:29 +0530] [Job 24] <STDIN>
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:29 +0530] [Job 24] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [31/Dec/2010:14:38:29 +0530] [Job 24] Printing system options:
D [31/Dec/2010:14:38:29 +0530] [Job 24] Pondering option 'job-uuid=urn:uuid:9375bf99-abd0-312c-4a05-6cc2aaa98d0c'
D [31/Dec/2010:14:38:29 +0530] [Job 24] Unknown option job-uuid=urn:uuid:9375bf99-abd0-312c-4a05-6cc2aaa98d0c.
D [31/Dec/2010:14:38:29 +0530] [Job 24] Pondering option 'job-originating-host-name=localhost'
D [31/Dec/2010:14:38:29 +0530] [Job 24] Unknown option job-originating-host-name=localhost.
D [31/Dec/2010:14:38:29 +0530] [Job 24] Options from the PPD file:
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:29 +0530] [Job 24] ================================================
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:29 +0530] [Job 24] File: <STDIN>
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:29 +0530] [Job 24] ================================================
D [31/Dec/2010:14:38:29 +0530] [Job 24]
D [31/Dec/2010:14:38:30 +0530] [Job 24] load_banner(filename="/var/spool/cups/d00024-001")
D [31/Dec/2010:14:38:30 +0530] [Job 24] pstopdf 5 args: 24 pavan Test Page 1 job-uuid=urn:uuid:9375bf99-abd0-312c-4a05-6cc2aaa98d0c job-originating-host-name=localhost
D [31/Dec/2010:14:38:30 +0530] [Job 24] PPD: /etc/cups/ppd/HP-LaserJet-1020.ppd
D [31/Dec/2010:14:38:30 +0530] cupsdAcceptClient: 17 from localhost (Domain)
D [31/Dec/2010:14:38:30 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [31/Dec/2010:14:38:30 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [31/Dec/2010:14:38:30 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:30 +0530] cupsdReadClient: 17 1.1 Get-Notifications 1
D [31/Dec/2010:14:38:30 +0530] Get-Notifications /
D [31/Dec/2010:14:38:30 +0530] cupsdIsAuthorized: requesting-user-name="pavan"
D [31/Dec/2010:14:38:30 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [31/Dec/2010:14:38:30 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [31/Dec/2010:14:38:30 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [31/Dec/2010:14:38:30 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [31/Dec/2010:14:38:30 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:30 +0530] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [31/Dec/2010:14:38:30 +0530] Get-Job-Attributes ipp://localhost/jobs/24
D [31/Dec/2010:14:38:30 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/24) from localhost
D [31/Dec/2010:14:38:30 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [31/Dec/2010:14:38:30 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:38:30 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [31/Dec/2010:14:38:30 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:30 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [31/Dec/2010:14:38:30 +0530] Get-Notifications /
D [31/Dec/2010:14:38:30 +0530] cupsdIsAuthorized: requesting-user-name="pavan"
D [31/Dec/2010:14:38:30 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [31/Dec/2010:14:38:30 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [31/Dec/2010:14:38:30 +0530] [Job 24] Page = 595x842; 18,14 to 577,828
D [31/Dec/2010:14:38:30 +0530] [Job 24] Connected using Kerberos...
D [31/Dec/2010:14:38:30 +0530] [Job 24] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [31/Dec/2010:14:38:30 +0530] [Job 24] PNG image: 192x128x8, color_type=2 (RGB)
D [31/Dec/2010:14:38:30 +0530] PID 2313 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [31/Dec/2010:14:38:30 +0530] [Job 24] Resolution: 600
D [31/Dec/2010:14:38:30 +0530] [Job 24] Page size: A4
D [31/Dec/2010:14:38:30 +0530] [Job 24] Width: 595, height: 842, absolute margins: 18, 14.39999961853, 577, 827.60000038147
D [31/Dec/2010:14:38:30 +0530] [Job 24] Relative margins: 18, 14.39999961853, 18, 14.39999961853
D [31/Dec/2010:14:38:30 +0530] [Job 24] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [31/Dec/2010:14:38:30 +0530] [Job 24] PostScript to be injected:
D [31/Dec/2010:14:38:30 +0530] [Job 24] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sOutputFile=-  -c .setpdfwrite -f -
D [31/Dec/2010:14:38:31 +0530] cupsdReadClient: 17 WAITING Closing on EOF
D [31/Dec/2010:14:38:31 +0530] cupsdCloseClient: 17
D [31/Dec/2010:14:38:33 +0530] PID 2314 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [31/Dec/2010:14:38:33 +0530] [Job 24] Filetype: PDF
D [31/Dec/2010:14:38:33 +0530] [Job 24] Storing temporary files in /var/spool/cups/tmp
D [31/Dec/2010:14:38:33 +0530] PID 2315 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [31/Dec/2010:14:38:33 +0530] [Job 24] File contains 1 pages
D [31/Dec/2010:14:38:33 +0530] [Job 24] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet 1018" -r600 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-fOWc5q
D [31/Dec/2010:14:38:33 +0530] [Job 24] Starting process "kid3" (generation 1)
D [31/Dec/2010:14:38:33 +0530] [Job 24] Starting process "kid4" (generation 2)
D [31/Dec/2010:14:38:33 +0530] [Job 24] Starting process "renderer" (generation 2)
D [31/Dec/2010:14:38:33 +0530] [Job 24] JCL: %-12345X@PJL
D [31/Dec/2010:14:38:33 +0530] [Job 24] <job data>
D [31/Dec/2010:14:38:33 +0530] [Job 24]
D [31/Dec/2010:14:38:33 +0530] [Job 24] prnt/hpijs/hpijs.cpp 268: unable to set device=HP LaserJet 1018, err=48
D [31/Dec/2010:14:38:33 +0530] [Job 24] prnt/hpijs/hpijs.cpp 289: unable to set device=HP LaserJet 1018, err=48
D [31/Dec/2010:14:38:33 +0530] [Job 24] prnt/hpijs/hpijs.cpp 694: unable to read client data err=-2
D [31/Dec/2010:14:38:33 +0530] [Job 24] renderer exited with status 1
D [31/Dec/2010:14:38:33 +0530] [Job 24] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [31/Dec/2010:14:38:33 +0530] PID 2316 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [31/Dec/2010:14:38:34 +0530] PID 2317 (/usr/lib/cups/backend/smb) exited with no errors.
D [31/Dec/2010:14:38:34 +0530] cupsdMarkDirty(-----S)
E [31/Dec/2010:14:38:34 +0530] [Job 24] Job stopped due to filter errors; please consult the error_log file for details.
D [31/Dec/2010:14:38:34 +0530] cupsdMarkDirty(----J-)
D [31/Dec/2010:14:38:34 +0530] cupsdMarkDirty(-----S)
D [31/Dec/2010:14:38:34 +0530] cupsdAcceptClient: 15 from localhost (Domain)
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 15 POST / HTTP/1.1
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 15 1.1 Get-Notifications 1
D [31/Dec/2010:14:38:34 +0530] Get-Notifications /
D [31/Dec/2010:14:38:34 +0530] cupsdIsAuthorized: requesting-user-name="pavan"
D [31/Dec/2010:14:38:34 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdAcceptClient: 17 from localhost (Domain)
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 13 WAITING Closing on EOF
D [31/Dec/2010:14:38:34 +0530] cupsdCloseClient: 13
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [31/Dec/2010:14:38:34 +0530] Get-Printer-Attributes ipp://pavan-Presario-C700-Notebook-PC:631/printers/HP-LaserJet-1020
D [31/Dec/2010:14:38:34 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://pavan-Presario-C700-Notebook-PC:631/printers/HP-LaserJet-1020) from localhost
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [31/Dec/2010:14:38:34 +0530] Get-Job-Attributes ipp://localhost/jobs/24
D [31/Dec/2010:14:38:34 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/24) from localhost
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [31/Dec/2010:14:38:34 +0530] Get-Notifications /
D [31/Dec/2010:14:38:34 +0530] cupsdIsAuthorized: requesting-user-name="pavan"
D [31/Dec/2010:14:38:34 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [31/Dec/2010:14:38:34 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:34 +0530] cupsdReadClient: 15 WAITING Closing on EOF
D [31/Dec/2010:14:38:34 +0530] cupsdCloseClient: 15
D [31/Dec/2010:14:38:35 +0530] [Job 24] Unloading...
D [31/Dec/2010:14:38:45 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:38:45 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:45 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:45 +0530] Report: clients=2
D [31/Dec/2010:14:38:45 +0530] Report: jobs=5
D [31/Dec/2010:14:38:45 +0530] Report: jobs-active=5
D [31/Dec/2010:14:38:45 +0530] Report: printers=1
D [31/Dec/2010:14:38:45 +0530] Report: printers-implicit=0
D [31/Dec/2010:14:38:45 +0530] Report: stringpool-string-count=3132
D [31/Dec/2010:14:38:45 +0530] Report: stringpool-alloc-bytes=10120
D [31/Dec/2010:14:38:45 +0530] Report: stringpool-total-bytes=64512
D [31/Dec/2010:14:38:45 +0530] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [31/Dec/2010:14:38:45 +0530] Get-Job-Attributes ipp://localhost/jobs/24
D [31/Dec/2010:14:38:45 +0530] [Job 24] Loading attributes...
D [31/Dec/2010:14:38:45 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/24) from localhost
D [31/Dec/2010:14:38:45 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:46 +0530] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [31/Dec/2010:14:38:46 +0530] Cancel-Subscription /
D [31/Dec/2010:14:38:46 +0530] cupsdIsAuthorized: requesting-user-name="pavan"
D [31/Dec/2010:14:38:46 +0530] cupsdMarkDirty(-----S)
D [31/Dec/2010:14:38:46 +0530] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdAuthorize: No authentication data provided.
D [31/Dec/2010:14:38:46 +0530] cupsdIsAuthorized: username=""
D [31/Dec/2010:14:38:46 +0530] cupsdSendHeader: 12 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [31/Dec/2010:14:38:46 +0530] cupsdCloseClient: 12
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdAcceptClient: 12 from localhost (Domain)
D [31/Dec/2010:14:38:46 +0530] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Active clients and dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdAuthorize: Authorized as pavan using PeerCred
D [31/Dec/2010:14:38:46 +0530] cupsdIsAuthorized: username="pavan"
I [31/Dec/2010:14:38:46 +0530] Installing config file "/etc/cups/cupsd.conf"...
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Dirty files
D [31/Dec/2010:14:38:46 +0530] cupsdCloseClient: 17
D [31/Dec/2010:14:38:46 +0530] cupsdCloseClient: 12
D [31/Dec/2010:14:38:46 +0530] cupsdDeregisterPrinter(p=0x21186968(HP-LaserJet-1020), removeit=1)
D [31/Dec/2010:14:38:46 +0530] cupsdNetIFUpdate: "lo" = localhost:631
D [31/Dec/2010:14:38:46 +0530] cupsdNetIFUpdate: "eth0" = 192.168.1.13:631
D [31/Dec/2010:14:38:46 +0530] cupsdNetIFUpdate: "eth1" = 192.168.1.9:631
D [31/Dec/2010:14:38:46 +0530] cupsdNetIFUpdate: "lo" = localhost:631
D [31/Dec/2010:14:38:46 +0530] cupsdNetIFUpdate: "eth0" = fe80::21b:38ff:fe96:2759%eth0:631
D [31/Dec/2010:14:38:46 +0530] cupsdNetIFUpdate: "eth1" = fe80::21a:73ff:fed6:1883%eth1:631
I [31/Dec/2010:14:38:46 +0530] Saving job cache file "/var/cache/cups/job.cache"...
I [31/Dec/2010:14:38:46 +0530] Saving subscriptions.conf...
D [31/Dec/2010:14:38:46 +0530] cupsdSetBusyState: Not busy
------

Thanks and regards,

Pavan

---

### Post by TeoBigusGeekus on 2010-12-31
> cupsdAuthorize: No authentication data provided
Have you checked if something has changed in your networks permissions?

---

### Post by pavanmatham on 2010-12-31
> **TeoBigusGeekus said:**
> Have you checked if something has changed in your networks permissions?
Hi,
Thanks for response. 
I don't know how to check the changes in network permissions? can you detail it.
Thanks and regards,

pavan

---

### Post by TeoBigusGeekus on 2011-01-01
I'm not a network printing expert unfortunately...
Someone else please?

---

