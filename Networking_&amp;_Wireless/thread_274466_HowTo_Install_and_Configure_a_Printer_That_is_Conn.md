---
title: "HowTo: Install and Configure a Printer That is Connected to Your Network (router)"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by NavmaN on 2006-10-09
**[SIZE="3"]Valid for Ubuntu 6.06[/SIZE]**
***Also* How to fix 'CUPS server could not be contacted'**

Hello,

I have just begun using Ubuntu (switched from windows) and have found Ubuntu a great alternative.

Anyway, I have been having problems with printing lately, but recently fixed them, so I thought I would make a step-by-step guide on how to install a printer that is connected wirelessly to your router. Let me just make it clear that this is meant for a printer that is connected to your router, but some of the earlier steps can fix other problems mentioned above.

Onto the Howto:

1.) System>Administration>Printing *If you are taken to a dialog that has an icon called new printer, proceed to step 2.* **If you receive the error 'CUPS server could not be contacted' proceed to step 1a.**

1a) System>Administration>Synaptic Package Manager
1b) Search for 'cups' Just click search and enter 'cups' and hit enter.
1c) Look at all the packages that have their check boxes filled with green and click on the check box>Mark for Reinstallation
1d) Click apply and wait until it is finished reinstalling the packages.
1e) System>Administration>Printing
(If you are still getting 'CUPS server could not be contacted' make sure you are following all the steps, if it still doesn't work just post in this thread)

2.) Once the 'printers' program appears, double click 'New Printer'
Click network printer and choose what type of printer it is(i.e. HP is HPJetDirect, **you basically have to look in the manual of your printer but you can do trial and error if you don't know the correct option**, since there are only four options. 

3.) Enter the URI, which is the printer;s IP address. To find out your Printer's IP address you have to go to your router menu, which can be accessed usually by going to [http://192.168.0.1](http://192.168.0.1) or [http://192.168.0.0](http://192.168.0.0)
Note: Some routers differ, your router manual is sure to tell you the default IP, and if you've changed the IP you're probably experienced enough to know how to get into the router config menu.
Once you go to that web address (yes you access 'http://192.168.0.1 or htt[://192.168.0.0' with a web browser) it will ask you for your username and password, you should know that, but the default is usually **USRNAME:admin** and **PASSWD: blank(as in nothing)**
Now, you have to find something in your router menu like a client table, which will list the IP's connected to your router, the names of the things connected will also be listed (i.e. HP12345   192.168.0.105) If you don't see an entry that is you printer, **make sure your printer is on**.
Record that IP and put it into the URI field. If your printer is an HP leave the port at 9100, unless you knowingly have changed it. If it is a windows printer, you probably are trying to configure a work/office printer, in which case I am not experienced and you will have to ask your tech support guy. If you have a unix printer (very rare) you should be experienced enough. **Click forward in the 'add printer' dialogue**.

4.) Select manufacturer and model. It will give you recommended and suggested drivers. Find those drivers in synaptic (i.e. search for the names of the drivers it gives you) and make sure they are installed. If they aren't, install them. **Click forward in the 'add printer' dialogue**.

5.) In the description field you have to just make up a description of your printer, for example 'home printer' or 'HP blah blah'. In the location field, just enter the IP of the printer that you entered in the URI, in step 3.

Hope that helps you guys. This is my first post and first guide, so constructive criticism of my writing style, contents of the guide, etc. would be appreciated.

Thanks.

---

### Post by NavmaN on 2006-10-10
Please, anyone? Should I have just added this to the wiki?
Any bit of feedback would be appreciated.
Thanks

---

### Post by fedupwithwin on 2006-10-17
Thanks very much for the info.  I'm trying to set up Ubuntu to print on a networked HP printer.  The only problem I'm having is that my network is set up with DHCP IP addreses automatically assigned by the router.  So when your instruction say to type in a static IP address, this is where I say "AWWW, not again!!".  Nobody seems to have adequately this one question.  Do you have any idea how to handle this?

---

### Post by Iowan on 2006-10-17
Static lease from router - PM'ed response.

> or htt[://192.168.0.0'
Sorry to nitpick - typo.
There are a few more, but I doubt that's the kind of help you were looking for.

---

### Post by trilobita on 2006-10-19
Does this work for any type of printer? I thought that the printer had to be connected directly to one computer, which acts as a printserver?

---

### Post by somersetsimon on 2006-10-19
When you say 'printer connected to your router', do you mean via a print server? I have my printer connected to a print server via the parallel port, the print server is connected (wired) to the router and the router serves my computers wirelessly.

If I could get Ubuntu connected wirelessly I could start on the printing phase!

---

### Post by fedupwithwin on 2006-10-19
My printer is an HP 7310 - it connects directly to a Lynksys BEFSR41 router via an ethernet cable.  I do not use a dedicated print server.  The router is currently set up to automatically assign IP addresses to each of four devices on my network.  The problem I'm having, is that at any given time, the printer can have a different IP address.  Someone mentioned previously in this thread about an extended address lease setup on the router?  Please explain... I guess this is really a router setup issue but it seems relevant.

---

### Post by Doctoxic on 2006-10-22
Hi

Same problem for me - printer gets different IP each time.  Any way around this?

Thanks

Doc

PS I have a HP2575 - how do i tell whether i use :
CUPS (IPP)
Windows (SMB)
Unix (LPD)
JP Jet Direct

---

### Post by bigken on 2006-10-22
does the printers have a control panel where you manually asign an ip address to the printer :-k

---

### Post by bigken on 2006-10-22
> **Doctoxic said:**
> Hi

Same problem for me - printer gets different IP each time.  Any way around this?

Thanks

Doc

PS I have a HP2575 - how do i tell whether i use :
CUPS (IPP)
Windows (SMB)
Unix (LPD)
JP Jet Direct


Use unix LPD

---

### Post by Doctoxic on 2006-10-23
thanks

i'll have a another go

Doc

---

