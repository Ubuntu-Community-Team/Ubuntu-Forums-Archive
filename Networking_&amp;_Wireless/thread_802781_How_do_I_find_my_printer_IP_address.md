---
title: "How do I find my printer IP address?"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by xl_cheese on 2008-05-21
I got a new printer and want to use it on the network.  So I plugged it into my router.

How do I find the printer IP?  Seriously, I've googled for 15 minutes.

---

### Post by solitaire on 2008-05-21
What's the Make & Model?

There should have been a disk with the Printer to install drivers.
Their should be a program to talk to the printer over the network to set it up.

Otherwise open "Network Neighbourhood" there should be an option to browse the network. open that and see if the printer pops up there. Their my also be an option to browse the network for a printer.

---

### Post by xl_cheese on 2008-05-21
It's a dell 1320c.  I was able to get it working in windows via usb connection.  

However when I try to do it over the network I don't see it anywhere.  Not even with the windows install cd.

---

### Post by jrusso2 on 2008-05-21
Different printers do it differently but with the HP there is usually in the menu is a key or combination of  buttons that will  print out the network configuration

---

### Post by Iowan on 2008-05-22
[http://delltalk.us.dell.com/supportforums/board/message?board.id=sw_linux&message.id=13733&query.id=179798#M13733]("http://delltalk.us.dell.com/supportforums/board/message?board.id=sw_linux&message.id=13733&query.id=179798#M13733")

> Connect printer to network with dhcp server (cable router, etc...).Power on printer.When printer is ready, press and hold printer "Continue" button to print settings pages to get printers DHCP assigned IP address.

---

### Post by Pioneer5000 on 2009-01-17
I have the same problem I need to find my Printer IP address, I have a Brother DCP-130C I cant find anything that just gives me a simple answer to this, its so annoying.

---

### Post by t1m on 2010-02-05
I found my (Brother MFC-7440N) printer IP on the printer's menus...try browsing them to see? (It's a 196.254... one, so I'm wondering if it has another one for the local network?)

---

### Post by doas777 on 2010-02-05
can always scann your network to find the live IPs with somthing like this:
[http://forums.jinx.com/topic.asp?TOPIC_ID=57110](http://forums.jinx.com/topic.asp?TOPIC_ID=57110)

nmap is prolly the best tool for the job, but it has a steep learning curve.

---

### Post by edc80 on 2011-02-06
My printer/scanner is a Brother MFC-9840CDW.  I found its IP address by printing a report called "User Settings List."  It's printed by navigating the menus on the printer itself:

   Menu Button
   6. Print Reports
   5. User Settings
   Start Button

On my printer, its IP address was in the report box that begins with the words WLAN ENABLE.  The address was in the sixth line of this box on the printed report.

With thanks,
-EdC
---
To Jesus through Mary

---

### Post by cjhabs on 2011-02-06
> **xl_cheese said:**
> I got a new printer and want to use it on the network.  So I plugged it into my router.

How do I find the printer IP?  Seriously, I've googled for 15 minutes.

They often are configured for DHCP so that they work out of the box - you can log onto your router - or whatever is your dhcp server - and find the printer there, with its ip address. Usually you can then hit it via http and configure it.

---

