---
title: "No output from cups to pdf"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by johnfrith on 2010-07-16
Hi. Since updating to Lucid, I don't have any output from print to pdf using cups. A pop up screen appears, but goes before I can read it. I checked the config file, and it's still has PDF as the out directory. I checked the pdf error log and it's blank.

I note the documentation says:

   * CUPS-PDF requires root privileges since it has to modify file ownerships. In order to ensure CUPS-PDF is running with the required root privileges
     you have to make 'root' the owner of the cups-pdf backend and set the file permissions of the backend to 0700 (root only). 

but I don't know enough to understand what this entails, or even if it is relevant.

TIA for any help.

---

### Post by cariboo on 2010-07-16
Try re-installing the ghostscript-cups package to see if that corrects the problem.

---

### Post by johnfrith on 2010-07-20
> **cariboo907 said:**
> Try re-installing the ghostscript-cups package to see if that corrects the problem.
Thanks Cariboo907, I tried that but the situation remains the same.

I also note that the  print to pdf dialogue has the location as pdftemp,  even though I  thought the output was to .PDF.

I've tried searching the file system in case the output is going elsewhere, but nothing shows up. Is there a log file somewhere (beside the already blank pdf error log) that would shed light on what's happening?

TIA.

---

### Post by TimEnid on 2010-07-20
dont choose the "print to pdf" option. Just choose print. Is this the answer you are looking for? I was having a similar issue where i would choose print to pdf and the page would just get created. a pop up would come and dissapear, without giving me the chance to rename it or choose where to save it.

---

### Post by johnfrith on 2010-07-20
Thanks for posting TimEnid. Not sure I understand you completely, but it is a pdf output that I want!

Interestingly "Export to PDF" from the print options works ok (so I do have a workaround), but a normal print with PDF-Printer selected as the printer has the problem I've talked about.

---

### Post by TimEnid on 2010-07-20
> **johnfrith said:**
> Thanks for posting TimEnid. Not sure I understand you completely, but it is a pdf output that I want!

Interestingly "Export to PDF" from the print options works ok (so I do have a workaround), but a normal print with PDF-Printer selected as the printer has the problem I've talked about.

you want to print something as a pdf, correct? if so, dont choose print to pdf, you will not see the option to rename the document or be able to choose where to save it. just select "Print", you will get the print config screen. and there is an option (which should already be checked, if print to pdf is the default printer) for "pdf". If its not checked, just check it.

---

