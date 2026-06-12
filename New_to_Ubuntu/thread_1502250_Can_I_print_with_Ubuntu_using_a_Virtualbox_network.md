---
title: "Can I print with Ubuntu using a Virtualbox network?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Old Newville on 2010-06-05
I have a Dell All-In-One printer that only works with Windows. There are no Ubuntu drivers available that seem to work. 

I'm running Ubuntu 10.04 and Windows XP as a guest in Virtualbox. Is it possible to network the 2 so that Ubuntu can use the Windows printer?

Any suggestions would be appreciated.

---

### Post by gsocker on 2010-06-05
Not easily. Windows printer sharing does all the processing on the computer you are printing from, not the computer the printer is connected to. About the only way that I can think of would be to print to a PDF in Ubuntu, then open it up in Windows and print the PDF.

---

### Post by Old Newville on 2010-06-05
Thanks for the reply. I guess I need to scan Ebay for a good AIO printer that works with both Windows and Ubuntu!

---

### Post by gsocker on 2010-06-07
Currently, your best choices are Epson or HP, at least for inkjets. Pretty much all of these should be supported, although it would be a good idea to check before buying one.

---

### Post by davidmohammed on 2010-06-07
> **Old Newville said:**
> I have a Dell All-In-One printer that only works with Windows. There are no Ubuntu drivers available that seem to work. 

I'm running Ubuntu 10.04 and Windows XP as a guest in Virtualbox. Is it possible to network the 2 so that Ubuntu can use the Windows printer?

Any suggestions would be appreciated.

Yes - should be straightforward. Lets assume your ubuntu picks up its IP address from a wireless router (i.e. your router is acting as a dhcp server - most wireless routers do this)

 Make sure your Windows guest is sharing its printer (see this snippet I plagiarized elsewhere):
"To share the printer, I opened the Printers and Faxes folder on the computer that was connected to my printer.
To open the Printers and Faxes folder
•	
Click Start and then click Control Panel.
•	
Click Printers and Other Hardware, and then click Printers and Faxes.
•	
In the Printers and Faxes folder, I clicked the printer's icon and, in the tasks pane, I clicked Share This Printer.
•	
I opened the printer's Properties dialog box, and clicked on the Sharing tab.
•	
I clicked Share Name, and then clicked OK."

then check in windows that it has picked up an ip address from your wireless router (check in network connections - properties)

Then in ubuntu add a printer - `network printer - windows printer via samba.  Browse to your printer share you created above.

---

### Post by Old Newville on 2010-06-07
Thanks for all the replies. That's helpful to know that a wireless router could solve the problem. My printer does have a wireless card, but right now I'm using a USB cable. So, either I'm buying a new printer or a wireless router!

I don't have the link handy, but someone else on the forum said he uses a Brother printer and the main attraction there is he's only spending $3 per cartridge. Dell charges more than $30. No wonder I don't want to print anything!

---

### Post by Logic Squirrel on 2010-06-07
I have a dual boot with 10.04 and vista and both can use HP photosmart i will add a linky below to the printer i use.

[http://www.bestbuy.com/site/HP+-+Photosmart+Premium+Wireless+Printer/+Copier/+Scanner/9472251.p?id=1218110871158&skuId=9472251](http://www.bestbuy.com/site/HP+-+Photosmart+Premium+Wireless+Printer/+Copier/+Scanner/9472251.p?id=1218110871158&skuId=9472251)

[IMG]http://img202.imageshack.us/img202/3434/screenshotoyr.png[/IMG]

---

### Post by gsocker on 2010-06-07
Old Newville, 
  A wireless router won't help. The problem isn't getting the Linux box to see the printer; the problem is getting the Linux box to generate printer data in a format the printer understands. It's a design difference.  In Linux, the computer connected to the printer formats the document for the printer. In Windows, each computer using the printer must have a driver installed, as all the server does is send the data to the printer. Dell printers are generally rebranded Lexmarks, which are not known for their Linux compatibility or cheap ink. Before you buy, it's a good idea to check linuxprinting.org and see if people have had success. If you're new to Linux, it is usually a good idea to check compatibility before purchase,  as you can't assume there will be a driver for it the way you can in Windows.

---

### Post by davidmohammed on 2010-06-08
Yes agree - my previous post is wrong in several respects.  However I did get a similar non linux printer (lexmark x5945) working, printing from ubuntu via windows with ghostscript installed.

[This post]("http://www.dragonblogger.com/ubuntu-linux-printing-to-a-non-post-script-printer/") explains what instructions I followed.

---

