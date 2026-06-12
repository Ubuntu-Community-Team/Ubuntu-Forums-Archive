---
title: "Epson 310 won't print"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by LearningPerson on 2009-08-01
Hi all,

Had no trouble with my old Epson but this Epson Workforce 310 won't print even a test page.

I chose the default driver from the wizard which was 300.  Haven't yet figured out to hookup the fax cable - would that be a problem for the printer part?

Here is what I get from troubleshooting the printer:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8f03d00>,
 'cups_instance': None,
 'cups_queue': 'WorkForce_310',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/WorkForce%20310',
                       'printer-info': u'EPSON WorkForce 310',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus Color 300 Foomatic/stcolor (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/WorkForce_310'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(108, u'Job completed.')],
 'test_page_job_id': [108],
 'test_page_job_status': [(108, 'WorkForce_310', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

Thanks,  Sharon

---

### Post by zanetu on 2009-10-02
Try using the WorkForce 30 driver. It works for me.

---

