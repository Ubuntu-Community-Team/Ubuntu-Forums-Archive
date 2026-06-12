---
title: "Hp LaserJet 1000 series"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by abou maryam on 2009-02-21
hello ,

i've installed Ubuntu 8.10 , and i'm trying to install the driver for Hp LaserJet 1000 series , but i don't know how to do this !!!

so please help me , how can i install driver for my printer ...

printer is connected via usb ........

---

### Post by blueridgedog on 2009-02-22
I think that printer has been supported for a while, you can click System -> Administration -> Printing, then Server, then connect, select local host in the server box and click connect, then click the new button and follow the instructions to select your printer.

---

### Post by stalkingwolf on 2009-02-22
you can also try System > Preferences > Default Printer.

---

### Post by abou maryam on 2009-02-24
Thanks for replying,

i've clicked on System -> Administration -> Printing, then Server, then i've connected to local host ,and  then i've clicked the new button and i've added my hplaser jet 1000 series .

and then i've tryed to print a test page but nothing is printed , also i've printed another document , and i have the same result .

always the print job is queed but nothing is printed ....

the printer is ok , i've used it on windows xp .......

---

### Post by abou maryam on 2009-02-24
i've used the troubleshot, and i've followed the steps , finally i've got these reprot , i think it may help to know more about the problem :




