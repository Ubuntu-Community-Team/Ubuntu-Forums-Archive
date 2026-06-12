---
title: "Help printing from Feisty to a Windows printer"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by timzak on 2007-06-09
Hi, I'm trying to set up a Windows printer over the network for my Ubuntu Feisty machine.  I successfully did this at work with a similar setup, but I can't get it working on my home computer.  At work, the Windows machine is using XP, at home I'm using Win2k SP4.  At work, we're on DSL with a Linksys router.  At home, I'm on cable with a D-Link router.  I didn't have to do anything special at work (didn't have to modify the samba.conf file at all), I just enabled sharing on the Windows printer, enabled "Detect LAN Printers" in Feisty, then went through the printer setup process.  At work, everything works fine.  At home, Feisty sees the Windows Network, sees the Windows machine, and even sees the Windows printer, but when I go to print, I hear the printer activate as if it's about to print, but nothing ever prints.  I eventually get a "Paused: job-hold-until-specified" message in the print window on Feisty.

The printer at work is an HP Deskjet 5650.  The printer at home is an HP Photosmart C3100.  In both cases, Feisty detects the model correctly and I use the default driver.  I'm not sure why I can't get it to work on my home network.  Can anyone help me?

Thanks.

---

### Post by timzak on 2007-06-10
*bump*...what's the secret to getting someone to help here?  I see some posts getting 47 replies as if everyone is jumping in to help them with their problem, but some posts hardly get any views, let alone replies to help.  

Did I forget to put on deodorant or something?  :D

---

### Post by timzak on 2007-06-10
I fixed it myself, so this thread can be closed.

Despite having no password on the Windows computer and no need to log in when booting up, I still needed to type in "Administrator" for the username in Feisty when setting up the printer.

---

### Post by DRHamp on 2007-06-11
Hi -- just did a search on the msg "Paused: job-hold-until-specified"  and came up with your post.

I upgraded to Feisty recently and just installed a printserver on my home network.  

All of the symptons I see are just as you described them -- and I get the same error -- and the print job doesn't print.

When I set up the printer, I did have to put in my administrator login and password (actually a couple of times) and I did that.

So, how did you get it to work?

Thanks in advance .... DRHamp

---

### Post by timzak on 2007-06-11
> **DRHamp said:**
> Hi -- just did a search on the msg "Paused: job-hold-until-specified"  and came up with your post.

I upgraded to Feisty recently and just installed a printserver on my home network.  

All of the symptons I see are just as you described them -- and I get the same error -- and the print job doesn't print.

When I set up the printer, I did have to put in my administrator login and password (actually a couple of times) and I did that.

So, how did you get it to work?

Thanks in advance .... DRHamp

Are you trying to print from Feisty to a Windows printer?  That was my situation.

The only thing I was doing wrong was when installing the printer in Feisty, I was not typing in "Administrator" under username to log into and access the Windows computer.  So (in Feisty) I'd go into the printer configuration and enable LAN printer.  Then I'd add a printer, select Network Printer, select Samba (Windows Printer), then it would ask me for the Windows username and password.  This was the step where I wasn't inputting anything and not getting success.  As soon as I typed in "Administrator" under username, things started working.  I believe it asks twice (once for the workgroup and once for the specific Windows computer).

Hope this helps.

---

### Post by DRHamp on 2007-06-11
Yes, I'm attempting to print to an HP5650 window printer.

I'll try using "Administrator" for the login -- I was actually putting in my Ubuntu administrator login and password

I'll try it and see what happens.  -- the printer is attached to a printserver, not to a windows pc...?

Well, that didn't do it ----  Removed the printer and reinstalled it -- using Administrator as login -- no change, still get the error.  

I can print to the printer from Windows XP with no problem.  -- I'm stuck at this point

---

### Post by farish on 2007-06-22
Timzak, thank you for posting this thread!  I was stumped on getting my HP OfficeJet 5610 working on a windows/Samba connection from my Feisty laptop.  Soon as I put in "Administrator" my problems were solved--it printed right off the bat.  You rock!  :KS

---

### Post by farlander on 2007-07-13
I've tried the "Administrator" thing to no avail.  I've tried using my own user name (Win).  I don't get an error message, it just sits there.  I also have an Officejet 5610.  The print job shows up on my windows machine but it doesn't print.  I can attempt to delete the job but it still remains.  I could delete the job before trying to enter a password but now it won't delete regardless of even a restart on my win machine.  

There must be an alternative to Gates!!!!

---

### Post by DRHamp on 2007-07-13
> **farlander said:**
> I've tried the "Administrator" thing to no avail.  I've tried using my own user name (Win).  I don't get an error message, it just sits there.  I also have an Officejet 5610.  The print job shows up on my windows machine but it doesn't print.  I can attempt to delete the job but it still remains.  I could delete the job before trying to enter a password but now it won't delete regardless of even a restart on my win machine.  

There must be an alternative to Gates!!!!

This is what worked for me:

I am now printing to the printserverr/network printer from Feisty and thought perhaps my update might help someone else.

Some further information regarding my environment. I basically have a windows network with several XP machines connected to a Linksys router. The printserver is also Linksys (WPS54GU2). The printer off of the printserver is an HP Deskjet USB connected to the printserver. I also have a Canon printer which is direct connected to one of the XP machines and is shared.

I could print to either printer from any XP machine.
I could print to the Canon Shared printer from Ubuntu
I could not print to the HP printer connected to the Linksys printserver from Ubuntu.

When trying to print to the printer on the Linksys printserver - I would get the message:
Paused: job-hold-until-specified

Over the past several days, I setup and removed this printer several time through the Ubuntu Admin interface as well as through the CUPs (localhost:631/) -- always setting the printer up as a windows / Samba printer.

Nothing worked. ........ but - here's the solution that worked for me:

Go through the normal "New Printer" setup

Printer Type: Select Network Printer
and in the drop-down window, select Unix Printer (LPD)
in the Host window - enter the ip address of the printserver/printer
in the Queue window - enter L1 if you're using a parallel printer, or L2 if your printer is usb connected.

This may not be a very elegant solution, but it works fine for me and the XP machines are unaffected.

I can't take credit for this solution - it was originally posted by jhuff in 2005 - here's a copy of his orig post:

---

