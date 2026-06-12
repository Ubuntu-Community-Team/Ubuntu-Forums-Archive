---
title: "How to configure ubuntu to connect to my printer via dlink wireless print server"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by jae2647 on 2007-02-18
Hi.  I have my printer  connected to a D-Link wireless print server (model DPR-1260).  I'd like to configure Unbuntu to print on this printer via the print server but I am having a hard time setting it up.  Can you tell me how to go about doing this?  Thanks!

---

### Post by beanworks on 2007-02-18
Is the printserver the only wireless item you have (no wireless router?).

You need the IP address of the printserver, and the drivers for the printer (which you can get from the printer's CD, or from the manufacturer's web site.

Go to Printers in the System menu and double click on the New Printer icon to get to the Add A Printer wizard.  Select the Network Printer option (CUPS should be fine) and put in the printer's IP address.  The next screen will ask for the driver.  Click the Install button to find the driver (this is where the CD comes in handy).  

Once you have the driver identified in the wizard, (going on memory here) you should be able to finish the wizard and print a test page.

---

