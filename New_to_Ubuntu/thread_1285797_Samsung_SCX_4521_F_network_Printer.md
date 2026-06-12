---
title: "Samsung SCX 4521 F network Printer"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by chitragurung on 2009-10-08
I have been using Dell Inspiron Mini with ubuntu OS. Everything fine but I could not use my network printer. When I try to print it does not print. It says cups missing filter. How can I use network printer using ubuntu I am using Samsung SCX4521 F multifunctional printer black and white in network.

---

### Post by swoody on 2009-10-08
Try running:
```
sudo aa-complain cupsd
```

If that doesn't take care of the issue, can you post the contents of /var/log/cups/error_log for us?

Thanks :)

---

### Post by chitragurung on 2009-10-10
when I browse the network it says printer is connected. In the status it says Idle. When I send printing command it does not print.

---

### Post by swoody on 2009-10-12
And when you attempt to print, you are making sure that you select the networked printer in the printing options before selecint 'Print'?

---

### Post by chitragurung on 2009-10-12
Yes I  Did but it does not work

---

### Post by swoody on 2009-10-12
Have you also tried hooking the printer up directly to the computer you're trying to print from? Also, take a look into the [Debugging Printing Problems]("https://wiki.ubuntu.com/DebuggingPrintingProblems") wiki page.

If you make it through that wiki page without any luck, can you post the contents of /var/log/cups/error_log for us?

---

### Post by chitragurung on 2009-10-13
When I do troubleshooting I found the following message.

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8db34e0>,
 'cups_instance': None,
 'cups_queue': 'SamsungS',
 'cups_queue_listed': True}
Page 2 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': ''}
Page 3 (Print test page):
{'test_page_job_status': [], 'test_page_successful': True}
Page 4 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': ''}

When I do the following 

chitra@chitra:~$ $ lsmod | grep usb
bash: $: command not found
chitra@chitra:~$  lsmod | grep usb
hci_usb                16540  0 
bluetooth              60772  5 rfcomm,l2cap,hci_usb
usbhid                 32256  0 
hid                    38912  1 usbhid
chitra@chitra:~$ lpinfo -v
network socket
network beh
direct hal
direct hpfax
direct hp
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb
chitra@chitra:~$ cupsctl LogLevel=debug 
chitra@chitra:~$ "cancel -a"
bash: cancel -a: command not found
chitra@chitra:~$ cancel -a
chitra@chitra:~$ /etc/cups/cupsd.conf
bash: /etc/cups/cupsd.conf: Permission denied
chitra@chitra:~$ /etc/cups/cupsd.conf
bash: /etc/cups/cupsd.conf: Permission denied
chitra@chitra:~$ 
chitra@chitra:~$

---

### Post by chitragurung on 2009-10-13
Here is the messages when I do troubleshooting again


Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86f9120>,
 'cups_instance': None,
 'cups_queue': 'SamsungS',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://ETI/COUNTER/SamsungS',
                       'printer-info': u'Samsung SCX 4x21F Series',
                       'printer-is-shared': True,
                       'printer-location': u'chitra',
                       'printer-make-and-model': u'Samsung SCX-4x21 Series',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to start filter "rastertosamsungspl" - No such file or directory.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135236,
                       'printer-uri-supported': u'ipp://localhost:631/printers/SamsungS'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "rastertosamsungspl" - No such file or directory.',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(29, 'SamsungS', 'Test Page')],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "rastertosamsungspl" - No such file or directory.',
 'printer-state-reasons': 'none'}

---

### Post by swoody on 2009-10-13
> **chitragurung said:**
> chitra@chitra:~$ /etc/cups/cupsd.conf
bash: /etc/cups/cupsd.conf: Permission denied
This is a config file, if you are trying to open it, you would need to run:
```
gksu gedit /etc/cups/cupsd.conf
```

> **chitragurung said:**
> Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to start filter "rastertosamsungspl" - No such file or directory.',
 'printer-state-reasons': 'none'}

This seems like you are just missing the 'rastertosamsungspl' filter. Do you still have the original CD that came with the printer? You should be able to pull the filter from there to your computer. On the CD, it *should* be listed under:
```
/SAMSUNG_LBP/Linux/x86_64/at_root/usr/lib64/cups/filter
```
or 
```
/SAMSUNG_LBP/Linux/i386/at_root/usr/lib/cups/filter
```

For the above, pick either i386 or x86_64 depending on what version of Ubuntu you are running. You have to navigate to that to make sure it's there, and then copy it to:
```
/usr/lib/cups/filter
```
Then shut off your printer, and restart it. Hopefully this should work for you. If you don't have the CD, or if you encounter some kind of problems, please let us know :)

---

### Post by chitragurung on 2009-10-13
hello,

I have printer drivers copied to my desktop. But I do not know how to install it.

I found those files in my notebook when browse chitra than desktop than cdroot and so on but I do not know how to copy to right directory ? Can you tell me code for me ?

---

### Post by swoody on 2009-10-13
Sure, to copy the files, the command would look like such:
```
sudo cp /path/to/CD/file/ /path/to/copy/to/
```
Just change the directories to the proper directory on the CD, and then the second one to the directory that you need to copy it to on your computer :)

---

### Post by chitragurung on 2009-10-13
I try to do but got the following error

chitra@chitra:~$ sudo cp /home/chitra/desktop/cdroot/linux/i386/at_root/usr/lib/cups/filter/ /fylesystem/usr/lib/cups/filter/copy/to/
[sudo] password for chitra: 
cp: cannot stat `/home/chitra/desktop/cdroot/linux/i386/at_root/usr/lib/cups/filter/': No such file or directory
chitra@chitra:~$ sudo cp/chitra/desktop/cdroot/linux/i386/at_root/usr/lib/cups/filter/to/cd/files/ /filesystem/usr/lib/cups/filter/to/copy/to/
sudo: cp/chitra/desktop/cdroot/linux/i386/at_root/usr/lib/cups/filter/to/cd/files/: command not found
chitra@chitra:~$

---

### Post by chitragurung on 2009-10-13
I have found files at following directory

/home/chitra/desktop/linux/i386/at_root/usr/lib/cups/filter

need to copy

I think

filesystem/usr/lib/cups/filter

I do not know how to do ?

---

### Post by chitragurung on 2009-10-14
Finally, I set upped my Samsung Scx 4521 F network printer as follows.

[http://ubuntuforums.org/showthread.php?t=1057344&highlight=setting+samsung+scx+network+printer](http://ubuntuforums.org/showthread.php?t=1057344&highlight=setting+samsung+scx+network+printer)

---

### Post by swoody on 2009-10-14
Excellent, so it's running fine now? :)

---

### Post by chitragurung on 2009-10-14
now running well, printing well. But I still have to fix the CDMA wireless usb modem.

---

### Post by swoody on 2009-10-15
Well if the wireless issue isn't related to the printing issue, I would recommend to create a thread about it in the Networking section, and then mark this thread as [SOLVED]. You can do that in the top-right of this page by clicking on 'Thread Tools' and then selecting 'Mark as solved' :)

---

