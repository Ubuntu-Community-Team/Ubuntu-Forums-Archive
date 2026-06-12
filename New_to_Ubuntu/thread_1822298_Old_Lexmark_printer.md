---
title: "Old Lexmark printer"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by peterson43 on 2011-08-10
I'm trying to get my old Lexmark Z611 to work with my new computer running Ubuntu 11.04. 

I followed the instructions from this [thread]("http://ubuntuforums.org/showthread.php?t=83456") from 2005, with a couple exceptions. First of all, the driver is no longer available for download from the Lexmark website. I finally found a site that I could download it from [here]("http://www.4shared.com/get/tpEtnV5Y/CJLZ600LE-CUPS-10-1TAR.html"). Secondly, I followed the instructions on the above mentioned thread all the way through the last line in step 2 which was 
```
sudo /etc/rc2.d/S19cupsys restart #The driver is now installed. Restart the cups daemon.
```
When I tried to do this I got the error message
```
sudo: /etc/rc2.d/S19cupsys: command not found
```
(I'm guessing that where some things are stored in Ubuntu has changed since 2005). Anyway, since this was supposed to restart the cups daemon I figured I could achieve the same effect by logging out and logging back in again. 

Since the driver was now supposedly installed, after logging back in again I plugged in my printer and now the computer seemed to recognize it. Hooray! However, when I tried printing I got an error message. A wizard pops up in Ubuntu to help me diagnose the printing problem, and it shows me the following error log 
```

D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:36 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:36 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:36 -0400] cupsdReadClient: 13 1.1 Get-Jobs 1
D [10/Aug/2011:11:54:36 -0400] Get-Jobs ipp://localhost/printers/
D [10/Aug/2011:11:54:36 -0400] [Job 6] Loading attributes...
D [10/Aug/2011:11:54:36 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:36 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:36 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:36 -0400] cupsdReadClient: 13 1.1 Get-Jobs 1
D [10/Aug/2011:11:54:36 -0400] Get-Jobs ipp://localhost/printers/
D [10/Aug/2011:11:54:36 -0400] [Job 1] Loading attributes...
D [10/Aug/2011:11:54:36 -0400] [Job 2] Loading attributes...
D [10/Aug/2011:11:54:36 -0400] [Job 3] Loading attributes...
D [10/Aug/2011:11:54:36 -0400] [Job 4] Loading attributes...
D [10/Aug/2011:11:54:36 -0400] [Job 5] Loading attributes...
D [10/Aug/2011:11:54:36 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:36 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:36 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:36 -0400] cupsdReadClient: 13 1.1 Create-Printer-Subscription 1
D [10/Aug/2011:11:54:36 -0400] Create-Printer-Subscription /
D [10/Aug/2011:11:54:36 -0400] cupsdCreateSubscription(con=0xb97528a0(13), uri="/")
D [10/Aug/2011:11:54:36 -0400] pullmethod="ippget"
D [10/Aug/2011:11:54:36 -0400] notify-lease-duration=86400
D [10/Aug/2011:11:54:36 -0400] notify-time-interval=0
D [10/Aug/2011:11:54:36 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [10/Aug/2011:11:54:36 -0400] Added subscription 10 for server
D [10/Aug/2011:11:54:36 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:36 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [10/Aug/2011:11:54:36 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:37 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:54:37 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:37 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:37 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:37 -0400] Get-Notifications /
D [10/Aug/2011:11:54:37 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:37 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:48 -0400] cupsdReadClient: 13 POST /jobs/ HTTP/1.1
D [10/Aug/2011:11:54:48 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:48 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:48 -0400] cupsdReadClient: 13 1.1 Cancel-Job 1
D [10/Aug/2011:11:54:48 -0400] Cancel-Job ipp://localhost/jobs/6
D [10/Aug/2011:11:54:48 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:48 -0400] cupsdMarkDirty(-----S)
I [10/Aug/2011:11:54:48 -0400] [Job 6] Job canceled by "jonpeterson"
D [10/Aug/2011:11:54:48 -0400] cupsdMarkDirty(----J-)
I [10/Aug/2011:11:54:48 -0400] [Job 6] Canceled by "jonpeterson".
D [10/Aug/2011:11:54:48 -0400] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/6) from localhost
D [10/Aug/2011:11:54:48 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 14 POST /printers/Z600-Series HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 14 1.1 Print-Job 1
D [10/Aug/2011:11:54:53 -0400] Print-Job ipp://localhost/printers/Z600-Series
D [10/Aug/2011:11:54:53 -0400] [Job ???] Auto-typing file...
I [10/Aug/2011:11:54:53 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(----J-)
D [10/Aug/2011:11:54:53 -0400] add_job: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:53 -0400] Adding default job-sheets values "none,none"...
I [10/Aug/2011:11:54:53 -0400] [Job 7] Adding start banner page "none".
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(----J-)
I [10/Aug/2011:11:54:53 -0400] [Job 7] Adding end banner page "none".
I [10/Aug/2011:11:54:53 -0400] [Job 7] File of type application/vnd.cups-banner queued by "jonpeterson".
D [10/Aug/2011:11:54:53 -0400] [Job 7] hold_until=0
I [10/Aug/2011:11:54:53 -0400] [Job 7] Queued on "Z600-Series" by "jonpeterson".
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(----J-)
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:53 -0400] [Job 7] job-sheets=none,none
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[0]="Z600-Series"
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[1]="7"
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[2]="jonpeterson"
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[3]="Test Page"
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[4]="1"
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[5]="job-uuid=urn:uuid:65eb9466-9e9a-398b-440a-8acf19a3b1f9 job-originating-host-name=localhost time-at-creation=1312991693 time-at-processing=1312991693 AP_D_InputSlot="
D [10/Aug/2011:11:54:53 -0400] [Job 7] argv[6]="/var/spool/cups/d00007-001"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[8]="HOME=/var/spool/cups/tmp"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[10]="SERVER_ADMIN=root@HP-home-laptop"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[11]="SOFTWARE=CUPS/1.4.6"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[13]="USER=root"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[16]="IPP_PORT=631"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[17]="CHARSET=utf-8"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[18]="LANG=en_US.UTF-8"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[19]="PPD=/etc/cups/ppd/Z600-Series.ppd"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[20]="RIP_MAX_CACHE=auto"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[22]="DEVICE_URI=usb://Lexmark/Z600%20Series"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[23]="PRINTER_INFO=Lexmark Z600 Series"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[24]="PRINTER_LOCATION=HP-home-laptop"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[25]="PRINTER=Z600-Series"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[26]="CUPS_FILETYPE=document"
D [10/Aug/2011:11:54:53 -0400] [Job 7] envp[27]="FINAL_CONTENT_TYPE=printer/Z600-Series"
I [10/Aug/2011:11:54:53 -0400] [Job 7] Started filter /usr/lib/cups/filter/bannertops (PID 2233)
I [10/Aug/2011:11:54:53 -0400] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 2234)
I [10/Aug/2011:11:54:53 -0400] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 2235)
I [10/Aug/2011:11:54:53 -0400] [Job 7] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 2236)
I [10/Aug/2011:11:54:53 -0400] [Job 7] Started filter /usr/lib/cups/filter/rastertoz600 (PID 2237)
I [10/Aug/2011:11:54:53 -0400] [Job 7] Started backend /usr/lib/cups/backend/usb (PID 2238)
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Z600-Series) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] [Job 7] pstopdf 5 args: 7 jonpeterson Test Page 1 job-uuid=urn:uuid:65eb9466-9e9a-398b-440a-8acf19a3b1f9 job-originating-host-name=localhost time-at-creation=1312991693 time-at-processing=1312991693 AP_D_InputSlot=
D [10/Aug/2011:11:54:53 -0400] [Job 7] PPD: /etc/cups/ppd/Z600-Series.ppd
D [10/Aug/2011:11:54:53 -0400] [Job 7] load_banner(filename="/var/spool/cups/d00007-001")
D [10/Aug/2011:11:54:53 -0400] [Job 7] Z600-Series: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
D [10/Aug/2011:11:54:53 -0400] PID 2237 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
D [10/Aug/2011:11:54:53 -0400] [Job 7] Page = 612x792; 18,36 to 594,787
D [10/Aug/2011:11:54:53 -0400] [Job 7] STATE: +connecting-to-device
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:53 -0400] [Job 7] Printer using device file "/dev/usblp0"...
D [10/Aug/2011:11:54:53 -0400] [Job 7] STATE: -connecting-to-device
D [10/Aug/2011:11:54:53 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:53 -0400] [Job 7] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0xb7803230)
D [10/Aug/2011:11:54:53 -0400] PID 2238 (/usr/lib/cups/backend/usb) exited with no errors.
D [10/Aug/2011:11:54:53 -0400] [Job 7] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [10/Aug/2011:11:54:53 -0400] [Job 7] PNG image: 192x128x8, color_type=2 (RGB)
D [10/Aug/2011:11:54:53 -0400] PID 2233 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [10/Aug/2011:11:54:53 -0400] [Job 7] Resolution:
D [10/Aug/2011:11:54:53 -0400] [Job 7] Page size: Letter
D [10/Aug/2011:11:54:53 -0400] [Job 7] Width: 612, height: 792, absolute margins: 18, 36, 594, 787
D [10/Aug/2011:11:54:53 -0400] [Job 7] Relative margins: 18, 36, 18, 5
D [10/Aug/2011:11:54:53 -0400] [Job 7] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [10/Aug/2011:11:54:53 -0400] [Job 7] PostScript to be injected:
D [10/Aug/2011:11:54:53 -0400] [Job 7] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:53 -0400] Get-Notifications /
D [10/Aug/2011:11:54:53 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:53 -0400] Get-Notifications /
D [10/Aug/2011:11:54:53 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 20 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Printer-Attributes ipp://localhost/printers/Z600-Series
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Z600-Series) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:53 -0400] Get-Notifications /
D [10/Aug/2011:11:54:53 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Printer-Attributes ipp://localhost/printers/Z600-Series
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Z600-Series) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Printer-Attributes ipp://localhost/printers/Z600-Series
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Z600-Series) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [10/Aug/2011:11:54:53 -0400] cupsdCloseClient: 18
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [10/Aug/2011:11:54:53 -0400] cupsdCloseClient: 18
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [10/Aug/2011:11:54:53 -0400] cupsdCloseClient: 18
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:54:53 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [10/Aug/2011:11:54:53 -0400] cupsdCloseClient: 18
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [10/Aug/2011:11:54:53 -0400] cupsdCloseClient: 19
D [10/Aug/2011:11:54:53 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [10/Aug/2011:11:54:53 -0400] CUPS-Get-Printers
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [10/Aug/2011:11:54:53 -0400] CUPS-Get-Classes
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [10/Aug/2011:11:54:53 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:53 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [10/Aug/2011:11:54:53 -0400] CUPS-Get-Default
D [10/Aug/2011:11:54:53 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [10/Aug/2011:11:54:53 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [10/Aug/2011:11:54:54 -0400] PID 2234 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [10/Aug/2011:11:54:54 -0400] PID 2235 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [10/Aug/2011:11:54:54 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [10/Aug/2011:11:54:54 -0400] cupsdNetIFUpdate: "eth1" = 192.168.0.5:631
D [10/Aug/2011:11:54:54 -0400] cupsdNetIFUpdate: "lo" = localhost:631
D [10/Aug/2011:11:54:54 -0400] cupsdNetIFUpdate: "eth1" = [v1.fe80::ae81:12ff:fe93:58c+eth1]:631
D [10/Aug/2011:11:54:54 -0400] PID 2236 (/usr/lib/cups/filter/pdftoraster-poppler) did not catch or ignore signal 13.
D [10/Aug/2011:11:54:54 -0400] cupsdMarkDirty(-----S)
E [10/Aug/2011:11:54:54 -0400] [Job 7] Job stopped due to filter errors; please consult the error_log file for details.
D [10/Aug/2011:11:54:54 -0400] cupsdMarkDirty(----J-)
D [10/Aug/2011:11:54:54 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:54:54 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:54 -0400] Get-Notifications /
D [10/Aug/2011:11:54:54 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:54 -0400] Get-Notifications /
D [10/Aug/2011:11:54:54 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1
D [10/Aug/2011:11:54:54 -0400] Get-Printer-Attributes ipp://localhost/printers/Z600-Series
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Z600-Series) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdAcceptClient: 21 from localhost (Domain)
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 21 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 21 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:54:54 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAcceptClient: 22 from localhost (Domain)
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [10/Aug/2011:11:54:54 -0400] Get-Printer-Attributes ipp://HP-home-laptop:631/printers/Z600-Series
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://HP-home-laptop:631/printers/Z600-Series) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 22 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 22 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:54:54 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 21 WAITING Closing on EOF
D [10/Aug/2011:11:54:54 -0400] cupsdCloseClient: 21
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [10/Aug/2011:11:54:54 -0400] Get-Notifications /
D [10/Aug/2011:11:54:54 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [10/Aug/2011:11:54:54 -0400] cupsdCloseClient: 16
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [10/Aug/2011:11:54:54 -0400] cupsdCloseClient: 19
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [10/Aug/2011:11:54:54 -0400] CUPS-Get-Printers
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [10/Aug/2011:11:54:54 -0400] CUPS-Get-Classes
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:54:54 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:54:54 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [10/Aug/2011:11:54:54 -0400] CUPS-Get-Default
D [10/Aug/2011:11:54:54 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [10/Aug/2011:11:54:54 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:54:55 -0400] [Job 7] Unloading...
D [10/Aug/2011:11:55:00 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:55:00 -0400] cupsdAuthorize: No authentication data provided.
I [10/Aug/2011:11:55:00 -0400] Generating printcap /var/run/cups/printcap...
I [10/Aug/2011:11:55:00 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [10/Aug/2011:11:55:00 -0400] Saving subscriptions.conf...
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Active clients
D [10/Aug/2011:11:55:00 -0400] cupsdReadClient: 13 1.1 Get-Job-Attributes 1
D [10/Aug/2011:11:55:00 -0400] Get-Job-Attributes ipp://localhost/jobs/7
D [10/Aug/2011:11:55:00 -0400] [Job 7] Loading attributes...
D [10/Aug/2011:11:55:00 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Not busy
D [10/Aug/2011:11:55:00 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Active clients
D [10/Aug/2011:11:55:00 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:55:00 -0400] cupsdReadClient: 13 1.1 Cancel-Subscription 1
D [10/Aug/2011:11:55:00 -0400] Cancel-Subscription /
D [10/Aug/2011:11:55:00 -0400] cupsdIsAuthorized: requesting-user-name="jonpeterson"
D [10/Aug/2011:11:55:00 -0400] cupsdMarkDirty(-----S)
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:55:00 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:55:00 -0400] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:55:00 -0400] cupsdAuthorize: No authentication data provided.
D [10/Aug/2011:11:55:00 -0400] cupsdIsAuthorized: username=""
D [10/Aug/2011:11:55:00 -0400] cupsdSendHeader: 13 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [10/Aug/2011:11:55:00 -0400] cupsdCloseClient: 13
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:55:00 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [10/Aug/2011:11:55:00 -0400] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Active clients and dirty files
D [10/Aug/2011:11:55:00 -0400] cupsdAuthorize: Authorized as jonpeterson using PeerCred
D [10/Aug/2011:11:55:00 -0400] cupsdIsAuthorized: username="jonpeterson"
I [10/Aug/2011:11:55:00 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Dirty files
D [10/Aug/2011:11:55:00 -0400] cupsdCloseClient: 14
D [10/Aug/2011:11:55:00 -0400] cupsdCloseClient: 20
D [10/Aug/2011:11:55:00 -0400] cupsdCloseClient: 18
D [10/Aug/2011:11:55:00 -0400] cupsdCloseClient: 22
D [10/Aug/2011:11:55:00 -0400] cupsdCloseClient: 13
D [10/Aug/2011:11:55:00 -0400] cupsdDeregisterPrinter(p=0xb971df80(Z600-Series), removeit=1)
I [10/Aug/2011:11:55:00 -0400] Saving subscriptions.conf...
D [10/Aug/2011:11:55:00 -0400] cupsdSetBusyState: Not busy
E [10/Aug/2011:11:55:00 -0400] Failed to update TXT record for Lexmark Z600 Series @ HP-home-laptop: -2

```
Can anyone help me make any sense of this, or help me get my printer working in some other way?

---

