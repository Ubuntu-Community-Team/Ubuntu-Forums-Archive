---
title: "Problem printing to windows attached printer"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by jcryan on 2009-01-12
Hello, I am running Ubuntu Hardy on my IBM laptop as a home office machine.  My printer is attached to a Windows Media Center desktop that my kids use.  I have been able to set up sharing and can now view my windows disk from my Ubuntu machine and my Ubuntu files from my windows machine.

I can also see and was able to set a share for my windows attached printer.

Here's the problem: I can not print to the windows attached printer.

The printer is an HP Deskjet D4100.  It is working properly on the windows pc and when I plug it directly into my Ubuntu laptop so I know I have the correct driver.

When I print a test page or a document it looks like it completes on the Ubuntu machine.  The file appears in the windows print queue and the printing button starts flashing on my printer but nothing ever comes out.

I used the troubleshooting feature and it could not determine the problem but generated the following output:
[INDENT]
"Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8de11e0>,
 'cups_instance': None,
 'cups_queue': 'HomePrinter',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://RYANFAMILYPC/HomePrinter',
                       'printer-info': u'Deskjet D4100',
                       'printer-is-shared': True,
                       'printer-location': u'Laundry Room',
                       'printer-make-and-model': u'HP DeskJet D4100 Foomatic/hpijs, hpijs 2.8.2',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4108,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HomePrinter'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(106, u'Job completed.')],
 'test_page_job_id': [106],
 'test_page_job_status': [(106, 'HomePrinter', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
[/INDENT]

I have searched the forums and internet (which helped me get this far) but I am now stuck.

Any help in resolving would be appreciated.

Thanks!
Claude

---