```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest hp-LaserJet-1000 (default)>,
 'cups_instance': None,
 'cups_queue': 'hp-LaserJet-1000',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1000?serial=0',
                       'printer-info': u'hp-LaserJet-1000',
                       'printer-is-shared': True,
                       'printer-location': u'wassim-desktop',
                       'printer-make-and-model': u'HP LaserJet 1000 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp-LaserJet-1000'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 4.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/hp_LaserJet_1000?serial=0\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   '  cups-printer                  hp-LaserJet-1000                                          ',
                   '  cups-uri                      hp:/usb/hp_LaserJet_1000?serial=0                         ',
                   '  dev-file                                                                                ',
                   '  device-state                  1                                                         ',
                   '  device-uri                    hp:/usb/hp_LaserJet_1000?serial=0                         ',
                   '  deviceid                      MFG:Hewlett-Packard;MDL:hp LaserJet                       ',
                   '                                1000;CMD:ZJS;CLS:PRINTER;DES:hp LaserJet                  ',
                   '                                1000;FWVER:20011207;                                      ',
                   '  duplexer                      0                                                         ',
                   '  error-state                   0                                                         ',
                   '  host                                                                                    ',
                   '  in-tray1                      1                                                         ',
                   '  in-tray2                      1                                                         ',
                   '  is-hp                         True                                                      ',
                   '  media-path                    1                                                         ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  photo-tray                    0                                                         ',
                   '  port                          1                                                         ',
                   '  r                             0                                                         ',
                   '  revision                      254                                                       ',
                   '  rg                            000                                                       ',
                   '  rr                            000000                                                    ',
                   '  rs                            000000000                                                 ',
                   '  serial                        0                                                         ',
                   '  status-code                   1000                                                      ',
                   '  status-desc                   Idle.                                                     ',
                   '  supply-door                   1                                                         ',
                   '  top-door                      1                                                         ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    0                                                         ',
                   '  clean-type                    0                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          0                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   1                                                         ',
                   '  icon                          default_printer.png                                       ',
                   '  io-mfp-mode                   1                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    2                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         hp_LaserJet_1000                                          ',
                   '  model-ui                      HP LaserJet 1000                                          ',
                   '  model1                        LaserJet 1000                                             ',
                   '  panel-check-type              0                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        1                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   8                                                         ',
                   '  support-released              1                                                         ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   2.7.12                                                    ',
                   "  tech-class                    ['LJZjsMono']                                             ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     3                                                         ',
                   '  usb-pid                       0517                                                      ',
                   '  usb-vid                       03f0                                                      ',
                   '\x1b[01m',
                   'Status History (most recent first):\x1b[0m',
                   '\x1b[01m  Date/Time             Code   Status Description                        User      Job ID  \x1b[0m',
                   '  --------------------  -----  ----------------------------------------  --------  --------',
                   '  02/24/09 17:10:20     1000   Idle.                                     wassim    0       ',
                   '',
                   '',
                   'Done.',
                   ''],
                  ['']),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Copies': u'1',
                                            u'InputSlot': u'Auto',
                                            u'MediaType': u'Standard',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Quality': u'normal'},
                               u'Miscellaneous': {u'Nup': u'1up',
                                                  u'NupOrient': u'port'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:hp LaserJet 1000;CLS:PRINTER;DES:hp LaserJet 1000;SN:0;',
                      'device-info': u'HP LaserJet 1000 USB 0 HPLIP',
                      'device-make-and-model': u'HP LaserJet 1000'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 2516L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [14],
 'test_page_job_status': [(True,
                           14,
                           'hp-LaserJet-1000',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 14,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 1,
                            'job-more-info': u'ipp://localhost:631/jobs/14',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'wassim',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1235488257,
                            'job-printer-uri': u'ipp://wassim-desktop:631/printers/hp-LaserJet-1000',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/14',
                            'job-uuid': u'urn:uuid:66bde061-2db1-38ab-5e6a-c72bb4311115',
                            'printer-uri': u'ipp://localhost/printers/hp-LaserJet-1000',
                            'time-at-completed': None,
                            'time-at-creation': 1235488244,
                            'time-at-processing': 1235488244})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [24/Feb/2009:17:10:41 +0200] cupsdCloseClient: 7',
               'D [24/Feb/2009:17:10:41 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [24/Feb/2009:17:10:41 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:41 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:41 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:10:41 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:41 +0200] cupsdCloseClient: 7',
               'D [24/Feb/2009:17:10:41 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [24/Feb/2009:17:10:41 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:41 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:41 +0200] Create-Printer-Subscription /',
               'D [24/Feb/2009:17:10:41 +0200] cupsdCreateSubscription(con=0xb92137f8(7), uri="/")',
               'D [24/Feb/2009:17:10:41 +0200] pullmethod="ippget"',
               'D [24/Feb/2009:17:10:41 +0200] notify-lease-duration=86400',
               'D [24/Feb/2009:17:10:41 +0200] notify-time-interval=0',
               'D [24/Feb/2009:17:10:41 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [24/Feb/2009:17:10:41 +0200] Added subscription 23 for server',
               'I [24/Feb/2009:17:10:41 +0200] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:10:41 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:41 +0200] cupsdCloseClient: 7',
               'D [24/Feb/2009:17:10:42 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [24/Feb/2009:17:10:42 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:42 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:42 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:42 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:42 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:42 +0200] cupsdCloseClient: 7',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [24/Feb/2009:17:10:44 +0200] cupsdReadClient: 7 POST /printers/hp-LaserJet-1000 HTTP/1.1',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:44 +0200] Print-Job ipp://localhost/printers/hp-LaserJet-1000',
               'D [24/Feb/2009:17:10:44 +0200] add_job: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:44 +0200] Adding default job-sheets values "none,none"...',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Adding start banner page "none".',
               'I [24/Feb/2009:17:10:44 +0200] Saving subscriptions.conf...',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Adding end banner page "none".',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] File of type application/postscript queued by "wassim".',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] hold_until=0',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Queued on "hp-LaserJet-1000" by "wassim".',
               'I [24/Feb/2009:17:10:44 +0200] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] job-sheets=none,none',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] banner_page = 0',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[0]="hp-LaserJet-1000"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[1]="14"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[2]="wassim"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[3]="Test Page"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[4]="1"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[5]="job-uuid=urn:uuid:66bde061-2db1-38ab-5e6a-c72bb4311115"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] argv[6]="/var/spool/cups/d00014-001"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[9]="SERVER_ADMIN=root@wassim-desktop"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[12]="TZ=Asia/Beirut"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[13]="USER=root"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[16]="IPP_PORT=631"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[17]="CHARSET=utf-8"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[18]="LANG=en_US.UTF8"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[19]="PPD=/etc/cups/ppd/hp-LaserJet-1000.ppd"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[20]="RIP_MAX_CACHE=8m"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[22]="DEVICE_URI=hp:/usb/hp_LaserJet_1000?serial=0"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[23]="PRINTER=hp-LaserJet-1000"',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] envp[24]="FINAL_CONTENT_TYPE=printer/hp-LaserJet-1000"',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Started filter /usr/lib/cups/filter/pstopdf (PID 5374)',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Started filter /usr/lib/cups/filter/pdftopdf (PID 5376)',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Started filter /usr/lib/cups/filter/foomatic-rip (PID 5378)',
               'I [24/Feb/2009:17:10:44 +0200] [Job 14] Started backend /usr/lib/cups/backend/hp (PID 5381)',
               'I [24/Feb/2009:17:10:44 +0200] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:10:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] pstopdf argv[6] = 14 wassim Test Page 1 job-uuid=urn:uuid:66bde061-2db1-38ab-5e6a-c72bb4311115 /var/spool/cups/d00014-001',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] PPD: /etc/cups/ppd/hp-LaserJet-1000.ppd',
               'D [24/Feb/2009:17:10:44 +0200] cupsdCloseClient: 7',
               'I [24/Feb/2009:17:10:44 +0200] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Resolution:',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Page size: Letter',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Getting input from file',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] foomatic-rip version 4.0.0.195 running...',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Parsing PPD file ...',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option PageSize',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option Quality',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option PrinterType',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option ColorMode',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option Resolution',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option ImageableArea',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option PaperDimension',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option InputSlot',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option MediaType',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option Copies',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option Nup',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option NupOrient',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Added option Font',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Parameter Summary',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] -----------------',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Spooler: cups',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Printer: hp-LaserJet-1000',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Shell: /bin/bash',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] PPD file: /etc/cups/ppd/hp-LaserJet-1000.ppd',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] ATTR file:',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Printer model: HP LaserJet 1000 Foomatic/foo2zjs (recommended)',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Job title: Test Page',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] File(s) to be printed:',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] <STDIN>',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               "D [24/Feb/2009:17:10:44 +0200] [Job 14] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               "D [24/Feb/2009:17:10:44 +0200] [Job 14] Pondering option 'job-uuid=urn:uuid:66bde061-2db1-38ab-5e6a-c72bb4311115'",
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Unknown option job-uuid=urn:uuid:66bde061-2db1-38ab-5e6a-c72bb4311115.',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] ================================================',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] File: <STDIN>',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] ================================================',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Width: 612, height: 792, absolute margins: , , ,',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Relative margins: 11.34, 11.34, 11.34, 11.34',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] PostScript to be injected:',
               'D [24/Feb/2009:17:10:44 +0200] [Job 14] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [24/Feb/2009:17:10:44 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:44 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:10:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:44 +0200] cupsdCloseClient: 7',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:44 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:44 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:44 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:44 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:44 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:44 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] Get-Job-Attributes ipp://localhost/jobs/14',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] CUPS-Get-Printers',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] CUPS-Get-Classes',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] CUPS-Get-Default',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] CUPS-Get-Printers',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] CUPS-Get-Classes',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] CUPS-Get-Default',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:45 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:45 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:45 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:45 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:45 +0200] cupsdCloseClient: 7',
               'D [24/Feb/2009:17:10:45 +0200] [Job 14] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [24/Feb/2009:17:10:46 +0200] [Job 14] Filetype: PDF',
               'D [24/Feb/2009:17:10:46 +0200] [Job 14] Driver does not understand PDF input, converting to PostScript',
               'D [24/Feb/2009:17:10:46 +0200] [Job 14] Starting process "pdf-to-ps" (generation 1)',
               'D [24/Feb/2009:17:10:46 +0200] PID 5374 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [24/Feb/2009:17:10:47 +0200] PID 5376 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Filetype: PostScript',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Reading PostScript input ...',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] --> This document is DSC-conforming!',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] -----------',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Found: %%BeginProlog',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Inserting option code into "Prolog" section.',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Found: %%EndProlog',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] -----------',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] New page: %%Page: 1 1',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] "Setup" section is missing, inserting it.',
               "D [24/Feb/2009:17:10:47 +0200] [Job 14] Inserting PostScript code for CUPS' page accounting",
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Inserting option code into "Setup" section.',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Found: %%BeginPageSetup',
               'D [24/Feb/2009:17:10:47 +0200] [Job 14] Inserting option code into "PageSetup" section.',
               'D [24/Feb/2009:17:10:48 +0200] [Job 14] Flushing FIFO.',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] Starting renderer with command: "foo2zjs-wrapper -P    -r600x600 -p1 -m1 -s7   "',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] Starting process "kid3" (generation 1)',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] Starting process "kid4" (generation 2)',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] JCL: \x1b%-12345X@PJL',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] <job data>',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] Starting process "renderer" (generation 2)',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14]',
               'D [24/Feb/2009:17:10:49 +0200] [Job 14] Closing renderer',
               'I [24/Feb/2009:17:10:53 +0200] Saving subscriptions.conf...',
               'I [24/Feb/2009:17:10:53 +0200] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:10:53 +0200] [Job 14] renderer exited with status 0',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:53 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:10:53 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:53 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:53 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:53 +0200] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:53 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:53 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:53 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:53 +0200] CUPS-Get-Printers',
               'D [24/Feb/2009:17:10:53 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:53 +0200] CUPS-Get-Classes',
               'D [24/Feb/2009:17:10:53 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:53 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:53 +0200] CUPS-Get-Default',
               'D [24/Feb/2009:17:10:53 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:53 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:54 +0200] cupsdCloseClient: 12',
               'D [24/Feb/2009:17:10:54 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:54 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:54 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:54 +0200] Get-Notifications /',
               'D [24/Feb/2009:17:10:54 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'D [24/Feb/2009:17:10:54 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:54 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:57 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:57 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:57 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:57 +0200] Get-Job-Attributes ipp://localhost/jobs/14',
               'D [24/Feb/2009:17:10:57 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:57 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:57 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:57 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:10:57 +0200] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:10:57 +0200] Cancel-Subscription /',
               'D [24/Feb/2009:17:10:57 +0200] cupsdIsAuthorized: requesting-user-name="wassim"',
               'I [24/Feb/2009:17:10:57 +0200] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:10:57 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:10:57 +0200] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:10:57 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:10:57 +0200] cupsdReadClient: 8 GET /admin/log/error_log HTTP/1.1',
               'D [24/Feb/2009:17:10:57 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
```

