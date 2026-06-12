---
title: "cannot print .ps documents but pdf prints ok."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by varunreeves on 2009-03-13
Hello everyone,
I do not remember testing it earlier but I have installed the packages upgrades for the ubuntu intrepid and today I suddenly found that I cannot print .ps files.I can print pdf files ok.I tried printing using the document viewer and okular on ubuntu.I started the trouble shooting for the printer and what actually happens is that when I give the print command then a printer icon appears on the top right of the title bar but it suddenly goes away.When the same thing happens with the pdf it results in printing the document but  for the .ps (postscript )file I have it does not print.Now when I look at the trouble shooter which is running it displays the job as "completed."I dont understand what has happened and so please help.The trouble shooter also has spit out some information which I am pasting here for ready reference.



Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest LaserJet-4350 (default)>,
 'cups_instance': None,
 'cups_queue': 'LaserJet-4350',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'http',
 'cups_printer_dict': {'device-uri': u'http://128.220.67.21',
                       'printer-info': u'grad lounge',
                       'printer-is-shared': True,
                       'printer-location': u'lounge',
                       'printer-make-and-model': u'HP LaserJet 4350 Postscript (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 168148,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserJet-4350'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'remote_server_name': u'128.220.67.21',
 'remote_server_port': 631}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Collate': u'False',
                                            u'Duplex': u'DuplexNoTumble',
                                            u'InputSlot': u'Auto',
                                            u'ManualFeed': u'False',
                                            u'MediaType': u'None',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'HPFinishing': {u'HPEdgeToEdge': u'False',
                                                u'HPManualDuplex': u'False',
                                                u'HPStaplerOptions': u'None',
                                                u'OutputBin': u'PrinterDefault'},
                               u'HPImagingOptions': {u'HPEconoMode': u'PrinterDefault',
                                                     u'HPHalftone': u'PrinterDefault',
                                                     u'Resolution': u'600x600dpi',
                                                     u'Smoothing': u'PrinterDefault'},
                               u'HPJobRetention': {u'HPJobName': u'DocName',
                                                   u'HPJobRetentionOption': u'HPJobRetentionOff',
                                                   u'HPUserName': u'FileSharingName'},
                               u'HPWaterMarks': {u'HPwmBrightness': u'Medium',
                                                 u'HPwmFontName': u'HelveticaB',
                                                 u'HPwmFontSize': u'pt48',
                                                 u'HPwmPages': u'AllPages',
                                                 u'HPwmSwitch': u'Off',
                                                 u'HPwmTextAngle': u'Deg45',
                                                 u'HPwmTextMessage': u'Draft',
                                                 u'HPwmTextStyle': u'Medium'},
                               u'InstallableOptions': {u'HPOption_Disk': u'False',
                                                       u'HPOption_Duplexer': u'True',
                                                       u'HPOption_Envelope_Feeder': u'False',
                                                       u'HPOption_MBM_Mixed': u'Standard',
                                                       u'HPOption_Tray3': u'False',
                                                       u'HPOption_Tray4': u'False',
                                                       u'HPOption_Tray5': u'False',
                                                       u'HPPaperPolicy': u'PromptUser',
                                                       u'InstalledMemory': u'Mem48_63'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Check network server sanity):
{'remote_server_name_resolves': ['128.220.67.21',
                                 '128.220.67.21',
                                 '128.220.67.21'],
 'remote_server_try_connect': u'128.220.67.21'}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 2275L}
Page 8 (Print test page):
{'test_page_job_status': [(True,
                           55,
                           'LaserJet-4350',
                           'hw1.dvi (hw1.ps)',
                           'Completed',
                           {'Duplex': u'DuplexNoTumble',
                            'HPEconoMode': u'PrinterDefault',
                            'HPEdgeToEdge': False,
                            'HPHalftone': u'PrinterDefault',
                            'HPJobName': u'DocName',
                            'HPJobRetentionOption': u'HPJobRetentionOff',
                            'HPManualDuplex': False,
                            'HPUserName': u'FileSharingName',
                            'HPwmBrightness': u'Medium',
                            'HPwmFontName': u'HelveticaB',
                            'HPwmFontSize': u'pt48',
                            'HPwmPages': u'AllPages',
                            'HPwmSwitch': u'Off',
                            'HPwmTextAngle': u'Deg45',
                            'HPwmTextMessage': u'Draft',
                            'HPwmTextStyle': u'Medium',
                            'InputSlot': u'Auto',
                            'ManualFeed': False,
                            'MediaType': u'None',
                            'OutputBin': u'PrinterDefault',
                            'PageSize': u'Letter',
                            'Resolution': u'600x1200dpi',
                            'Smoothing': u'PrinterDefault',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 55,
                            'job-k-octets': 228,
                            'job-media-sheets-completed': 6,
                            'job-more-info': u'ipp://localhost:631/jobs/55',
                            'job-name': u'hw1.dvi (hw1.ps)',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'varun',
                            'job-preserved': False,
                            'job-printer-state-message': u'Waiting for job to complete...',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1236995225,
                            'job-printer-uri': u'ipp://varun-laptop:631/printers/LaserJet-4350',
                            'job-priority': 80,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 9,
                            'job-state-reasons': u'job-completed-successfully',
                            'job-uri': u'ipp://localhost:631/jobs/55',
                            'job-uuid': u'urn:uuid:1da27e21-1337-39c2-7df2-7e8359597bd7',
                            'number-up': 1,
                            'printer-uri': u'ipp://localhost:631/printers/LaserJet-4350',
                            'time-at-completed': 1236995193,
                            'time-at-creation': 1236995189,
                            'time-at-processing': 1236995189})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': []}

---

### Post by 73ckn797 on 2009-03-19
Have not had to print any ps files. Maybe you could convert them to another format.

---

