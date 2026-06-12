---
title: "mfc 4800 printer on network"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Papa-san on 2009-07-29
I have a desktop box at the site where my printer is. This system is running Ubuntu 8.04 alongside Windows XP SP2. when I hit 'print' it acts like it's doing something, but never get a print, nor do I get any error. 
I run the last stable LTS version of Ubuntu in hopes that I can get things running the way I need them to, and then actually keep them working for a few years...
Currently, my Brother MFC 4800 laser printer is hooked up to that system. Whenever I need to print something, I have to shut down and boot up in WinXP. This is a real pain, and I would like to fix it. 
My ladies, (Wife and 2 daughters) all have WinVista boxes connected via a wireless router, and I would like for us all to be able to print at any time from any of the systems. (2 of the laptops are also dual boot with 8.04, but as there are problems, they use the Windows OS's almost exclusively.)
I have found several threads in which the OP has the desktop & printer working together, but not the network, I'll follow those once I get this working, but for now, I have to try to get the basics working.

---

### Post by LookTJ on 2009-07-29
Does the Brother printer have an rj 45 port? If so, you could hook it up to the router and use an IP based setup.

If not, you can use Samba in Ubuntu, though I'm not sure how to set that up.

:)

---

### Post by Papa-san on 2009-07-29
Don't know...
Not sure what an "RJ 45 port" is, but I'll take a look!

---

### Post by LookTJ on 2009-07-29
> **Papa-san said:**
> Don't know...
Not sure what an "RJ 45 port" is, but I'll take a look!
It's that port that you plug into with a network cable

:)

---

### Post by plucky on 2009-07-30
Have you installed the drivers for the MFC-4800?

Open **Synaptic Package Manager** and search for **MFC-4800** and it should find the Cupswrapper and LPR drivers.Install both.

Then turn on printer and go to **System > Administration > Printing** and select new printer.The system should find and install the printer when you select the correct driver.

Then set it as default and try a Test print.If that works,then

To Network the printer,**System > Administration > Printing > Server > Settings** and tick the box to "publish shared printer".The printer should then be available on the Network.


Good Luck

---

### Post by Papa-san on 2009-08-04
I went through the Synaptic steps and installed both programs (as well as the dependencies) and nothing happened. It acts like it is working, but the printer never fires up.
I went through the troubleshooting process, and, though it didn't find a solution, I got this report:```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8e2fd20>,
 'cups_instance': None,
 'cups_queue': 'MFC-4800',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'MFC-4800',
                       'printer-is-shared': True,
                       'printer-location': u'john-desktop',
                       'printer-make-and-model': u'Brother DCP-1200 Foomatic/ljet2p',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143364,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MFC-4800'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(7, u'Job completed.')],
 'test_page_job_id': [7],
 'test_page_job_status': [(7, 'MFC-4800', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

```
It means very little to me, but I hope somebody can tell me if they see anything off...

---

### Post by plucky on 2009-08-05
```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8e2fd20>,
 'cups_instance': None,
 'cups_queue': 'MFC-4800',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'MFC-4800',
                       'printer-is-shared': True,
                       'printer-location': u'john-desktop',
                       [color=red]'printer-make-and-model': u'Brother DCP-1200 Foomatic/ljet2p',[/color]
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143364,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MFC-4800'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(7, u'Job completed.')],
 'test_page_job_id': [7],
 'test_page_job_status': [(7, 'MFC-4800', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
```


See above in [color=red]red[/color]
I don't have your printer,but I think you have the wrong driver installed as that seems to be the default printer driver when you attach a new printer.

Open **System > Administration > Printing** select your printer and search for a new driver.

According to [Open Printing Database](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC_4800) your printer driver should be HL7x0.

Also for troubleshooting using the CUPS interface,open Firefox and put ```
http://localhost:631/
``` into the address bar will open the CUPS interface.

Good Luck

---

### Post by Papa-san on 2009-08-05
LOL...
Thanks... That was a very 'Brilliant' thing...
I didn't see my printer in the list at first. 

I have it working now for me to print from my Ubuntu desktop. I cannot get anything working on the Vista boxes that will allow them to see this computer (or the printer) on the network, though...

---

### Post by Papa-san on 2009-08-20
Just got around to posting again.

I can print a 'test page' but nothing else will print from Open Office or any of my text editors. Nor can I print a web-page or anything. Somehow my configuration has to be wrong, and everything I have tried gives me no love.

Anyone have ideas as to where to start checking? It works OK in Windows XP, but it's such a pain to have to save to my thumb-drive and re-boot whenever I need to print anything.
I'll check in a bit later to see if there are any ideas!
Thanks!

---

### Post by plucky on 2009-08-21
> **Papa-san said:**
> Just got around to posting again.

I can print a 'test page' but nothing else will print from Open Office or any of my text editors. Nor can I print a web-page or anything. Somehow my configuration has to be wrong, and everything I have tried gives me no love.

Anyone have ideas as to where to start checking? It works OK in Windows XP, but it's such a pain to have to save to my thumb-drive and re-boot whenever I need to print anything.
I'll check in a bit later to see if there are any ideas!
Thanks!

Do you have "lpadmin" privileges for your account? Open a terminal and post output of the command ```
id
```
If not,add yourself using the "user and groups" GUI then logout and log back in to gain the privilege for your account.Also check the paper size is set up correctly for the printer as this can cause the printer to not print if it is incorrect.
That is all I can think of to get you going.

Good Luck

---

### Post by Lavaeagle on 2009-08-21
I had a similar problem where at first i could send the document to the printer but wouldn't print, what i ended up doing.

Printing from my computer to another computer just through a router, worked with computer off.


[LIST=1]
[*]Uninstall the printer
[*]Reinstall as a network printer
[*]System > Administration > Printing
[*]Click add printer button
[*]Network printer > Windows Printer Samba
[*]Browse
[*]Go through Network Groups till you find you're printer.
[*]Select Make Model
[*]Print test page
[*]See what happens.
[/LIST]
My printer just had to be plugged into the network to work.
Also you may need to forward the ports that your printer is using to get through.

---

### Post by Papa-san on 2009-08-22
Here is the results of 'id':
```
john@john-desktop:~$ id
uid=1000(john) gid=1000(john) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(john)
john@john-desktop:~$ 


```I am assuming that I have the proper rights because it's listed. Let me know if my assumption is wrong, please!

---

