---
title: "More Epson SX 205 grief"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by taronski on 2009-02-02
Hiya,

I am painfully new to Linux so please bear with me.

I followed the instructions in the "[SOLVED] Epson Stylus SX205 - cannot install/use printer and scanner" thread but still no luck.

Attached the bug report I got

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Stylus-SX200 (default)>,
'cups_instance': None,
'cups_queue': 'Stylus-SX200',
'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20SX200',
'printer-info': u'EPSON Stylus SX200',
'printer-is-shared': True,
'printer-location': u'Beast',
'printer-make-and-model': u'Epson Stylus Scan 2500 - CUPS+Gutenprint v5.2.0-rc1',
'printer-state': 3,
'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',
'printer-state-reasons': [u'none'],
'printer-type': 8556556,
'printer-uri-supported': u'ipp://localhost:631/printers/Stylus-SX200'},
'cups_printer_remote': False,
'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'C0L0': {u'StpInkSet': u'None'},
u'C0L2': {u'StpPrintingDirection': u'None',
u'StpWeave': u'None'},
u'C0L3': {u'StpInkType': u'None'},
u'C0L4': {u'StpFeedSequence': u'None'},
u'C1L0': {u'StpBrightness': u'None',
u'StpColorCorrection': u'None',
u'StpContrast': u'None',
u'StpFineBrightness': u'None',
u'StpFineContrast': u'None',
u'StpFineSaturation': u'None',
u'StpImageType': u'TextGraphics',
u'StpSaturation': u'None'},
u'C1L1': {u'StpBlackDensity': u'None',
u'StpCyanDensity': u'None',
u'StpDensity': u'None',
u'StpDitherAlgorithm': u'None',
u'StpFineBlackDensity': u'None',
u'StpFineCyanDensity': u'None',
u'StpFineDensity': u'None',
u'StpFineMagentaDensity': u'None',
u'StpFineYellowDensity': u'None',
u'StpMagentaDensity': u'None',
u'StpYellowDensity': u'None'},
u'C1L2': {u'StpBlackGamma': u'None',
u'StpCyanBalance': u'None',
u'StpCyanGamma': u'None',
u'StpFineBlackGamma': u'None',
u'StpFineCyanBalance': u'None',
u'StpFineCyanGamma': u'None',
u'StpFineGamma': u'None',
u'StpFineMagentaBalance': u'None',
u'StpFineMagentaGamma': u'None',
u'StpFineYellowBalance': u'None',
u'StpFineYellowGamma': u'None',
u'StpGamma': u'None',
u'StpMagentaBalance': u'None',
u'StpMagentaGamma': u'None',
u'StpYellowBalance': u'None',
u'StpYellowGamma': u'None'},
u'C1L4': {u'StpLinearContrast': u'False'},
u'C1L5': {u'StpBlackTrans': u'None',
u'StpDropSize1': u'None',
u'StpDropSize2': u'None',
u'StpDropSize3': u'None',
u'StpFineBlackTrans': u'None',
u'StpFineDropSize1': u'None',
u'StpFineDropSize2': u'None',
u'StpFineDropSize3': u'None',
u'StpFineGCRLower': u'None',
u'StpFineGCRUpper': u'None',
u'StpFineInkLimit': u'None',
u'StpGCRLower': u'None',
u'StpGCRUpper': u'None',
u'StpInkLimit': u'None'},
u'General': {u'ColorModel': u'RGB',
u'MediaType': u'Plain',
u'OutputOrder': u'Reverse',
u'PageRegion': u'A4',
u'PageSize': u'A4',
u'Resolution': u'361x360dpi',
u'StpColorPrecision': u'Normal',
u'StpQuality': u'Standard',
u'StpiShrinkOutput': u'Shrink'}},
'cups_printer_ppd_valid': True,
'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
'device-id': u'MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1;MDL:Styl us SX200;CLSRINTER;DES:EPSON Stylus SX200;',
'device-info': u'EPSON Stylus SX200 USB #1',
'device-make-and-model': u'EPSON Stylus SX200'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',
'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
'MaxLogSize': '2000000',
'SystemGroup': 'lpadmin',
'_debug_logging': '0',
'_remote_admin': '0',
'_remote_any': '0',
'_remote_printers': '0',
'_share_printers': '0',
'_user_cancel_any': '0'},
'error_log_checkpoint': 5028L}
Page 9 (Print test page):
{'test_page_attempted': True,
'test_page_job_id': [8],
'test_page_job_status': [(False,
7,
'Stylus-SX200',
'Printer Maintenance',
'Stopped',
None),
(True,
8,
'Stylus-SX200',
'Test Page',
'Processing',
{'attributes-charset': u'utf-8',
'attributes-natural-language': u'en-gb',
'document-format': u'application/postscript',
'job-hold-until': u'no-hold',
'job-id': 8,
'job-k-octets': 17,
'job-media-sheets-completed': 1,
'job-more-info': u'ipp://localhost:631/jobs/8',
'job-name': u'Test Page',
'job-originating-host-name': u'localhost',
'job-originating-user-name': u'taron',
'job-printer-state-message': u'Printing page 1, 21%',
'job-printer-state-reasons': [u'none'],
'job-printer-up-time': 1233580966,
'job-printer-uri': u'ipp://Beast:631/printers/Stylus-SX200',
'job-priority': 50,
'job-sheets': [u'none', u'none'],
'job-state': 5,
'job-state-reasons': u'job-printing',
'job-uri': u'ipp://localhost:631/jobs/8',
'job-uuid': u'urn:uuid:4ec02214-0016-3e6f-44c6-2267243a0c95',
'printer-uri': u'ipp://localhost/printers/Stylus-SX200',
'time-at-completed': None,
'time-at-creation': 1233580960,
'time-at-processing': 1233580960})],
'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['I [02/Feb/2009:13:22:34 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Adding start banner page "none".',
'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Adding end banner page "none".',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] File of type application/postscript queued by "taron".',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Queued on "Stylus-SX200" by "taron".',
'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/pstopdf (PID 1021',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/pdftopdf (PID 10221)',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/pdftoraster (PID 10224)',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started filter /usr/lib/cups/filter/rastertogutenprint.5.2 (PID 10226)',
'I [02/Feb/2009:13:22:40 +0000] [Job 8] Started backend /usr/lib/cups/backend/usb (PID 1022',
'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:40 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:43 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:43 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:44 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:45 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:46 +0000] Saving subscriptions.conf...',
'I [02/Feb/2009:13:22:46 +0000] Saving subscriptions.conf...']}
Page 11 (Printer state reasons):
{'printer-state-message': u'Printing page 1, 21%',
'printer-state-reasons': [u'none']}