### Post by johnfrith on 2010-07-20
Thanks TimEnid. Yes, that's what I've been trying to do, with no output that I can find. :(

The only other route I know of is to "Export to PDF", which as I said previously, does work, though you have to go through extra clicks.

---

### Post by johnfrith on 2010-07-20
Noticed that the printer "PDF Printer" wasn't enabled. Now it's enabled, I get the message "There was a problem printing document XX: Stopping job because the sheduler (sic) could not execute the backend:No such file or directory". There is a "Diagnose" option, which produces the following trail. Have bolded the 1st error message, which is: "Unable to execute /usr/lib/cups/backend/cups-pdf: No such file or  directory". 

If I look at Backend properties, it is owned by root, but it says "You are not the owner, so you cannot change these permissions". 

Any ideas?

TIA.

.......
I [20/Jul/2010:17:41:29 +0100] [Job 280] Adding start banner page "none".
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(-----S)
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(----J-)
I [20/Jul/2010:17:41:29 +0100] [Job 280] Adding end banner page "none".
I [20/Jul/2010:17:41:29 +0100] [Job 280] File of type application/vnd.cups-banner queued by "john".
D [20/Jul/2010:17:41:29 +0100] [Job 280] hold_until=0
I [20/Jul/2010:17:41:29 +0100] [Job 280] Queued on "PDF-Printer" by "john".
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(----J-)
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(-----S)
D [20/Jul/2010:17:41:29 +0100] [Job 280] job-sheets=none,none
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[0]="PDF-Printer"
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[1]="280"
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[2]="john"
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[3]="Test Page"
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[4]="1"
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[5]="job-uuid=urn:uuid:68af2454-cc0c-332b-5c11-0a9bcfda1b18 job-originating-host-name=localhost"
D [20/Jul/2010:17:41:29 +0100] [Job 280] argv[6]="/var/spool/cups/d00280-001"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[8]="HOME=/var/spool/cups/tmp"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[10]="SERVER_ADMIN=root@jf"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[11]="SOFTWARE=CUPS/1.4.3"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[13]="TZ=Europe/London"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[14]="USER=root"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[17]="IPP_PORT=631"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[18]="CHARSET=utf-8"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[19]="LANG=en_GB.UTF-8"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[20]="PPD=/etc/cups/ppd/PDF-Printer.ppd"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[21]="RIP_MAX_CACHE=1012545k"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[23]="DEVICE_URI=cups-pdf:/"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[24]="PRINTER_INFO=Generic CUPS-PDF Printer"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[25]="PRINTER_LOCATION=pdftemp"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[26]="PRINTER=PDF-Printer"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[27]="CUPS_FILETYPE=document"
D [20/Jul/2010:17:41:29 +0100] [Job 280] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
I [20/Jul/2010:17:41:29 +0100] [Job 280] Started filter /usr/lib/cups/filter/bannertops (PID 6686)
I [20/Jul/2010:17:41:29 +0100] [Job 280] Started filter /usr/lib/cups/filter/pstopdf (PID 6687)
I [20/Jul/2010:17:41:29 +0100] [Job 280] Started filter /usr/lib/cups/filter/pdftopdf (PID 6688)
E [20/Jul/2010:17:41:29 +0100] **Unable to execute /usr/lib/cups/backend/cups-pdf: No such file or directory**
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(P-----)
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(-----S)
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(-----S)
E [20/Jul/2010:17:41:29 +0100] [Job 280] Stopping job because the sheduler could not execute the backend.
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(----J-)
D [20/Jul/2010:17:41:29 +0100] cupsdMarkDirty(-----S)
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/PDF-Printer) from localhost
D [20/Jul/2010:17:41:29 +0100] PID 6686 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] PID 6688 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.
D [20/Jul/2010:17:41:29 +0100] PID 6687 (/usr/lib/cups/filter/pstopdf) was terminated normally with signal 15.
D [20/Jul/2010:17:41:29 +0100] cupsdAcceptClient: 16 from localhost (Domain)
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 16 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdAcceptClient: 17 from localhost (Domain)
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 16 1.1 Get-Notifications 1
D [20/Jul/2010:17:41:29 +0100] Get-Notifications /
D [20/Jul/2010:17:41:29 +0100] cupsdIsAuthorized: requesting-user-name="john"
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 1.1 Get-Jobs 1
D [20/Jul/2010:17:41:29 +0100] Get-Jobs ipp://localhost/printers/
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 WAITING Closing on EOF
D [20/Jul/2010:17:41:29 +0100] cupsdCloseClient: 17
D [20/Jul/2010:17:41:29 +0100] cupsdAcceptClient: 17 from localhost (Domain)
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 1.1 Get-Notifications 1
D [20/Jul/2010:17:41:29 +0100] Get-Notifications /
D [20/Jul/2010:17:41:29 +0100] cupsdIsAuthorized: requesting-user-name="john"
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdAcceptClient: 18 from localhost (Domain)
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Printer-Attributes ipp://localhost/printers/PDF-Printer
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF-Printer) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Job-Attributes ipp://localhost/jobs/280
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/280) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAcceptClient: 19 from localhost (Domain)
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 19 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Printer-Attributes ipp://jf:631/printers/PDF-Printer
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jf:631/printers/PDF-Printer) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 19 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Job-Attributes ipp://localhost/jobs/280
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/280) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 12 1.1 Get-Notifications 1
D [20/Jul/2010:17:41:29 +0100] Get-Notifications /
D [20/Jul/2010:17:41:29 +0100] cupsdIsAuthorized: requesting-user-name="john"
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Printer-Attributes ipp://localhost/printers/PDF-Printer
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF-Printer) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Printer-Attributes ipp://localhost/printers/PDF-Printer
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/PDF-Printer) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Printers
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Classes
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Default
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Printers
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Classes
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Default
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Printers
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Classes
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: Authorized as john using PeerCred
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [20/Jul/2010:17:41:29 +0100] CUPS-Get-Default
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAcceptClient: 20 from localhost (Domain)
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 14 WAITING Closing on EOF
D [20/Jul/2010:17:41:29 +0100] cupsdCloseClient: 14
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 19 WAITING Closing on EOF
D [20/Jul/2010:17:41:29 +0100] cupsdCloseClient: 19
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 20 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 20 1.1 Get-Printer-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Printer-Attributes ipp://jf:631/printers/PDF-Printer
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jf:631/printers/PDF-Printer) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 20 POST / HTTP/1.1
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:29 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:29 +0100] cupsdReadClient: 20 1.1 Get-Job-Attributes 1
D [20/Jul/2010:17:41:29 +0100] Get-Job-Attributes ipp://localhost/jobs/280
D [20/Jul/2010:17:41:29 +0100] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/280) from localhost
D [20/Jul/2010:17:41:29 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:30 +0100] [Job 280] Unloading...
D [20/Jul/2010:17:41:38 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [20/Jul/2010:17:41:38 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:38 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:38 +0100] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [20/Jul/2010:17:41:38 +0100] Get-Job-Attributes ipp://localhost/jobs/280
D [20/Jul/2010:17:41:38 +0100] [Job 280] Loading attributes...
D [20/Jul/2010:17:41:38 +0100] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/280) from localhost
D [20/Jul/2010:17:41:38 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:38 +0100] cupsdReadClient: 12 POST / HTTP/1.1
D [20/Jul/2010:17:41:38 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:38 +0100] cupsdAuthorize: No authentication data provided.
D [20/Jul/2010:17:41:38 +0100] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [20/Jul/2010:17:41:38 +0100] Cancel-Subscription /
D [20/Jul/2010:17:41:38 +0100] cupsdIsAuthorized: requesting-user-name="john"
D [20/Jul/2010:17:41:38 +0100] cupsdMarkDirty(-----S)
D [20/Jul/2010:17:41:38 +0100] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [20/Jul/2010:17:41:38 +0100] cupsdSetBusyState: Dirty files
D [20/Jul/2010:17:41:38 +0100] cupsdAcceptClient: 14 from localhost (Domain)
D [20/Jul/2010:17:41:38 +0100] cupsdReadClient: 14 GET /admin/log/error_log HTTP/1.1
D [20/Jul/2010:17:41:38 +0100] cupsdSetBusyState: Active clients and dirty files
D [20/Jul/2010:17:41:38 +0100] cupsdAuthorize: No authentication data provided.

