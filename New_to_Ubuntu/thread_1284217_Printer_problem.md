---
title: "Printer problem"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by viodelin on 2009-10-06
Hello,
I have a HP 1100A printer and I'm running Ubuntu Heron. It worked fine with the HPLIP driver until I tried to print some PDFs. Since then it pretends to have done the printing, but I know it hasn't, and it's just ignoring the jobs, reminds me of my kids.

The troubleshooter gives me this:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86fe080>,
 'cups_instance': None,
 'cups_queue': 'LaserJet_1100A',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'Impresora laser',
                       'printer-is-shared': True,
                       'printer-location': u'labonita',
                       'printer-make-and-model': u'HP LaserJet 1100A Foomatic/ljet4 (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 12292,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserJet_1100A'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(22, u'Job completed.')],
 'test_page_job_id': [22],
 'test_page_job_status': [(22, 'LaserJet_1100A', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}


Any help would be greatly appreciated

---

### Post by bernardfrancois on 2009-10-14
Do you mean you are trying to print pdf files with your HP printer, or are you printing documents to pdf files? In the latter case, these pdf files will be stored in the PDF folder in your home folder.

---

### Post by Chuck_W on 2009-10-14
In the last year or so I've been seeing a problem with some pdf files. You send them to the printer and absolutely nothing happens. I've seen it at work and at home. Different OS's, different documents. The one thing that seems to work is to go to "Advanced Settings" (or something like that) and tell it to print as image. The processing time is a little longer but it does print. Purely speculation but I suspect that the "print to pdf" function of some applications may be the cause.

---

### Post by Captain_tux on 2009-10-15
Off topic, but ...

Bernard, awesome avatar!!

---

### Post by bernardfrancois on 2009-10-21
Maybe there's still an unfinished pdf file in the print queue, blocking other print orders?

You can view the print que by going to system>administration>printing, and then you can right-click on the printer and choose 'View Print Queue'.

@Captain_tux: Better use a PM for off topic stuff. I sent you one.

---

### Post by HarrisonNapper on 2009-10-21
Also, when this gets solved, could you post the output of the troubleshooter while it's working? For posterity/google.

From what I can find, you might want to make sure there are options besides HP LaserJet 1100A Foomatic/ljet4 (recommended) for your printer make/model. I've seen examples where this had to be changed in printer settings.

Can you post the output of ```
cat /dev/lp0
```? Looks like cups is finding the information, but it never hurts to check ^^

Cheers.

---

