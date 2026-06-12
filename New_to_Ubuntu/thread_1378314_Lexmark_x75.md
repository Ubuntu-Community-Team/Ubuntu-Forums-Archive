---
title: "Lexmark x75"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Xoanan on 2010-01-11
Hi all

I am having some difficulty installing the proper driver for my LexMark printer. I followed the installation instructions as found on [http://ubuntuforums.org/showthread.php?t=340735]("http://ubuntuforums.org/showthread.php?t=340735"), but I ran into the following error 
```
Error: Unable to locate the CUPS model directory (where the PPD files are stored).

```

Any thoughts?

---

### Post by Xoanan on 2010-01-11
Here&#347; some more info

```
ls: cannot access /usr/share/cups/model/: No such file or directory

```

---

### Post by Xoanan on 2010-01-11
I created the directory manually but now I have another issue.

Here&#347; the error log from the troubleshooter

```
1/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Dirty files
D [11/Jan/2010:10:35:50 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Active clients and dirty files
D [11/Jan/2010:10:35:50 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:35:50 -0600] cupsdReadClient: 12 1.1 Get-Jobs 1
D [11/Jan/2010:10:35:50 -0600] Get-Jobs ipp://localhost/printers/
D [11/Jan/2010:10:35:50 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Dirty files
D [11/Jan/2010:10:35:50 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Active clients and dirty files
D [11/Jan/2010:10:35:50 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:35:50 -0600] cupsdReadClient: 12 1.1 Get-Jobs 1
D [11/Jan/2010:10:35:50 -0600] Get-Jobs ipp://localhost/printers/
D [11/Jan/2010:10:35:50 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [11/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Dirty files
D [11/Jan/2010:10:35:50 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Active clients and dirty files
D [11/Jan/2010:10:35:50 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:35:50 -0600] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [11/Jan/2010:10:35:50 -0600] Create-Printer-Subscription /
D [11/Jan/2010:10:35:50 -0600] cupsdCreateSubscription(con=0x117d430(12), uri="/")
D [11/Jan/2010:10:35:50 -0600] pullmethod="ippget"
D [11/Jan/2010:10:35:50 -0600] notify-lease-duration=86400
D [11/Jan/2010:10:35:50 -0600] notify-time-interval=0
D [11/Jan/2010:10:35:50 -0600] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [11/Jan/2010:10:35:50 -0600] Added subscription 43 for server
D [11/Jan/2010:10:35:50 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:35:50 -0600] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [11/Jan/2010:10:35:50 -0600] cupsdSetBusyState: Dirty files
D [11/Jan/2010:10:35:51 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:35:51 -0600] cupsdSetBusyState: Active clients and dirty files
D [11/Jan/2010:10:35:51 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:35:51 -0600] cupsdReadClient: 12 1.1 Get-Notifications 1
D [11/Jan/2010:10:35:51 -0600] Get-Notifications /
D [11/Jan/2010:10:35:51 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:35:51 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:35:51 -0600] cupsdSetBusyState: Dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAcceptClient: 14 from localhost (Domain)
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 14 POST /printers/Lexmark-All-In-One HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 14 1.1 Print-Job 1
D [11/Jan/2010:10:36:03 -0600] Print-Job ipp://localhost/printers/Lexmark-All-In-One
D [11/Jan/2010:10:36:03 -0600] [Job ???] Auto-typing file...
I [11/Jan/2010:10:36:03 -0600] [Job ???] Request file type is application/vnd.cups-banner.
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(----J-)
D [11/Jan/2010:10:36:03 -0600] add_job: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:03 -0600] Adding default job-sheets values "none,none"...
I [11/Jan/2010:10:36:03 -0600] [Job 42] Adding start banner page "none".
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(----J-)
I [11/Jan/2010:10:36:03 -0600] [Job 42] Adding end banner page "none".
I [11/Jan/2010:10:36:03 -0600] [Job 42] File of type application/vnd.cups-banner queued by "xoanan".
D [11/Jan/2010:10:36:03 -0600] [Job 42] hold_until=0
I [11/Jan/2010:10:36:03 -0600] [Job 42] Queued on "Lexmark-All-In-One" by "xoanan".
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(----J-)
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:03 -0600] [Job 42] job-sheets=none,none
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[0]="Lexmark-All-In-One"
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[1]="42"
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[2]="xoanan"
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[3]="Test Page"
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[4]="1"
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[5]="job-uuid=urn:uuid:a28e8eea-a8b9-3bf9-6d11-8e0ec5c6c09a job-originating-host-name=localhost"
D [11/Jan/2010:10:36:03 -0600] [Job 42] argv[6]="/var/spool/cups/d00042-001"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[8]="HOME=/var/spool/cups/tmp"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[10]="SERVER_ADMIN=root@ubuntu"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[11]="SOFTWARE=CUPS/1.4.1"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[13]="TZ=America/Chicago"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[14]="USER=root"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[17]="IPP_PORT=631"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[18]="CHARSET=utf-8"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[19]="LANG=en_US.UTF-8"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[20]="PPD=/etc/cups/ppd/Lexmark-All-In-One.ppd"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[21]="RIP_MAX_CACHE=256449k"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[23]="DEVICE_URI=usb://Lexmark/All%20In%20One"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[24]="PRINTER_INFO=Lexmark Lexmark All In One"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[25]="PRINTER_LOCATION=ubuntu"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[26]="PRINTER=Lexmark-All-In-One"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[27]="CUPS_FILETYPE=document"
D [11/Jan/2010:10:36:03 -0600] [Job 42] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark-All-In-One"
I [11/Jan/2010:10:36:03 -0600] [Job 42] Started filter /usr/lib/cups/filter/bannertops (PID 3288)
I [11/Jan/2010:10:36:03 -0600] [Job 42] Started filter /usr/lib/cups/filter/pstopdf (PID 3289)
I [11/Jan/2010:10:36:03 -0600] [Job 42] Started filter /usr/lib/cups/filter/pdftopdf (PID 3290)
I [11/Jan/2010:10:36:03 -0600] [Job 42] Started filter /usr/lib/cups/filter/pdftoraster (PID 3291)
I [11/Jan/2010:10:36:03 -0600] [Job 42] Started filter /usr/lib/cups/filter/rastertolxx74 (PID 3292)
I [11/Jan/2010:10:36:03 -0600] [Job 42] Started backend /usr/lib/cups/backend/usb (PID 3293)
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Lexmark-All-In-One) from localhost
D [11/Jan/2010:10:36:03 -0600] [Job 42] STATE: +connecting-to-device
D [11/Jan/2010:10:36:03 -0600] [Job 42] Printer using device file "/dev/usblp0"...
D [11/Jan/2010:10:36:03 -0600] [Job 42] STATE: -connecting-to-device
D [11/Jan/2010:10:36:03 -0600] [Job 42] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0xc75b30)
D [11/Jan/2010:10:36:03 -0600] [Job 42] pstopdf 5 args: 42 xoanan Test Page 1 job-uuid=urn:uuid:a28e8eea-a8b9-3bf9-6d11-8e0ec5c6c09a job-originating-host-name=localhost
D [11/Jan/2010:10:36:03 -0600] [Job 42] PPD: /etc/cups/ppd/Lexmark-All-In-One.ppd
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] [Job 42] load_banner(filename="/var/spool/cups/d00042-001")
D [11/Jan/2010:10:36:03 -0600] [Job 42] rastertolxx74.c:1725: Found options on the command line.
E [11/Jan/2010:10:36:03 -0600] [Job 42] rastertolxx74.c:1687: Unknown option job-uuid=urn:uuid:a28e8eea-a8b9-3bf9-6d11-8e0ec5c6c09a.
D [11/Jan/2010:10:36:03 -0600] [Job 42] Set job-printer-state-message to "rastertolxx74.c:1687: Unknown option job-uuid=urn:uuid:a28e8eea-a8b9-3bf9-6d11-8e0ec5c6c09a.", current level=ERROR
E [11/Jan/2010:10:36:03 -0600] [Job 42] rastertolxx74.c:1687: Unknown option job-originating-host-name=localhost.
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:03 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:03 -0600] [Job 42] Page = 612x792; 0,0 to 610,787
D [11/Jan/2010:10:36:03 -0600] [Job 42] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [11/Jan/2010:10:36:03 -0600] [Job 42] PNG image: 192x128x8, color_type=2 (RGB)
D [11/Jan/2010:10:36:03 -0600] PID 3288 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [11/Jan/2010:10:36:03 -0600] [Job 42] Resolution: 600
D [11/Jan/2010:10:36:03 -0600] [Job 42] Page size: Letter
D [11/Jan/2010:10:36:03 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 16 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:03 -0600] Get-Notifications /
D [11/Jan/2010:10:36:03 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAcceptClient: 17 from localhost (Domain)
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:03 -0600] Get-Notifications /
D [11/Jan/2010:10:36:03 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 WAITING Closing on EOF
D [11/Jan/2010:10:36:03 -0600] cupsdCloseClient: 17
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdAcceptClient: 17 from localhost (Domain)
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [11/Jan/2010:10:36:03 -0600] Get-Job-Attributes ipp://localhost/jobs/42
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/42) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 12 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:03 -0600] Get-Notifications /
D [11/Jan/2010:10:36:03 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Printers
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Classes
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Default
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jan/2010:10:36:03 -0600] cupsdCloseClient: 16
D [11/Jan/2010:10:36:03 -0600] [Job 42] Width: 612.00, height: 792.00, absolute margins: 0.00, 0.00, 610.00, 787.00
D [11/Jan/2010:10:36:03 -0600] [Job 42] Relative margins: 0.00, 0.00, 2.00, 5.00
D [11/Jan/2010:10:36:03 -0600] [Job 42] PPD options: -r600 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00
D [11/Jan/2010:10:36:03 -0600] [Job 42] PostScript to be injected:
D [11/Jan/2010:10:36:03 -0600] [Job 42] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 - -
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Printers
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Classes
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Default
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [11/Jan/2010:10:36:03 -0600] CUPS-Get-Printers
D [11/Jan/2010:10:36:03 -0600] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:03 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:03 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:04 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [11/Jan/2010:10:36:04 -0600] CUPS-Get-Classes
D [11/Jan/2010:10:36:04 -0600] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2010:10:36:04 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:04 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:04 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:04 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:04 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [11/Jan/2010:10:36:04 -0600] CUPS-Get-Default
D [11/Jan/2010:10:36:04 -0600] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2010:10:36:04 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:04 -0600] [Job 42] GPL Ghostscript 8.70: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [11/Jan/2010:10:36:05 -0600] PID 3289 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [11/Jan/2010:10:36:05 -0600] PID 3290 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [11/Jan/2010:10:36:05 -0600] [Job 42] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=6 -dcupsRowCount=192 -scupsPageSizeName=Letter -c -f -_
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[8]="HOME=/var/spool/cups/tmp"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[10]="SERVER_ADMIN=root@ubuntu"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[11]="SOFTWARE=CUPS/1.4.1"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[12]="TZ=America/Chicago"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[13]="USER=root"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[16]="IPP_PORT=631"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[17]="CHARSET=utf-8"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[18]="LANG=en_US.UTF-8"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[19]="PPD=/etc/cups/ppd/Lexmark-All-In-One.ppd"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[20]="RIP_MAX_CACHE=256449k"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[22]="DEVICE_URI=usb://Lexmark/All%20In%20One"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[23]="PRINTER_INFO=Lexmark Lexmark All In One"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[24]="PRINTER_LOCATION=ubuntu"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[25]="PRINTER=Lexmark-All-In-One"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[26]="CUPS_FILETYPE=document"
D [11/Jan/2010:10:36:05 -0600] [Job 42] envp[27]="FINAL_CONTENT_TYPE=printer/Lexmark-All-In-One"
D [11/Jan/2010:10:36:05 -0600] PID 3291 (/usr/lib/cups/filter/pdftoraster) exited with no errors.
D [11/Jan/2010:10:36:05 -0600] [Job 42] num_components = 1, depth = 1
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsColorSpace = 3, cupsColorOrder = 0
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsBitsPerPixel = 1, cupsBitsPerColor = 1
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_gray = 1, dither_grays = 2
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_color = 0, dither_colors = 0
D [11/Jan/2010:10:36:05 -0600] [Job 42] Updating PageSize to [612 792]...
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting initial media size, [612 792] = 5100x6600 pixels...
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting cupsBitsPerColor to 1...
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting cupsColorOrder to 0...
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting cupsColorSpace to 6...
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting cupsRowCount to 192...
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting cupsPageSizeName to "Letter"...
D [11/Jan/2010:10:36:05 -0600] [Job 42] num_components = 4, depth = 4
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsColorSpace = 6, cupsColorOrder = 0
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsBitsPerPixel = 4, cupsBitsPerColor = 1
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_gray = 1, dither_grays = 2
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_color = 1, dither_colors = 2
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting initial media size, [612 792] = 5100x6600 pixels...
I [11/Jan/2010:10:36:05 -0600] [Job 42] Processing page 1...
D [11/Jan/2010:10:36:05 -0600] [Job 42] num_components = 4, depth = 4
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsColorSpace = 6, cupsColorOrder = 0
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsBitsPerPixel = 4, cupsBitsPerColor = 1
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_gray = 1, dither_grays = 2
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_color = 1, dither_colors = 2
D [11/Jan/2010:10:36:05 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:05 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:05 -0600] [Job 42] Setting LeadingEdge to 0...
D [11/Jan/2010:10:36:05 -0600] [Job 42] num_components = 4, depth = 4
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsColorSpace = 6, cupsColorOrder = 0
D [11/Jan/2010:10:36:05 -0600] [Job 42] cupsBitsPerPixel = 4, cupsBitsPerColor = 1
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_gray = 1, dither_grays = 2
D [11/Jan/2010:10:36:05 -0600] [Job 42] max_color = 1, dither_colors = 2
D [11/Jan/2010:10:36:05 -0600] [Job 42] Updating PageSize to [612 792]...
D [11/Jan/2010:10:36:05 -0600] [Job 42] size = Letter
D [11/Jan/2010:10:36:05 -0600] [Job 42] margins[] = [ 0.000000 0.000000 0.027778 0.069444 ]
D [11/Jan/2010:10:36:06 -0600] [Job 42] Setting LeadingEdge to 0...
D [11/Jan/2010:10:36:06 -0600] [Job 42] num_components = 4, depth = 4
D [11/Jan/2010:10:36:06 -0600] [Job 42] cupsColorSpace = 6, cupsColorOrder = 0
D [11/Jan/2010:10:36:06 -0600] [Job 42] cupsBitsPerPixel = 4, cupsBitsPerColor = 1
D [11/Jan/2010:10:36:06 -0600] [Job 42] max_gray = 1, dither_grays = 2
D [11/Jan/2010:10:36:06 -0600] [Job 42] max_color = 1, dither_colors = 2
D [11/Jan/2010:10:36:06 -0600] [Job 42] Setting LeadingEdge to 0...
D [11/Jan/2010:10:36:06 -0600] [Job 42] num_components = 4, depth = 4
D [11/Jan/2010:10:36:06 -0600] [Job 42] cupsColorSpace = 6, cupsColorOrder = 0
D [11/Jan/2010:10:36:06 -0600] [Job 42] cupsBitsPerPixel = 4, cupsBitsPerColor = 1
D [11/Jan/2010:10:36:06 -0600] [Job 42] max_gray = 1, dither_grays = 2
D [11/Jan/2010:10:36:06 -0600] [Job 42] max_color = 1, dither_colors = 2
D [11/Jan/2010:10:36:06 -0600] [Job 42] Updating PageSize to [612 792]...
D [11/Jan/2010:10:36:06 -0600] [Job 42] size = Letter
D [11/Jan/2010:10:36:06 -0600] [Job 42] margins[] = [ 0.000000 0.000000 0.027778 0.069444 ]
D [11/Jan/2010:10:36:06 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:06 -0600] Get-Notifications /
D [11/Jan/2010:10:36:06 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jan/2010:10:36:06 -0600] cupsdCloseClient: 16
D [11/Jan/2010:10:36:06 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:06 -0600] Get-Notifications /
D [11/Jan/2010:10:36:06 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jan/2010:10:36:06 -0600] cupsdCloseClient: 16
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 12 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:06 -0600] Get-Notifications /
D [11/Jan/2010:10:36:06 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [11/Jan/2010:10:36:06 -0600] CUPS-Get-Printers
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [11/Jan/2010:10:36:06 -0600] CUPS-Get-Classes
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [11/Jan/2010:10:36:06 -0600] CUPS-Get-Default
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] [Job 42] cups_print_chunked - flip = 0, height = 6558
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1542: File (stdin) is not a regular file, its size is unknown (stat reports 0 bytes).
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1399: Read header from file positions 4294967295 to 4294967295 (0 bytes).
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1400: HWResolution starts at offset 276.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1401: MediaClass:      .
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1402: MediaColor:      .
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1403: MediaType:       .
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1404: OutputType:      .
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1405: AdvanceDistance: 0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1406: AdvanceMedia:    CUPS_ADVANCE_NONE.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1407: Collate:         False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1408: CutMedia:        CUPS_CUT_NONE.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1409: Duplex:          False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1410: HWResolution[0]: 600.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1411: HWResolution[1]: 600.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1412: ImagingBoundingBox[0]: 0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1413: ImagingBoundingBox[1]: 0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1414: ImagingBoundingBox[2]: 610.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1415: ImagingBoundingBox[3]: 787.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1416: InsertSheet      False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1417: Jog:             CUPS_JOG_NONE.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1418: LeadingEdge:     CUPS_EDGE_TOP.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1419: Margins[0]       0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1420: Margins[1]       0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1421: ManualFeed       False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1422: MediaPosition:   0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1423: MediaWeight:     0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1424: MirrorPrint:     False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1425: NegativePrint:   False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1426: NumCopies:       1.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1427: Orientation:     CUPS_ORIENT_0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1428: OutputFaceUp     False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1429: PageSize[0]      612.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1430: PageSize[1]      792.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1431: Separations      False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1432: TraySwitch       False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1433: Tumble           False.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1435: cupsWidth        5083.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1436: cupsHeight       6558.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1437: cupsMediaType    0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1438: cupsBitsPerColor 1.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1439: cupsBitsPerPixel 4.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1440: cupsBytesPerLine 2542.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1442: cupsColorOrder:  CUPS_ORDER_CHUNKED.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1443: cupsColorSpace:  CUPS_CSPACE_CMYK.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1445: cupsCompression  0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1446: cupsRowCount     192.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1447: cupsRowFeed      0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1448: cupsRowStep      0.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1450: Expect next page at offset 16670435.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1454: Resolution is 600.0000008.2 x  600.00.
D [11/Jan/2010:10:36:06 -0600] [Job 42] rastertolxx74.c:1572: Starting page at byte -1.
D [11/Jan/2010:10:36:06 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] [Job 42] STATE: -media-empty-warning
D [11/Jan/2010:10:36:06 -0600] [Job 42] STATE: -offline-report
I [11/Jan/2010:10:36:06 -0600] [Job 42] Printer is now online.
D [11/Jan/2010:10:36:06 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:06 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:06 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:06 -0600] Get-Notifications /
D [11/Jan/2010:10:36:06 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jan/2010:10:36:06 -0600] cupsdCloseClient: 16
D [11/Jan/2010:10:36:06 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:06 -0600] Get-Notifications /
D [11/Jan/2010:10:36:06 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jan/2010:10:36:06 -0600] cupsdCloseClient: 16
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 12 1.1 Get-Notifications 1
D [11/Jan/2010:10:36:06 -0600] Get-Notifications /
D [11/Jan/2010:10:36:06 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [11/Jan/2010:10:36:06 -0600] CUPS-Get-Printers
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [11/Jan/2010:10:36:06 -0600] CUPS-Get-Classes
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:06 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:06 -0600] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [11/Jan/2010:10:36:06 -0600] CUPS-Get-Default
D [11/Jan/2010:10:36:06 -0600] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [11/Jan/2010:10:36:06 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:06 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:06 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:07 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:07 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:07 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:07 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:07 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:07 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:10 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:10 -0600] [Job 42] Received 12 bytes of back-channel data!
D [11/Jan/2010:10:36:10 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:10 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:10 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Received 12 bytes of back-channel data!
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
I [11/Jan/2010:10:36:15 -0600] Generating printcap /var/run/cups/printcap...
I [11/Jan/2010:10:36:15 -0600] Saving job cache file "/var/cache/cups/job.cache"...
I [11/Jan/2010:10:36:15 -0600] Saving subscriptions.conf...
D [11/Jan/2010:10:36:15 -0600] cupsdSetBusyState: Printing jobs
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:15 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:16 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:16 -0600] [Job 42] Read 8192 bytes of print data...
D [11/Jan/2010:10:36:16 -0600] [Job 42] Wrote 8192 bytes of print data...
D [11/Jan/2010:10:36:17 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:36:17 -0600] cupsdSetBusyState: Active clients and printing jobs
D [11/Jan/2010:10:36:17 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:17 -0600] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [11/Jan/2010:10:36:17 -0600] Get-Job-Attributes ipp://localhost/jobs/42
D [11/Jan/2010:10:36:17 -0600] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/42) from localhost
D [11/Jan/2010:10:36:17 -0600] cupsdSetBusyState: Printing jobs
D [11/Jan/2010:10:36:17 -0600] cupsdReadClient: 12 POST / HTTP/1.1
D [11/Jan/2010:10:36:17 -0600] cupsdSetBusyState: Active clients and printing jobs
D [11/Jan/2010:10:36:17 -0600] cupsdAuthorize: No authentication data provided.
D [11/Jan/2010:10:36:17 -0600] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [11/Jan/2010:10:36:17 -0600] Cancel-Subscription /
D [11/Jan/2010:10:36:17 -0600] cupsdIsAuthorized: requesting-user-name="xoanan"
D [11/Jan/2010:10:36:17 -0600] cupsdMarkDirty(-----S)
D [11/Jan/2010:10:36:17 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:17 -0600] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [11/Jan/2010:10:36:17 -0600] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jan/2010:10:36:17 -0600] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jan/2010:10:36:17 -0600] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1
D [11/Jan/2010:10:36:17 -0600] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jan/2010:10:36:17 -0600] cupsdAuthorize: No authentication data provided.
```

---

### Post by Xoanan on 2010-07-12
rastertolxx74.c:1687: Unknown option job-uuid

---