---

### Post by PRC09 on 2009-02-25
Found this link and used this driver.Everything works but was a bit of a struggle to follow.



[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

---

### Post by abou maryam on 2009-02-25
thanks for the reply, 

i've followed this steps but when i become at

and then i've connected to localhost , and then i've created a new printer , but also it doesen't print .

---

### Post by abou maryam on 2009-03-01
i've justed installed hplip-3.9.2.run  , but also it won't to print, any one can help me to solve this problem ??

---

### Post by green0eggs on 2009-03-07
> **abou maryam said:**
> Thanks for replying,

i've clicked on System -> Administration -> Printing, then Server, then i've connected to local host ,and  then i've clicked the new button and i've added my hplaser jet 1000 series .

and then i've tryed to print a test page but nothing is printed , also i've printed another document , and i have the same result .

always the print job is queed but nothing is printed ....

the printer is ok , i've used it on windows xp .......

I seem to be having the same problem. 

The printer manager detects my printer and supports the model (HPLJ 1020) but when I send jobs or test pages they sit in the queue and then get 'sent' (Status: Completed) but nothing happens in the real world.

---

### Post by gandaran on 2009-03-07
> **green0eggs said:**
> I seem to be having the same problem. 

The printer manager detects my printer and supports the model (HPLJ 1020) but when I send jobs or test pages they sit in the queue and then get 'sent' (Status: Completed) but nothing happens in the real world.
how is the printer connected? just the simple usb connection to your computer or is the printer shared over a network of more than one computer?

---

### Post by green0eggs on 2009-03-08
Just a simple USB.

---

### Post by green0eggs on 2009-04-04
I hate to bump threads, but has anyone found a solution to this?

My printer (1020) is fully supported and all the drivers *seem* to be installed OK, (print jobs accepted and get status: 'Completed' but it doesn't *actually* print anything. 

I've done a troubleshoot and seem to have a similar output to abou maryam in post #5 which I have attached to keep the post readable.

Furthermore I know it is not a printer hardware fault because I can print from (shudder) Windows just fine. In fact (transparent attempt at invoking pride in the Ubuntu forums wise-men(and wise-ladies)) printing is the only thing I need Windows for nowadays.

Also would I be advised to start a new thread? Since my model is different.

Thanks

---

### Post by grahams on 2009-04-06
I seemed to be having the same issue on 8.10 with an HP1020. This was working fine a few weeks ago (I don't print very often), but now doesn't work. Looks like an issue with the latest CUPS update.

---

### Post by bambuin on 2009-04-06
i have also problems with my laserjet 1018.
i can see the printer in localhost, the pc says that everything is ok but when i m going to print, says that the printer is not connected.(is connected with usb )

---

### Post by expatCM on 2009-04-06
Did you install hplip (in the repositories)?

I did this to get my 1200 series to work .....

---

### Post by bambuin on 2009-04-06
yeap
it s already installed

---

### Post by MrWES on 2009-04-06
Try connecting to the printer via the Web GUI

[http://localhost:631]("http://localhost:631")

You should be able to see your printer from there, and also any errors messages regarding the status. Also, there is an option to set the config file back to default -- helps sometimes if it has become corrupted.

Bill

---

### Post by green0eggs on 2009-04-06
Thanks for the responses

> **grahams said:**
> This was working fine a few weeks ago 

Did you set up the printer (when it worked) in a clever way using the command line? Or just like me with the straightforward System/Administration/Printing?




> **MrWES said:**
> Try connecting to the printer via the Web GUI

[http://localhost:631]("http://localhost:631")

You should be able to see your printer from there, and also any errors messages regarding the status. Also, there is an option to set the config file back to default -- helps sometimes if it has become corrupted.

Bill

I have used this before as well: there are no error messages when printing a doc. The web GUI tells me that the print job's status is 'Completed' including a date and time.

I have also reset the config to default and saved. This produces the same results.

Thanks for the replies though, makes me feel less lonely!

---

### Post by MrWES on 2009-04-06
> **green0eggs said:**
> Thanks for the responses



Did you set up the printer (when it worked) in a clever way using the command line? Or just like me with the straightforward System/Administration/Printing?






I have used this before as well: there are no error messages when printing a doc. The web GUI tells me that the print job's status is 'Completed' including a date and time.

I have also reset the config to default and saved. This produces the same results.

Thanks for the replies though, makes me feel less lonely!

Try unplugging the printer from the usb port, wait a couple of minutes and then plug it back in. Now check 
```
dmesg | tail
```

For any potential error messages concerning the usb hub.

Bill

---

### Post by gandaran on 2009-04-06
is the printer set as default printer?

---

### Post by green0eggs on 2009-04-06
> **MrWES said:**
> Try unplugging the printer from the usb port, wait a couple of minutes and then plug it back in. Now check 
```
dmesg | tail
```

For any potential error messages concerning the usb hub.

Bill

I unplugged all other USB devices and the terminal shows me this:
```
[  387.229935] usb 1-3: configuration #1 chosen from 1 choice
[  387.375808] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
[  387.376696] usbcore: registered new interface driver usblp
[  591.648058] usb 2-1: USB disconnect, address 2
[  593.684027] Clocksource tsc unstable (delta = -384954119 ns)
[  603.356196] usb 1-3: USB disconnect, address 4
[  603.359418] usblp0: removed
[  607.276286] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  607.442551] usb 1-3: configuration #1 chosen from 1 choice
[  607.445982] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17

```

Which I'm afraid makes no sense to me.


> **gandaran said:**
> is the printer set as default printer?

Yep.


Thanks for your help, I do appreciate it!

---

### Post by LowSky on 2009-04-06
these printer have an issue where the printer doesn't restart after a reboot, dumb issue but there is a workaround

this is how I installed my LaserJet 1018 

first install HPLIP (it in the Repos).
they should auto find and get install easily.
then unplug printer (complete power off) 
replug in computer,
reboot everything it should work correctly and from now on.

If not try HPLIP form sourceforge, that veriosn is usually more up to date than the repo version
[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

---

### Post by stchman on 2009-04-06
To install the LaserJet 1000 series do the following:

Install hplip

```
sudo apt-get install hplip
```

Now launch hplip and select the LaserJet 1000 series printer.  There will be a firmware you need to load.

After that it will work.

---

### Post by bambuin on 2009-04-06
i still don't print after all

---

### Post by drs305 on 2009-04-06
My LaserJet-1000 worked fine for years with CUPS and then with HPLIP. I upgraded with a fresh Jaunty install and found the way I had done it in the past no longer worked for me. I really liked HPLIP but got my printer working without it.

Here's what I did:
Removed hplip and hpijs. I now only have CUPS + and f002zjs from compilation from the link below. The actual instructions start about half way down the page: 
[_http://foo2zjs.rkkda.com/_]("http://foo2zjs.rkkda.com/")
Opened CUPS from the address below to add the printer: _[http://localhost:631/printers/]("http://localhost:631/printers/")_
The address of my printer is: usb://HP/LaserJet%201000 
The driver I am using is "Foomatic/foo2zjs"

Sometimes I have to cycle the power or go to the CUPS interface page to restart the printer, but that may be because I leave it off most of the time, including at boot.

I would really have liked the HPLIP to work, but for some reason it wouldn't on this install. However, remember Jaunty is still beta so I'm not complaining.

---

### Post by rintintin on 2009-04-06
I struggled quite a while to get an HP Laserjet 1000 working with Ubuntu 10.8.
What finally worked was advice at the very bottom of: 
[https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/96454](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/96454)

In essence, I fixed the problem by typing

sudo /usr/share/hplip/plugin.py    

[answer "d" then "Y" when prompted during running of the above command]

sudo getweb 1000 (... which may be overkill but seemed also to help)

Next, I then deleted any printers already existing under 'system --> administration --> printing'.  

Lastly, I created a new printer, choosing the device called "HP Laserjet 1000 USB 0 HPLIP" then I selected HP from the database in the next pane, and then what seemed to really make a difference was _not_ choosing the "recommended" driver in the next pane, but instead selecting "HP Laserjet Foomatic/hpijs-ZJS [en]" rather than anything labeled foomatic/foo2zjs... 

This seems to have done the trick!

---

### Post by grahams on 2009-04-07
Thanks 

I found just loading the firmware was all I needed.

sudo /usr/share/hplip/plugin.py

---

### Post by green0eggs on 2009-04-07
> **rintintin said:**
> I struggled quite a while to get an HP Laserjet 1000 working with Ubuntu 10.8.
What finally worked was advice at the very bottom of: 
[https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/96454](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/96454)

In essence, I fixed the problem by typing

sudo /usr/share/hplip/plugin.py    

[answer "d" then "Y" when prompted during running of the above command]

sudo getweb 1000 (... which may be overkill but seemed also to help)

Next, I then deleted any printers already existing under 'system --> administration --> printing'.  

Lastly, I created a new printer, choosing the device called "HP Laserjet 1000 USB 0 HPLIP" then I selected HP from the database in the next pane, and then what seemed to really make a difference was _not_ choosing the "recommended" driver in the next pane, but instead selecting "HP Laserjet Foomatic/hpijs-ZJS [en]" rather than anything labeled foomatic/foo2zjs... 

This seems to have done the trick!



[SIZE="6"]This worked![/SIZE]

What I did:
[LIST]
Ran
```
sudo /usr/share/hplip/plugin.py
```
[/LIST]
[LIST]
Answered 'd' and download firmware update,
Answered 'y' to install updated firmware when prompted.
[/LIST][LIST]
Then deleted previous instance of HP1020 in System>>Administration>>Printing and re-added this time choosing
[CENTER]"HP Laserjet 1020 Foomatic/hpijs-ZJS [en]"[/CENTER]
[/LIST]
[LIST]Test page was submitted and given Status 'Completed'
...And a real life test page popped out of the printer!!![/LIST]

---

### Post by bambuin on 2009-04-13
i ve done all this and still not printing
i see the printer, i installed all the stuffs, i chosen HP Laserjet 1018 Foomatic...
and still nothing
the work goes in queu, is processing and then it desapears without printing

---

### Post by bambuin on 2009-04-28
ok the problem resolved after i upgraded to ubuntu 9.04 and
type 
sudo /usr/share/hplip/plugin.py 
and then retry 5-6 times to print the same job
it was like it has waked up...

---

### Post by bambuin on 2009-04-28
> **bambuin said:**
> i ve done all this and still not printing
i see the printer, i installed all the stuffs, i chosen HP Laserjet 1018 Foomatic...
and still nothing
the work goes in queu, is processing and then it desapears without printing

i restarted the pc and the same problem
:(:(:confused:

---

### Post by bambuin on 2009-04-28
> **bambuin said:**
> ok the problem resolved after i upgraded to ubuntu 9.04 and
type 
sudo /usr/share/hplip/plugin.py 
and then retry 5-6 times to print the same job
it was like it has waked up...

i ve done this again from the beggining
and that worked again
and if i restart the pc i must do the same thing again and again?
maybe something doesn't work with the usb portals...
the important is that with the jaunty, the driver worked better...

---

### Post by grahams on 2009-04-30
After updating to 9.04 my 1020 wont print again

after I run 
sudo /usr/share/hplip/plugin.py -i

I get the following error

Downloading firmware to device hp:/usb/HP_LaserJet_1020?serial=FN1B7LR...
error: Device busy: hp:/usb/HP_LaserJet_1020?serial=FN1B7LR
error: unable to open channel
error: Device busy: hp:/usb/HP_LaserJet_1020?serial=FN1B7LR
error: unable to open channel
error: Channel write error
error: An error occured: Device I/O error

Tried deleting the printer and trying again, same issue.
Any clues? 

Btw. the printer still works on 8.10, so not a H/W issue

---

### Post by bambuin on 2009-04-30
after a new restart the problem was there again
then i typed
sudo hp-setup
and it resolved

---

### Post by wally the duck on 2009-04-30
Bambuin,
Did it stay resolved? For me that only works until the next restart.

---

### Post by grahams on 2009-04-30
sudo hp-setup

doesn't work either for me on 9.04

Very frustrating I need to print

---

### Post by grahams on 2009-05-02
Not sure how or why but it is now working again.

---

### Post by SJC-Caron on 2009-05-03
I seem to have the same problem too.  My HP LaserJet1000 will not physically print, even though as far as Ubuntu 9.04 is concerned, the file has printed.  Would the fact that I am running Ubuntu as a dual-boot with Windows XP (also where the LaserJet is the default printer) play a part in causing this issue?  I plan looking in XP to check out this theory in an bit.

---

### Post by wally the duck on 2009-05-07
Any luck?
The Laserjet 1020 still will not work for me in Ubuntu 9.04 Jaunty unless it is turned off when the computer starts and then manually turned on once the computer is running. It will not load the hp usb direct port during boot.
I've downloaded, installed, removed, retried and played with every suggested 'fix' I could find... but it is the same now as when I first installed Jaunty.

---

### Post by GARoss on 2009-05-13
Hi all. HP printer problems? Me, too. 
I've been working with Aaron @ launchpad & the going is slow.
[https://answers.launchpad.net/hplip/+question/70935](https://answers.launchpad.net/hplip/+question/70935)
A few days ago everything except test print in HPLIP was working. But then the wife ran out of paper & now I can't print anything. It has this circle of device is busy error & code 1018. Really at a loss as to what to do.

---

### Post by drs305 on 2009-05-15
I just completed a fresh install of jaunty 64-bit. I tried all the HP tips in the last 10 posts or so and was still unable to get my HP LJ-1000 to work - even after downloading the HP drivers automatically.

I resorted to the steps I took in post #25 (removing all HP packages and installing foomatic and cups) and my printer is working normally again.

---

### Post by tundraquad on 2009-05-26
A very _**easy**_ & clean way **which worked** in Jaunty:
unplug usb > del any printer
> from Synaptic, remove any foo, foomatic, hp , hplip , hpoj
> reboot > install hplip-3.9.4b (just double-click the *.run)
> plug usb when rqrd > close all printer config windows >
> set hp-Laserjet-10002 as default printer > open HP Device Mgr > Actions > Install required plugin > select ...from HP authorized...    => printer should spool.
> reboot cpt (should spool during start) > perform a printing test > del printer hp-Laserjet-1000

---

### Post by pikaia on 2009-07-23
I have the same problem, and NONE of the proposed options work for me.  Jaunty sees it, but won't print.  It worked fine in Hardy (yesterday).  But after an upgrade to Jaunty (fresh install) it doesnt' work.  I've tried the hplip, hplip-gui, hp-setup, plugin... everything, none of it works.  

Is there anyone who ACTUALLY has gotten their 1020 to work in Jaunty?

EDIT:  I finally got mine to work.  I followed the instructions here:

[https://answers.launchpad.net/ubuntu/+source/hplip/+question/45032](https://answers.launchpad.net/ubuntu/+source/hplip/+question/45032)

It seems the firmware isn't installed properly and you need to download and copy a driver into your foo2zjs folder.  Good luck.

---

### Post by grahams on 2009-08-13
If you find you lose printer connectivity after a resume from suspend, try power cycling your printer. This works for me 8/10 times.

---

### Post by wally the duck on 2009-11-25
Same problem - exactly - in Karmic with this printer. Tried every fix ever published on the net; many worked... until the first reboot, then it was the same problem all over again.

I finally went to the motherboard BIOS (a Gigabyte board) and disabled all legacy ports (serial, parallel... everything listed). FINALLY I am able to leave the printer 'on', reboot, and still have a working printer.

Something during the bootup was 'squashing' the printer installation.

---

### Post by whoey on 2011-04-21
> **grahams said:**
> Thanks 

I found just loading the firmware was all I needed.

sudo /usr/share/hplip/plugin.py


Thanks! that sorted mine out too...

---

