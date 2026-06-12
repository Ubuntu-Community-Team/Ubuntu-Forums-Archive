---
title: "Help Epson nx 105 Printer!"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by TRiCiDE on 2009-01-29
Hello,

  I followed these instructions that someone else posted along time ago.  I can print test pages but nothing else.  I have Ubuntu 8.04.

These were the directions.

I've noticed that there are quite a few people having problems getting their Epson Stylus SX105 All-In-One machine working.

Here's how I got the printer working under Hardy and Intrepid (scanner is still unresolved, to my knowledge):

Go to [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Select the driver for Epson Stylus NX100/SX100/TX100/TX101/TX105/TX106,Epson ME 300 and fill in the other required information.

Download the file that matches your version of Ubuntu (8.04,8.10).

Extract the file to a folder, open terminal and cd into the folder (example: cd /home/username/Documents).

Installation for Hardy Heron:
Code:

sudo bash pips-snx100-ubuntu8.04-3.3.0-CG.install

Installation for Intrepid Ibex:
Code:

sudo bash pips-snx100-ubuntu8.04-3.5.0-CG.install

You should now be able to use your printer. Good luck!
__________________
Pacman so silly

---

### Post by TRiCiDE on 2009-01-29
OK here's the troubleshooting copy.  Please let me know what you think.

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8707320>,
 'cups_instance': None,
 'cups_queue': 'Stylus_NX100',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20NX100',
                       'printer-info': u'EPSON Stylus NX100',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus NX100, Photo Image Print System',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_NX100'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [], 'test_page_successful': True}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by TRiCiDE on 2009-01-29
Refreshing it, looking for help. Heeeeeelp! :D

---

