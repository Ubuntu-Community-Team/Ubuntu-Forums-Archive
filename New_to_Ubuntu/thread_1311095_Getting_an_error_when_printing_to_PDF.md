---
title: "Getting an error when printing to PDF"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Excedio on 2009-11-02
Hey Guys...just made the upgrade to 9.10. I installed cups-pdf the same way that I did in 9.04, but now I'm getting an error message when doing a test print.[IMG]http://i71.photobucket.com/albums/i136/Excedio/Untitled-4.png[/IMG]


I ran the diagnostic and got this read out...

[quote=Error log messages]
D [02/Nov/2009:08:41:25 -0500] cupsdMarkDirty(-----S)
D [02/Nov/2009:08:41:25 -0500] [Job 7] job-sheets=none,none
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[0]="PDF"
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[1]="7"
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[2]="excedio"
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[3]="Test Page"
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[4]="1"
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[5]="job-uuid=urn:uuid:eadcf5af-9021-35c8-4a5e-ee20a4a4463a job-originating-host-name=localhost"
D [02/Nov/2009:08:41:25 -0500] [Job 7] argv[6]="/var/spool/cups/d00007-001"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[8]="HOME=/var/spool/cups/tmp"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[10]="SERVER_ADMIN=root@excedio-desktop"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[11]="SOFTWARE=CUPS/1.4.1"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[13]="TZ=US/Eastern"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[14]="USER=root"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[17]="IPP_PORT=631"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[18]="CHARSET=utf-8"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[19]="LANG=en_US.UTF-8"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[20]="PPD=/etc/cups/ppd/PDF.ppd"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[21]="RIP_MAX_CACHE=950093k"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[23]="DEVICE_URI=cups-pdf:/"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[24]="PRINTER_INFO=PDF"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[25]="PRINTER_LOCATION="
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[26]="PRINTER=PDF"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[27]="CUPS_FILETYPE=document"
D [02/Nov/2009:08:41:25 -0500] [Job 7] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
I [02/Nov/2009:08:41:25 -0500] [Job 7] Started filter /usr/lib/cups/filter/bannertops (PID 8910)
I [02/Nov/2009:08:41:25 -0500] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 8911)
I [02/Nov/2009:08:41:25 -0500] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 8912)
E [02/Nov/2009:08:41:25 -0500] Unable to execute /usr/lib/cups/backend/cups-pdf: insecure file permissions (0106700)
D [02/Nov/2009:08:41:25 -0500] cupsdMarkDirty(P-----)
D [02/Nov/2009:08:41:25 -0500] cupsdMarkDirty(-----S)
D [02/Nov/2009:08:41:25 -0500] cupsdMarkDirty(-----S)
**E [02/Nov/2009:08:41:25 -0500] [Job 7] Stopping job because the sheduler could not execute the backend.**
D [02/Nov/2009:08:41:25 -0500] cupsdMarkDirty(----J-)
D [02/Nov/2009:08:41:25 -0500] cupsdMarkDirty(-----S)
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/PDF) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] PID 8910 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.
D [02/Nov/2009:08:41:25 -0500] PID 8912 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.
D [02/Nov/2009:08:41:25 -0500] PID 8911 (/usr/lib/cups/filter/pstopdf) stopped with status 1!
D [02/Nov/2009:08:41:25 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 1.1 Get-Jobs 1
D [02/Nov/2009:08:41:25 -0500] Get-Jobs ipp://localhost/printers/
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [02/Nov/2009:08:41:25 -0500] cupsdCloseClient: 14
D [02/Nov/2009:08:41:25 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1
D [02/Nov/2009:08:41:25 -0500] Get-Notifications /
D [02/Nov/2009:08:41:25 -0500] cupsdIsAuthorized: requesting-user-name="excedio"
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 1.1 Get-Job-Attributes 1
D [02/Nov/2009:08:41:25 -0500] Get-Job-Attributes ipp://localhost/jobs/7
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2009:08:41:25 -0500] Get-Printer-Attributes ipp://excedio-desktop:0/printers/PDF
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://excedio-desktop:0/printers/PDF) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2009:08:41:25 -0500] Get-Job-Attributes ipp://localhost/jobs/7
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdAcceptClient: 16 from localhost (Domain)
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 16 1.1 Get-Notifications 1
D [02/Nov/2009:08:41:25 -0500] Get-Notifications /
D [02/Nov/2009:08:41:25 -0500] cupsdIsAuthorized: requesting-user-name="excedio"
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdAcceptClient: 17 from localhost (Domain)
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [02/Nov/2009:08:41:25 -0500] Get-Printer-Attributes ipp://excedio-desktop:0/printers/PDF
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://excedio-desktop:0/printers/PDF) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:25 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [02/Nov/2009:08:41:25 -0500] Get-Job-Attributes ipp://localhost/jobs/7
D [02/Nov/2009:08:41:25 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [02/Nov/2009:08:41:25 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Nov/2009:08:41:25 -0500] cupsdCloseClient: 12
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [02/Nov/2009:08:41:25 -0500] cupsdCloseClient: 15
D [02/Nov/2009:08:41:25 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [02/Nov/2009:08:41:25 -0500] cupsdCloseClient: 14
D [02/Nov/2009:08:41:26 -0500] [Job 7] Unloading...
D [02/Nov/2009:08:41:39 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [02/Nov/2009:08:41:39 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:41:39 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:39 -0500] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [02/Nov/2009:08:41:39 -0500] Get-Job-Attributes ipp://localhost/jobs/7
D [02/Nov/2009:08:41:39 -0500] [Job 7] Loading attributes...
D [02/Nov/2009:08:41:39 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/7) from localhost
D [02/Nov/2009:08:41:39 -0500] cupsdSetBusyState: Dirty files
I [02/Nov/2009:08:41:56 -0500] Saving printers.conf...
I [02/Nov/2009:08:41:56 -0500] Saving job cache file "/var/cache/cups/job.cache"...
I [02/Nov/2009:08:41:56 -0500] Saving subscriptions.conf...
D [02/Nov/2009:08:41:56 -0500] cupsdSetBusyState: Not busy
D [02/Nov/2009:08:41:59 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [02/Nov/2009:08:41:59 -0500] cupsdSetBusyState: Active clients
**D [02/Nov/2009:08:41:59 -0500] cupsdAuthorize: No authentication data provided.**
D [02/Nov/2009:08:41:59 -0500] cupsdReadClient: 16 1.1 Cancel-Subscription 1
D [02/Nov/2009:08:41:59 -0500] Cancel-Subscription /
D [02/Nov/2009:08:41:59 -0500] cupsdIsAuthorized: requesting-user-name="excedio"
D [02/Nov/2009:08:41:59 -0500] cupsdMarkDirty(-----S)
D [02/Nov/2009:08:41:59 -0500] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2009:08:41:59 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [02/Nov/2009:08:41:59 -0500] cupsdSetBusyState: Dirty files
D [02/Nov/2009:08:42:01 -0500] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Nov/2009:08:42:01 -0500] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [02/Nov/2009:08:42:01 -0500] cupsdSetBusyState: Active clients and dirty files
**D [02/Nov/2009:08:42:01 -0500] cupsdAuthorize: No authentication data provided.**
[\QUOTE]

---

### Post by blazemore on 2009-11-02
Try running the command
```
sudo /etc/init.d/cups restart
```

---

### Post by richbuda on 2009-11-03
I have exactly the same issue.  Restarting doesn't help.  Any ideas?  My cup folder is owned by root.

---

### Post by blazemore on 2009-11-03
my only other advice would be
```
sudo aptitude purge cups-pdf
sudo aptitude install cups-pdf
```

---

### Post by astriemer on 2009-11-12
> **blazemore said:**
> my only other advice would be
```
sudo aptitude purge cups-pdf
sudo aptitude install cups-pdf
```

That worked for me, thanks! Not sure if it matters but another poster had suggested that I needed a PDF folder (accessible by anyone) in my Home folder. I created that before doing the above steps.

---

### Post by trancer_ on 2010-06-13
> **blazemore said:**
> my only other advice would be
```
sudo aptitude purge cups-pdf
sudo aptitude install cups-pdf
```

Yes! This helped me too!

---

### Post by rugbeeprop on 2010-10-22
> **blazemore said:**
> my only other advice would be
```
sudo aptitude purge cups-pdf
sudo aptitude install cups-pdf
```

Amazing... works for me.

---

