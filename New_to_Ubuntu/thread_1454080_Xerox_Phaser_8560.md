---
title: "Xerox Phaser 8560"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by jugglingphil on 2010-04-14
Hi 
I'm using Ubuntu 9.10 and have a new printer, Xerox Phaser 8560. I can print to it from Windows, and from CentOS 4.8, but it doesn't work from Ubuntu!

In CentOS queue is set to lpd://xerox/raw
If I set the queue the same in Ubuntu, send job,  Status: Processing - Not connected? then after a few minutes get Printer 'Xerox-Phaser-8560': 'com.apple.print.recoverable'.

From CentOS&Windows can ping the printer's IP address (fixed) but can not from ubuntu? What could be stopping it? All devices are on the same network.

Has anyone got this printer working from Ubuntu, it's really starting to drive me mad now!

---

### Post by opossumjack on 2010-04-14
Did you try downloading the CUPS ppd for the printer from the [Xerox support site]("http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=1&prodID=8560&Family=Phaser&ripId=&langs=English%20%28US%29&plats=Linux&Xtype=download&uType=")?

---

### Post by jugglingphil on 2010-04-14
Thanks for response

Yes tried the Xerox download
Also tried, path being 
socket://xerox ip address:9100
ipp://xerox ip address/ipp/

Add New Printer - Network Printer - Find network printer - enter host ip address and find, doesn't find it.

I'm certain it has something to do with the fact that I can't ping it from Ubuntu, but can from Windows and CentOS.

---

### Post by halitech on 2010-04-14
what is the ip address of the xerox printer and the ubuntu computer? is the printer connected to a router or another computer?

---

### Post by jugglingphil on 2010-04-14
The problem is my wireless network. 

Printer has detected fine when I connect with cable (as Windows and CentOS)! Can't believe I didn't notice this before!!!
 
Installed printer easily in Ubuntu now, it finds printer using LPD via DNS-SD

Thanks to all.

---

### Post by opossumjack on 2010-04-14
You are welcome... Happy to see you solved your problem.. 

Have a good day

---

