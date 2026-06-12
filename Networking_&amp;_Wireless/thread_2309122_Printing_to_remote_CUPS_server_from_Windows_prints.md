---
title: "Printing to remote CUPS server from Windows prints &quot;@PJL&quot; code"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by CDuv on 2016-01-07
I originally wanted to continue on the existing thread "[Printing remotely via CUPS isn't working - Prints @PJS Information]("http://ubuntuforums.org/showthread.php?t=2213919")" by Jonny_Morrison as I have the same issue (I get "-123456X@PJL JOB ..." text on my printed paper) but it is now closed, so I am starting this new thread.

I have setup a CUPS v1.7.5 server for my Xerox (using manufacturer's PPD files and LPD or Socket or IPP protocols) + HP (using *hplip*) printers and it works just fine on Ubuntu workstations: I just provide the CUPS print server FQDN and it offers me to select the printer (queue) I wan to add, no need to provide a PPD.

However, I have a issue with Windows 7 workstations and one particular Xerox printer (a *WorkCentre* with finisher modules): printers are added as "remote printer" via "http://cups-server:631/printers/printername" it prints "@PJL" commands instead of the documents:
```
-123456X@PJL JOB@PJL XCPT <?xml version="1.0" encoding="UTF-8"?>
@PJL XCPT <!DOCTYPE xpif SYSTEM "xpif-v02082.dtd">
@PJL XCPT <xpif version="1.0" cpss-version="2.07" xml:lang="en-US">
@PJL XCPT     <job-template-attributes>
[...]
@PJL COMMENT DCPVer: DSPY 5.433.6.1
@PJL XCPT ENTER LANGUAGE=PCLXL
) HP-PCL XL;3.0;Comment Copyright © 2000-2015 Xerox Corporation. All Rights Reserved.
jX
```

Windows workstations have the Windows Xerox's printer driver installed locally and it works when configuring Windows to directly access the printer (bypassing the CUPS server)
If I set the printer queue on "RAW" in CUPS (without PPD then) it then works for Windows, but Ubuntu workstations now need to be provided with a PPD when adding the printer :-/

[According to houstonbofh]("http://ubuntuforums.org/showthread.php?t=2213919&p=12971702#post12971702"), when one experience this "@PJL" code issue, it is because of Windows driver that already has processed the document and the solution he provides is to set CUPS queue to RAW and suggests to make Samba force CUPS to RAW (via the "cups options = raw" paramter) and use Samba to access printer queues from Windows.

Is there another way that to involve a Samba server? Couldn't CUPS somehow detect if job is coming already processed?
Another workaround would be to have two queues: a RAW (for Windows) and a PPD-based for Ubuntu but it would requires more maintenance on the long run. 

Thanks

---