Unfortunately printer scanner is one of those attributes that I need from my PC and I would be really happy to be a "purist" with no dual boot.

Thanks

Taron

---

### Post by halovivek on 2009-02-03
I hope these threads will help you
1.[ link]("http://ubuntuforums.org/archive/index.php/t-932547.html")

2. [link]("http://ubuntuforums.org/showthread.php?t=206927")
3. [link]("http://www.etanonline.fr/en/2008/ubuntu-installer-une-imprimante-multifonction-espson-dx8450/")

---

### Post by taronski on 2009-02-03
Thanks a lot.

Thanks to those notes I got the printer working (but not the scanner, not recognised in xsane)

Taron

---

### Post by halitech on 2009-02-03
try running xsane as sudo
```
sudo xsane
``` and see if it finds the scanner

---

### Post by taronski on 2009-02-04
No luck with sudo xsane unfortunatelly. 

Is there a command line to check if the system sees the scanner?

Thanks

Taron

PS scary pop up "YOU ARE ALONE"

---

### Post by halitech on 2009-02-05
if its a usb printer/scanner  you can use
```
lsusb
``` to list your devices. 

chances are if the printer works but the scanner doesn't, its not just a connection issue.

---

### Post by cariboo on 2009-02-05
Have you tried in a Applications--Accessories-->Terminal:

```
sane-find-scanner
```

Have a look at the [Scanner Howto]("http://tldp.org/HOWTO/Scanner-HOWTO/index.html").

Jim

---

### Post by celiapgt on 2010-06-04
Hello. I wonder if you still need to use your Epson SX205 scanner. There's a pwebpage [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) where you can download the Linux driver for this scanner. I regularlay use it because I also have an Epson all-in-one.

Good luck!

---

