---
title: "Print Server/Network Printing"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-07-22
Hello All,
I have a print server set up in my home.  The printer is connected to a router that I have upstairs via a print server.  The router is a netgear wnr3500 and the print server is a wps54g.  The way we have it set up for windows was through a disk that had a wizard on it.  How do I even begin to set this up to print wirelessly through ubuntu??

Thanks!

---

### Post by jsweet007 on 2009-07-23
you will need the ip address of the print server. and then look in to "cups" .
there is a printer or printing services in the admin section of your toolbar

---

### Post by cariboo on 2009-07-23
The printer should show up in System-->Administration-->Printing.

---

### Post by LookTJ on 2009-07-23
Depending on your printer, there are about 3-4 ways of setting up a network printer.  You need the printer's IP, know the printer model(so you know what driver to look for)

I will also link you to CUPS guide on setting up network printers: [http://cups.org/documentation.php/doc-1.4/network.html](http://cups.org/documentation.php/doc-1.4/network.html)

---

### Post by rideburton56 on 2009-07-23
I ended up falling asleep last night and not getting around to this, and now I am at work.  I will report back with what I have found.  I already have the printer set up on windows, so I imagine that would be a good starting point for figuring out the IP?

---

### Post by rideburton56 on 2009-07-23
My Print Server IP address is 192.168.1.2
My Printer is  Dell Laser Printer 1700

I am in printing and went through the troubleshooting guide for adding a printer, and it that isnt getting it done.  Any Suggestions?

---

### Post by scrooge_74 on 2009-07-23
Here is the detail about your printer

[http://www.linuxprinting.org/show_printer.cgi?recnum=Dell-1700](http://www.linuxprinting.org/show_printer.cgi?recnum=Dell-1700)

---

### Post by rideburton56 on 2009-07-23
So based on that post, it seems that I should be looking for the PCL6 Driver... It doesnt really say much about networking that printer.  Is there something else I am missing???  I am really not good at networking and editing config files (which the cups page is alluding to) and I know you guys are trying to help, but in the words of michael scott... explain it to me like im a 6 yearold..... ok..... now explain it to me like im a 5 yearold. :)

---

### Post by rideburton56 on 2009-07-23
Sadly, until further notice, I am going to chalk this one up to 'not possible'

---

### Post by alphacrucis2 on 2009-07-23
> **rideburton56 said:**
> Sadly, until further notice, I am going to chalk this one up to 'not possible'

Under Windows go into control panel - printers then:

Right click on the printer icon and select properties. Select the ports tab and see what port id and port description is configured in windows - report back here. Shouldn't be hard to figure it out. Most of these print servers support multiple protocols in any case so I would be surprised if it doesn't talk LPR/LPD, HP IP/Jet Direct, IPP etc.

---

### Post by scrooge_74 on 2009-07-23
Look if you use the printer option under System>ADmin>Printer you tell it to look for printers that are on the network, in there you will give it the IP your print server is using.

You can also type on your browser (my prefer way) localhost:631  that will take you to the webconfig for the CUPS server. There you can add printers make changes, etc.

Is a very good nice interface

---

### Post by rideburton56 on 2009-07-23
I guess one thing that I am not making clear is that nothing is showing up in printing other than the PDF writer.  I try to go into network printers and I am not having any luck with the the IP address I have gotten.

---

### Post by rideburton56 on 2009-07-24
More info from windows
Port is IP_LKD5862B_P1
IP 192.168.1.2
Protocol LPR
Queue P1
Standard TCP/IP Port

In the XP port config page, it had two options... raw or LPR.
LPR was checked off
Below that was Raw port 515, but that was all greyed out, and below that it had the LPR queue.  

I also have this from the troubleshooter.

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [('PDF', None)], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.1.2', 'remote_server_name': ''}
Page 5 (Check network server sanity):
{'remote_server_connect_ipp': True,
 'remote_server_cups': True,
 'remote_server_name_resolves': ['192.168.1.2', '192.168.1.2', '192.168.1.2'],
 'remote_server_try_connect': '192.168.1.2'}
Page 6 (Choose network printer):
{'remote_cups_dests_available': [('PDF', None)],
 'remote_cups_queue_listed': False}
Page 7 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}


Help!

---

### Post by LookTJ on 2009-07-24
does this work with a generic pcl6 driver?

```

lpd://*192.168.1.2*/[I]P1

```


[/I]

---

### Post by rideburton56 on 2009-07-24
am i pasting that into the add network printer/ LPR interface?

---

### Post by LookTJ on 2009-07-24
> **rideburton56 said:**
> am i pasting that into the add network printer/ LPR interface?If I interpret your question correctly, then yes

LPD is the same as LPR as far as I know :)

---

### Post by rideburton56 on 2009-07-24
IT WORKED!!!!!

So what I did in 9.04 was admin/printing/add new/other

after clicking on other, the left side of the page was asking for a URI address, i pasted that baby in there and we are all set to go.  I did a test page and also a hopstop directions page just to be safe.  

YOU GUYS ARE THE BEST!!!!

I honestly cant thank you enough ( i still miss the thanks option from the forums).  I was convinced that if windows can do it, linux can do it, and you guys came through big time.  It just reinforces (for me), what this whole open source community is all about.  Someday ill be on the other side of this convo maybe!!


PS.  @looktj, if you want a good laugh, I originally posted that lpd address in the terminal.... har har har

---

### Post by LookTJ on 2009-07-24
> **rideburton56 said:**
> IT WORKED!!!!!

So what I did in 9.04 was admin/printing/add new/other

after clicking on other, the left side of the page was asking for a URI address, i pasted that baby in there and we are all set to go.  I did a test page and also a hopstop directions page just to be safe.  

YOU GUYS ARE THE BEST!!!!

I honestly cant thank you enough ( i still miss the thanks option from the forums).  I was convinced that if windows can do it, linux can do it, and you guys came through big time.  It just reinforces (for me), what this whole open source community is all about.  Someday ill be on the other side of this convo maybe!!


PS.  @looktj, if you want a good laugh, I originally posted that lpd address in the terminal.... har har har
Thanks for providing the info from XP's configuration. That's what made me give the LPD address.  

from [URL="http://cups.org/documentation.php/doc-1.4/network.html"]CUPS
[/URL]
```
lpd://*ip-address-or-hostname*/[I]queue
```

All the best!
T:)
[/I]

---

### Post by scrooge_74 on 2009-07-24
Good to hear you got it solve. 

First time I tried to add my printer using 2 linux machines I got even more impressed, I just had to tell the PC that had it attach to share it over the network and the other one picked it up right away with no need to install or config anything

---