---

### Post by mainak_sen on 2010-07-21
I am having the same problem!!
I have been using Hardy for last 2 years and there were no problems and I used the print to PDF (by selecting PDF as my default printer) option very often. Ever since I upgraded to Lucid last week this is not working any longer. Even the "Print Test Page" option is not working. The various error messages I am getting are given below.
Interestingly, I have upgraded to Lucid in another machine and there also I am getting the same errors. 

I shall greatly appreciate if someone could help us!

Thanks in advance!

----Error Messages-----

Print Error: There was a problem printing document 'Test Page' (job 768): 'Stopping job because the scheduler could not execute the backend.' 

Stopped - Printer Configuration error

Status Messages: There is a missing print filter for printer 'PDF'.

---

### Post by johnfrith on 2010-07-22
Bump.

---

### Post by geonolis on 2010-08-30
It seems that the problem has to do with backend directory permissions. The answer is at [http://ubuntuforums.org/showthread.php?t=1477978](http://ubuntuforums.org/showthread.php?t=1477978) and it is as follows:

> 
I got the same error message and then i used these three commands:
  
 ```
sudo chmod 700 /usr/lib/cups/backend
sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo /etc/init.d/cups restart 
```

And then it worked


---

### Post by johnfrith on 2010-08-30
[FONT=monospace]Thanks for posting geonolis. I hadn't spotted that thread.

I tried this and got:
[/FONT]```
john@jf:~$ sudo chmod 700 /usr/lib/cups/backend
[sudo] password for john: 
john@jf:~$ sudo chmod 700 /usr/lib/cups/backend/cups-pdf
chmod: cannot access `/usr/lib/cups/backend/cups-pdf': No such file or directory
```[FONT=monospace]

Which is the same message I get trying to print. When I try and look via the file browser, it shows the backend directory with an X on it, and tells me I don't have permission to look inside, so I don't know if the cups-pdf directory is not there or I just don't have permission.

[/FONT]

---

### Post by mainak_sen on 2010-08-30
just noticed the last two posts...
Well, have you tried re-installing the CUPS-PDF from synaptic?
If not, I think it is worth trying. It worked for me...

---

