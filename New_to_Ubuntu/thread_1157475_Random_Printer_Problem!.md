---
title: "Random Printer Problem!"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Frank-er on 2009-05-12
Okay so...I'm on my dad's computer, and he asked me to help him. The printer was working fine and such, for the last 3 weeks and now out of the blue the thing decides to be non-functional. It acts as if it isn't plugged in or not connected. I've tried switching USB ports, still nothing. I also tried the troubleshooting function, this is the result.

PS. The usb ports work for the mouse and keyboard. Any help would be awesome!

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest officejet-4200-series2 (default)>,
 'cups_instance': None,
 'cups_queue': 'officejet-4200-series2',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hal',
 'cups_printer_dict': {'device-uri': u'hal:///org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if1_printer_CN571GH1P4',
                       'printer-info': u'hp officejet 4200 series',
                       'printer-is-shared': True,
                       'printer-location': u'Home',
                       'printer-make-and-model': u'HP Officejet 4200 Series hpijs, 3.9.2',
                       'printer-state': 4,
                       'printer-state-message': u'Printer not connected; will retry in 30 seconds...',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/officejet-4200-series2'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'Printer not connected; will retry in 30 seconds...',
 'printer-state-reasons': [u'connecting-to-device']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 3154L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': '12/May/2009:06:58:45 +0000',
 'test_page_job_id': [50],
 'test_page_job_status': [(True,
                           49,
                           'officejet-4200-series2',
                           'Fax mail(7)',
                           'Processing',
                           {'PageSize': u'Letter',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 49,
                            'job-k-octets': 227,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/49',
                            'job-name': u'Fax mail(7)',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'robert',
                            'job-printer-state-message': u'Printer not connected; will retry in 30 seconds...',
                            'job-printer-state-reasons': [u'connecting-to-device'],
                            'job-printer-up-time': 1242125933,
                            'job-printer-uri': u'ipp://Home:631/printers/officejet-4200-series2',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/49',
                            'job-uuid': u'urn:uuid:37dc0f25-1e2e-3a16-7b7e-9711c5ddfd63',
                            'number-up': 2,
                            'printer-uri': u'ipp://localhost/printers/officejet-4200-series2',
                            'time-at-completed': None,
                            'time-at-creation': 1242125819,
                            'time-at-processing': 1242125819}),
                          (True,
                           50,
                           'officejet-4200-series2',
                           'Test Page',
                           'Pending',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 50,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/50',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'robert',
                            'job-printer-up-time': 1242125933,
                            'job-printer-uri': u'ipp://Home:631/printers/officejet-4200-series2',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 3,
                            'job-state-reasons': u'none',
                            'job-uri': u'ipp://localhost:631/jobs/50',
                            'job-uuid': u'urn:uuid:061669ef-2190-3b15-5dbe-9d3a3483fe21',
                            'number-up': 2,
                            'printer-uri': u'ipp://localhost/printers/officejet-4200-series2',
                            'time-at-completed': None,
                            'time-at-creation': 1242125925,
                            'time-at-processing': None})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [12/May/2009:06:58:36 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:36 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:36 -0400] Get-Jobs ipp://localhost/printers/',
               'D [12/May/2009:06:58:36 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:36 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:36 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:36 -0400] Get-Jobs ipp://localhost/printers/',
               'D [12/May/2009:06:58:36 -0400] [Job 32] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 33] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 34] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 35] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 36] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 37] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 38] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 39] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 40] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 41] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 42] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 43] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 44] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 45] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 46] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 47] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] [Job 48] Loading attributes...',
               'D [12/May/2009:06:58:36 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:36 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:36 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:36 -0400] Create-Printer-Subscription /',
               'D [12/May/2009:06:58:36 -0400] cupsdCreateSubscription(con=0xb9cbfb58(7), uri="/")',
               'D [12/May/2009:06:58:36 -0400] pullmethod="ippget"',
               'D [12/May/2009:06:58:36 -0400] notify-lease-duration=86400',
               'D [12/May/2009:06:58:36 -0400] notify-time-interval=0',
               'D [12/May/2009:06:58:36 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [12/May/2009:06:58:36 -0400] Added subscription 80 for server',
               'I [12/May/2009:06:58:36 -0400] Saving subscriptions.conf...',
               'D [12/May/2009:06:58:36 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:37 -0400] Get-Notifications /',
               'D [12/May/2009:06:58:37 -0400] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [12/May/2009:06:58:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:45 -0400] cupsdAcceptClient: 10 from localhost (Domain)',
               'D [12/May/2009:06:58:45 -0400] cupsdReadClient: 10 POST /printers/officejet-4200-series2 HTTP/1.1',
               'D [12/May/2009:06:58:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:45 -0400] Print-Job ipp://localhost/printers/officejet-4200-series2',
               'D [12/May/2009:06:58:45 -0400] [Job ???] Auto-typing file...',
               'I [12/May/2009:06:58:45 -0400] [Job ???] Request file type is application/postscript.',
               'D [12/May/2009:06:58:45 -0400] add_job: requesting-user-name="robert"',
               'D [12/May/2009:06:58:45 -0400] Adding default job-sheets values "none,none"...',
               'I [12/May/2009:06:58:45 -0400] [Job 50] Adding start banner page "none".',
               'I [12/May/2009:06:58:45 -0400] Saving subscriptions.conf...',
               'I [12/May/2009:06:58:45 -0400] [Job 50] Adding end banner page "none".',
               'I [12/May/2009:06:58:45 -0400] [Job 50] File of type application/postscript queued by "robert".',
               'D [12/May/2009:06:58:45 -0400] [Job 50] hold_until=0',
               'I [12/May/2009:06:58:45 -0400] [Job 50] Queued on "officejet-4200-series2" by "robert".',
               'D [12/May/2009:06:58:45 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:45 -0400] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [12/May/2009:06:58:45 -0400] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [12/May/2009:06:58:45 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [12/May/2009:06:58:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:45 -0400] Get-Notifications /',
               'D [12/May/2009:06:58:45 -0400] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [12/May/2009:06:58:45 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:45 -0400] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [12/May/2009:06:58:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:45 -0400] Get-Notifications /',
               'D [12/May/2009:06:58:45 -0400] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [12/May/2009:06:58:45 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:45 -0400] cupsdCloseClient: 12',
               'D [12/May/2009:06:58:45 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [12/May/2009:06:58:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:45 -0400] Get-Job-Attributes ipp://localhost/jobs/50',
               'D [12/May/2009:06:58:45 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:45 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:45 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:45 -0400] Get-Notifications /',
               'D [12/May/2009:06:58:45 -0400] cupsdIsAuthorized: requesting-user-name="robert"',
               'D [12/May/2009:06:58:45 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:45 -0400] cupsdCloseClient: 11',
               'D [12/May/2009:06:58:53 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:53 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:53 -0400] Get-Job-Attributes ipp://localhost/jobs/49',
               'D [12/May/2009:06:58:53 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:53 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:53 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:53 -0400] Get-Job-Attributes ipp://localhost/jobs/50',
               'D [12/May/2009:06:58:53 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:53 -0400] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [12/May/2009:06:58:53 -0400] cupsdAuthorize: No authentication data provided.',
               'D [12/May/2009:06:58:53 -0400] Cancel-Subscription /',
               'D [12/May/2009:06:58:53 -0400] cupsdIsAuthorized: requesting-user-name="robert"',
               'I [12/May/2009:06:58:53 -0400] Saving subscriptions.conf...',
               'D [12/May/2009:06:58:53 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [12/May/2009:06:58:53 -0400] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [12/May/2009:06:58:53 -0400] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1',
               'D [12/May/2009:06:58:53 -0400] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'job_page_size': u'Letter',
 'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```

---

### Post by cariboo on 2009-05-12
Does the printer show up when you plug it in? Open a terminal and type:

```
dmesg | tail -n15
```

Paste the output in your next post.

---

### Post by Frank-er on 2009-05-12
Hmm the command didn't work. 

EDIT: Cause I'm captain of the assclown brigade!

```
[  686.476882] ppdev0: unregistered pardevice
[  705.597547] usblp0: removed
[  816.784253] ppdev0: registered pardevice
[  816.834442] ppdev0: unregistered pardevice
[  817.188770] ppdev0: registered pardevice
[  817.236526] ppdev0: unregistered pardevice
[  817.281531] ppdev0: registered pardevice
[  817.328366] ppdev0: unregistered pardevice
[ 1034.382977] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[ 1034.448332] [fglrx] Maximum main memory to use for locked dma buffers: 1644 MBytes.
[ 1034.448387] [fglrx]   vendor: 1002 device: 9610 count: 1
[ 1034.448941] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[ 1034.448957] pci 0000:01:05.0: setting latency timer to 64
[ 1034.450423] [fglrx] Driver built-in PAT support is enabled successfully
[ 1034.450450] [fglrx:firegl_init_module] *ERROR* firegl_stub_register faile

```

---

### Post by Frank-er on 2009-05-12
Anyone, anyone at all? This is bugging me to hell and back. Plus my sister is a PITA as she needs the printer for schoolwork.

---

