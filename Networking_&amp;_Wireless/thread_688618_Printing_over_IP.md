---
title: "Printing over IP"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-02-05
This is getting frustrating...

I'm trying to get an Edubuntu server version 7.10 to print to a printer connected via network (not samba, just network)

The printer is located at ip: 192.168.10.21 and uses port: 9100

Windows computers on the networks are having no problem.

Any suggestions / guidelines?

---

### Post by Cope57 on 2008-02-05
Maybe installing CUPS, and using [http://localhost:631/](http://localhost:631/)
Instead of port 9100, which is used for Windows 2000 servers maybe?

---

### Post by rickyjones on 2008-02-05
> **Geran said:**
> This is getting frustrating...

I'm trying to get an Edubuntu server version 7.10 to print to a printer connected via network (not samba, just network)

The printer is located at ip: 192.168.10.21 and uses port: 9100

Windows computers on the networks are having no problem.

Any suggestions / guidelines?

What printer? Did you configure the printer in CUPS? Printing over IP is no issue, I do the same thing at my location. What the problem might be is that your computer needs to know about the printer, and needs the driver loaded. Hence, CUPS.

-Richard

---

### Post by tgalati4 on 2008-02-05
Some printers have a web interface to set up configuration.

What happens when you put 

[http://192.168.10.21:9100](http://192.168.10.21:9100)

in a browser?

If it's an HP, then it should work as I have set up several to print over IP including through firewalls from remote locations.

You should set up cups as suggested and share with us the printer model.

---

### Post by Geran on 2008-02-05
Thanks a lot for the help so far guys.

I'm trying out a new driver, not sure if the old one was ok.

The printer is a Xerox Work Center Pro 123. Can anyone tell me which of the options presented in the printer set up menu is the best to follow?

---

### Post by Geran on 2008-02-05
Accessing the printer in the browser.. not ok. But this is to be expected, since I am trying to set up this printer across a VLANs. Our VLAN system only has rules allowing printing open right now, such as 9100 631 and snmp.

---

### Post by tgalati4 on 2008-02-05
Once you set up CUPS on Edubuntu (there are several tutorials in the forums search CUPS) it will set up a /etc/cups/printers.conf that looks something like:

# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2007-07-23 10:03
<DefaultPrinter OfficeJet-7110>
Info General Business Color Printer
Location Terry's Office
DeviceURI socket://192.168.1.118:9100
State Idle
StateTime 1185210232
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

Some Xerox printers use an HP print engine and possibly an HP JetDirect network driver, so you may have to do a google search on your printer to find the correct driver.  I assume that you have checked

[http://cups.org/ppd.php?L366+I0+T+Qxerox](http://cups.org/ppd.php?L366+I0+T+Qxerox)

I'm not sure what the differences are between a Work Center Pro 420 in the link above and your  Pro 123.  If it handles PCL6 then you could set it up as a RAW device and give it a generic PLC6 driver.

---

### Post by Geran on 2008-02-05
Alright, thanks a lot, I'll have to try this tomorrow.

---

### Post by Geran on 2008-02-05
Alright, thanks a lot, I'll have to try this tomorrow.

The example of printers.conf that you have posted, is that your own configuration?

---

### Post by tgalati4 on 2008-02-05
Yes, it's created automatically when you add a printer through CUPS.  The trick is to pick the appropriate driver.  The IPP protocol (port 9100) is pretty simple, but the printer has to know what to do with the data stream.  In a mixed printing network, you don't have the option to set the printer to PCL6 mode since Windows will use the Xerox driver.  If your printer supports postscript, then you could set it up as a generic postscript printer for Linux users.

At my previous job, we had a Xerox Work Center Pro (I don't remember the model) and it was an HP engine using PCL6 protocol.  I guess Xerox found it cheaper to buy HP engines than build their own for small business printers.  Of course, it had a Xerox price.

---

### Post by halitech on 2008-02-09
download the driver from here

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=WCP123_WCP128&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=WCP123_WCP128&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

extract the files, go into add a printer (System - Administration - Printing), select Network, put in just the IP address of the machine, click install driver and browse to where the files are located and slect the PPD file and then you should be good to go. 

To make sure you can get to the machine, open a browser and put in just the IP address (no 9100) and it should load the CWIS page for the machine. If it doesn't, something is blocking you.

hth

---

