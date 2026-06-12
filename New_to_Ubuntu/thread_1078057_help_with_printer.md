---
title: "help with printer"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by BJH44 on 2009-02-22
I just install ubuntu today and I can't get the printer to work. It Shows the printer and it looks like it will work, but it never prints. Could someone help.

Also, how do I get new applications, like AUDACITY to show on the desktop.

Thanks,

Sammy
sammyholmes.com

---

### Post by llamabr on 2009-02-22
What kind of printer?

Putting things on the desktop should not be hard.  Right click on desktop, and choose laucher.  But you might find it more convenient to put it on the task bar.  The desktop is a bit awkward.

---

### Post by BJH44 on 2009-02-23
My printer is a MFC210C. Sorry 'bout that.

---

### Post by plucky on 2009-02-23
> My printer is a MFC210C.


Open Synaptic package manager and search for **MFC-210c** and you should find ```
brother-cups-wrapper-extra
brother-lpr-driver-extra
```

Mark both for installation and **Apply**

After the drivers have been installed,plug in and power up printer.

Go to **System > Administration > Printing** and select "New Printer".

The printer will then be installed.

If you have to troubleshoot the printer,use the CUPS interface.Open Firefox and in the address bar type ```
http://localhost:631
```


Good Luck

---

### Post by BJH44 on 2009-02-23
Ok, I did all you said. I went as instructed to NEW PRINTER where it said "search for drivers for MFC-210c. It comes back with not matches. Now what? I think I would like UBUNTU but it5 is hard to figure this thing out.

---

### Post by plucky on 2009-02-24
> **BJH44 said:**
> Ok, I did all you said. I went as instructed to NEW PRINTER where it said "search for drivers for MFC-210c. It comes back with not matches. Now what? I think I would like UBUNTU but it5 is hard to figure this thing out.

Takes time to learn,but completely worth it.

Open a terminal **Applications > Accessories > Terminal** and copy and paste each command individually into the terminal window ```
dpkg -l | grep brother
lsusb
lpq
``` and post output to the forums.

I assume it found your printer as it was searching for the driver.

1)Did it display in the "Printing" window?
2)Did you connect it with a USB connector or is it a parallel connection?

---

### Post by BJH44 on 2009-02-24
It is USB and it does go to print. The printer never receives the data.
I will send the terminal output soon.

---

### Post by avtolle on 2009-02-24
One other thought. Power down the printer and computer. Attach the printer, power up the computer and see if that results in both the printer being recognized and your being able to print. Another thought: check the USB port; is it a USB 1.1 or 2.0 port? Sometimes, for reasons I don't understand, there is a problem with a newer USB device if it is in a 1.1 port rather than a 2.0 port. Don't know if either of these thoughts are worth anything, but here they are.

EDIT: Attach the printer, power it up, then power up the computer... Sorry about leaving the part about powering the printer up out the first time; it's been a long day.

---

### Post by BJH44 on 2009-02-24
sammy@ubuntu:~$ dpkg -l | grep brother
ii  brother-cups-wrapper-common                1.0.0-10-0ubuntu5                       Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                 1.2.1-0ubuntu3                          Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-common                 1.0.0-4-0ubuntu1                        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                  1.2.0-2-0ubuntu3                        LPR drivers for extra brother printers
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

sammy@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f9:0161 Brother Industries, Ltd MFC-210C
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

sammy@ubuntu:~$ lpq
MFC-210C is ready
no entries

---

