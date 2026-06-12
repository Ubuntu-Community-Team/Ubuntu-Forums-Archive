---
title: "hp laserjet P1008 not printing. please help"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by santhust on 2009-04-05
hi.
i am using ubuntu 8.10 on Dell inspiron 1525 laptop
 yesterday i bought HP Laser jet P1008 laser printer.  i had previously checked that the drivers are there for the same in my operating system.  when i connected the printer through USB, it got installed.  when i try to print some document then i see my printer's name listed in the print window.  but when i press the print button then nothing is printed.  however it has been able to print once, one page, yesterday.  i am able to print the documents in windows vista (which is another OS installed in my laptop).each time i press the print button, the job number increases by one and now it has reached 19 after my multiple trials for printing.  here below i am attaching a copy which may be of some help.

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8dd13a0>,
 'cups_instance': None,
 'cups_queue': 'HP_LaserJet_P1008',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/HP_LaserJet_P1008?serial=DC09F1M',
                       'printer-info': u'Hewlett-Packard HP LaserJet P1008',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet P1006 Foomatic/foo2xqx (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167956,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP_LaserJet_P1008'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(16, u'Job completed.'), (17, u'Job completed.')],
 'test_page_job_id': [16, 17],
 'test_page_job_status': [(16, 'HP_LaserJet_P1008', 'Test Page'),
                          (17, 'HP_LaserJet_P1008', 'Test Page')],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by superprash2003 on 2009-04-05
install hplip [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1008.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1008.html)

---

### Post by santhust on 2009-04-05
santhust@santhust-laptop:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          2.8.2-0ubuntu8 HP Linux Printing and Imaging System (HPLIP)
santhust@santhust-laptop:~$ 


the HP site says the version should be at least 2.8.6 where as when my efforts to update hplip resulted in terminal telling me that the installed version is the latest by itself.

however i followed the steps given at the hp's site to download and install hplip, whose version seems to be 3.9.2, but encountered a problem. 
** i installed dependency packages, downloaded hplip, configured it for installation. then i had to run make but the following appeared in the terminal:**
[I]santhust@santhust-laptop:~/Desktop/hplip-3.9.2$ make
make: *** No targets specified and no makefile found.  Stop.[/I]
it was noted on the site that one has to run make as a regular user and NOT as a root user.
so this is where i am stuck up..
pls help
):P :guitar:

---

