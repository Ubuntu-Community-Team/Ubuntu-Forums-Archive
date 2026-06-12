---
title: "HOWTO: Print from Mac OS X to Ubuntu over the network"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by Limulus on 2007-06-14
I just posted this to [https://help.ubuntu.com/community/NetworkPrintingFromMacOSX](https://help.ubuntu.com/community/NetworkPrintingFromMacOSX)

---
Printing from Mac OS X 10.4 (Tiger; tested with 10.4.9) to a printer attached to Ubuntu 7.04 (Feisty) is not difficult .

On the Ubuntu side, first verify that the printer is installed and working.

Then go System -> Administration -> Printing. Jot down the name of your printer(s) as you'll need this info later. In the menu, select Global Settings and check Share Printers. Note the warning about opening a port. Preferably you're doing this on a local network behind a firewall.

You can verify that port 631 is open by going:System -> Administration -> Network Tools Determine your (local) IP Address (e.g. 192.168.0.100) by selecting the Devices tab and picking the right Network device. Write it down too. Then select the Port Scan tab and scan your IP address. The service on port 631, "IPP", is short for "Internet Printing Protocol".

So far so good; now go to the Mac.

Install the Mac version of the printer driver for your printer or if it can use Postscipt or what have you, then you'll be using that. Run the Printer Setup Utility. Select Add. Select IP Printer. The protocol is IPP. The Address is the Ubuntu machine followed by :631 (e.g. 192.168.0.100:631). The Queue is printers/put_your_printer_name_here For Print Using, if you installed a driver, select it.

To test your printer, use a web browser on your Mac to go to [http://localhost:631/printers](http://localhost:631/printers) (you will need to input an admin username and password). The Device URI should read something like [http://192.168.0.100:631/printers/your_printer_name_here](http://192.168.0.100:631/printers/your_printer_name_here) Select Print Test Page.

Hopefully it worked for you too :)
---

---

### Post by butcher99 on 2007-08-19


 I can print just fine from the localhost:631 but when I attempt to print anything from the mac it sends 100% then printing stops.  
  There is no error I can find, it just stops.   
any suggestions?

---

### Post by tadtoll on 2007-09-01
Thank you very much for the straight-forward tutorial.

I hadn't realized I needed "printers/" in the queue form and was only putting the printer name in there.

Also did not know about the web app on the Mac. Thanks for that too.

---