### Post by BJH44 on 2009-02-24
Here is the trouble shooter report:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest MFC-210C (default)>,
 'cups_instance': None,
 'cups_queue': 'MFC-210C',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Brother/MFC-210C',
                       'printer-info': u'Brother MFC-210C',
                       'printer-is-shared': True,
                       'printer-location': u'ubuntu',
                       'printer-make-and-model': u'Generic text-only printer',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4100,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MFC-210C'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'SendFF': u'False'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Brother;CMD:HBP,BRPJL;MDL:MFC-210C;CLS:PRINTER;',
                      'device-info': u'Brother MFC-210C USB #1',
                      'device-make-and-model': u'Brother MFC-210C'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 1561L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(1, u'Job completed.')],
 'test_page_job_id': [1],
 'test_page_job_status': [(True,
                           1,
                           'MFC-210C',
                           'Test Page',
                           'Completed',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'text/plain',
                            'job-hold-until': u'no-hold',
                            'job-id': 1,
                            'job-k-octets': 1,
                            'job-media-sheets-completed': 1,
                            'job-more-info': u'ipp://localhost:631/jobs/1',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'sammy',
                            'job-preserved': False,
                            'job-printer-state-message': u'Printer is now on-line.',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1235518435,
                            'job-printer-uri': u'ipp://ubuntu.ubuntu-domain:631/printers/MFC-210C',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 9,
                            'job-state-reasons': u'job-completed-successfully',
                            'job-uri': u'ipp://localhost:631/jobs/1',
                            'job-uuid': u'urn:uuid:f459aa95-33d9-3f41-5780-f72788c7a136',
                            'printer-uri': u'ipp://localhost/printers/MFC-210C',
                            'time-at-completed': 1235518390,
                            'time-at-creation': 1235518387,
                            'time-at-processing': 1235518387})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [24/Feb/2009:17:32:56 -0600] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:32:56 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:32:56 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:32:56 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:32:56 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:32:56 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:32:56 -0600] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:32:56 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:32:56 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:32:56 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:32:56 -0600] Create-Printer-Subscription /',
               'D [24/Feb/2009:17:32:56 -0600] cupsdCreateSubscription(con=0xb8560658(8), uri="/")',
               'D [24/Feb/2009:17:32:56 -0600] pullmethod="ippget"',
               'D [24/Feb/2009:17:32:56 -0600] notify-lease-duration=86400',
               'D [24/Feb/2009:17:32:56 -0600] notify-time-interval=0',
               'D [24/Feb/2009:17:32:56 -0600] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [24/Feb/2009:17:32:56 -0600] Added subscription 10 for server',
               'I [24/Feb/2009:17:32:56 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:32:56 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:32:56 -0600] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:32:57 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:32:57 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:32:57 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:32:57 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:32:57 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:32:57 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:32:57 -0600] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:33:07 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:33:07 -0600] cupsdReadClient: 8 POST /printers/MFC-210C HTTP/1.1',
               'D [24/Feb/2009:17:33:07 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:07 -0600] Print-Job ipp://localhost/printers/MFC-210C',
               "D [24/Feb/2009:17:33:07 -0600] Print-Job client-error-document-format-not-supported: Unsupported format 'application/postscript'!",
               'D [24/Feb/2009:17:33:07 -0600] cupsdProcessIPPRequest: 8 status_code=40a (client-error-document-format-not-supported)',
               'D [24/Feb/2009:17:33:07 -0600] cupsdReadClient: 8 POST /printers/MFC-210C HTTP/1.1',
               'D [24/Feb/2009:17:33:07 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:07 -0600] Print-Job ipp://localhost/printers/MFC-210C',
               'D [24/Feb/2009:17:33:07 -0600] add_job: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:07 -0600] Adding default job-sheets values "none,none"...',
               'I [24/Feb/2009:17:33:07 -0600] [Job 1] Adding start banner page "none".',
               'I [24/Feb/2009:17:33:07 -0600] Saving subscriptions.conf...',
               'I [24/Feb/2009:17:33:07 -0600] [Job 1] Adding end banner page "none".',
               'I [24/Feb/2009:17:33:07 -0600] [Job 1] File of type text/plain queued by "sammy".',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] hold_until=0',
               'I [24/Feb/2009:17:33:07 -0600] [Job 1] Queued on "MFC-210C" by "sammy".',
               'I [24/Feb/2009:17:33:07 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] job-sheets=none,none',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] banner_page = 0',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[0]="MFC-210C"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[1]="1"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[2]="sammy"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[3]="Test Page"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[4]="1"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[5]="job-uuid=urn:uuid:f459aa95-33d9-3f41-5780-f72788c7a136"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] argv[6]="/var/spool/cups/d00001-001"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[9]="SERVER_ADMIN=root@ubuntu.ubuntu-domain"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[12]="TZ=America/Chicago"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[13]="USER=root"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[16]="IPP_PORT=631"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[17]="CHARSET=utf-8"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[18]="LANG=en_US.UTF8"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[19]="PPD=/etc/cups/ppd/MFC-210C.ppd"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[20]="RIP_MAX_CACHE=8m"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[21]="CONTENT_TYPE=text/plain"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[22]="DEVICE_URI=usb://Brother/MFC-210C"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[23]="PRINTER=MFC-210C"',
               'D [24/Feb/2009:17:33:07 -0600] [Job 1] envp[24]="FINAL_CONTENT_TYPE=printer/MFC-210C"',
               'I [24/Feb/2009:17:33:07 -0600] [Job 1] Started filter /usr/lib/cups/filter/textonly (PID 31761)',
               'I [24/Feb/2009:17:33:07 -0600] [Job 1] Started backend /usr/lib/cups/backend/usb (PID 31762)',
               'I [24/Feb/2009:17:33:07 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:07 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:07 -0600] cupsdCloseClient: 8',
               'I [24/Feb/2009:17:33:08 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:08 -0600] [Job 1] Printer using device file "/dev/usblp0"...',
               'D [24/Feb/2009:17:33:08 -0600] [Job 1] backendRunLoop(print_fd=0, device_fd=5, use_bc=0, side_cb=0xb7f28a80)',
               'I [24/Feb/2009:17:33:08 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:08 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:08 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:08 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:33:08 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:08 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:33:08 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:08 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:08 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:08 -0600] CUPS-Get-Classes',
               'D [24/Feb/2009:17:33:08 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:08 -0600] CUPS-Get-Default',
               'D [24/Feb/2009:17:33:08 -0600] CUPS-Get-Default client-error-not-found: No default printer',
               'D [24/Feb/2009:17:33:08 -0600] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)',
               'D [24/Feb/2009:17:33:08 -0600] cupsdCloseClient: 11',
               'D [24/Feb/2009:17:33:08 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Classes',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Default',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Default client-error-not-found: No default printer',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Classes',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Default',
               'D [24/Feb/2009:17:33:09 -0600] CUPS-Get-Default client-error-not-found: No default printer',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdCloseClient: 8',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:09 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdCloseClient: 8',
               'I [24/Feb/2009:17:33:09 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:09 -0600] [Job 1] Read 22 bytes of print data...',
               'D [24/Feb/2009:17:33:09 -0600] [Job 1] Wrote 22 bytes of print data...',
               'I [24/Feb/2009:17:33:09 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [24/Feb/2009:17:33:09 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:09 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:09 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:09 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:09 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Classes',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Default',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Default client-error-not-found: No default printer',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdCloseClient: 11',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:10 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdCloseClient: 11',
               'D [24/Feb/2009:17:33:10 -0600] PID 31761 (/usr/lib/cups/filter/textonly) exited with no errors.',
               'D [24/Feb/2009:17:33:10 -0600] PID 31762 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [24/Feb/2009:17:33:10 -0600] [Job 1] File 0 is complete.',
               'I [24/Feb/2009:17:33:10 -0600] [Job 1] Completed successfully.',
               'I [24/Feb/2009:17:33:10 -0600] Saving subscriptions.conf...',
               'I [24/Feb/2009:17:33:10 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:10 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Classes',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Default',
               'D [24/Feb/2009:17:33:10 -0600] CUPS-Get-Default client-error-not-found: No default printer',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 12 status_code=406 (client-error-not-found)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:10 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:10 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:10 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:33:10 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:10 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:11 -0600] [Job 1] Unloading...',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] Create-Printer-Subscription /',
               'D [24/Feb/2009:17:33:14 -0600] cupsdCreateSubscription(con=0xb85626b8(9), uri="/")',
               'D [24/Feb/2009:17:33:14 -0600] pullmethod="ippget"',
               'D [24/Feb/2009:17:33:14 -0600] notify-lease-duration=86400',
               'D [24/Feb/2009:17:33:14 -0600] notify-time-interval=0',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [24/Feb/2009:17:33:14 -0600] Added subscription 11 for server',
               'I [24/Feb/2009:17:33:14 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] CUPS-Get-Printers',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] CUPS-Get-Classes',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] CUPS-Get-Default',
               'D [24/Feb/2009:17:33:14 -0600] CUPS-Get-Default client-error-not-found: No default printer',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=406 (client-error-not-found)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:14 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:14 -0600] Get-Notifications /',
               'D [24/Feb/2009:17:33:14 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'D [24/Feb/2009:17:33:14 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:14 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:55 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:55 -0600] Report: clients=2',
               'D [24/Feb/2009:17:33:55 -0600] Report: jobs=1',
               'D [24/Feb/2009:17:33:55 -0600] Report: jobs-active=0',
               'D [24/Feb/2009:17:33:55 -0600] Report: printers=1',
               'D [24/Feb/2009:17:33:55 -0600] Report: printers-implicit=0',
               'D [24/Feb/2009:17:33:55 -0600] Report: stringpool-string-count=530',
               'D [24/Feb/2009:17:33:55 -0600] Report: stringpool-alloc-bytes=7296',
               'D [24/Feb/2009:17:33:55 -0600] Report: stringpool-total-bytes=11576',
               'D [24/Feb/2009:17:33:55 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:55 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:55 -0600] Get-Job-Attributes ipp://localhost/jobs/1',
               'D [24/Feb/2009:17:33:55 -0600] [Job 1] Loading attributes...',
               'D [24/Feb/2009:17:33:55 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:55 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:55 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:55 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [24/Feb/2009:17:33:55 -0600] cupsdAuthorize: No authentication data provided.',
               'D [24/Feb/2009:17:33:55 -0600] Cancel-Subscription /',
               'D [24/Feb/2009:17:33:55 -0600] cupsdIsAuthorized: requesting-user-name="sammy"',
               'I [24/Feb/2009:17:33:55 -0600] Saving subscriptions.conf...',
               'D [24/Feb/2009:17:33:55 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [24/Feb/2009:17:33:55 -0600] cupsdCloseClient: 9',
               'D [24/Feb/2009:17:33:55 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [24/Feb/2009:17:33:55 -0600] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [24/Feb/2009:17:33:55 -0600] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}

---

### Post by Vantrax on 2009-02-24
In reply to the other question:

You get new applications to show up on the desktop by either creating a new launcher (equivalent to a shortcut) by right clicking on the desktop then clicking create launcher.

You can also copy the .desktop file (shortcut) from /usr/share/applications where the shortcuts for the Applications menu are stored.

---

### Post by BJH44 on 2009-02-24
I got it working by renaming it Brother instead of MFC210C. Thanks for all the help.

---

### Post by northwestuntu on 2009-04-01
> **plucky said:**
> Open Synaptic package manager and search for MFC-210c and you should find
Code:

brother-cups-wrapper-extra
brother-lpr-driver-extra

Mark both for installation and Apply

After the drivers have been installed,plug in and power up printer.

Go to System > Administration > Printing and select "New Printer".

thanks!! that worked perfect :p

---

