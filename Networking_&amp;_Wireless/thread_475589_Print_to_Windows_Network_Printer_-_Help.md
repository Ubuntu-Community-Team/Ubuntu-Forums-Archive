---
title: "Print to Windows Network Printer - Help?"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by DRHamp on 2007-06-16
Hopefully, someone has encountered this problem and has a solution.

I'm running Feisty, and have an HP Deskjet 5650 connected to a print server on my home network.  All of my Windows machines can print to it with no problem.
In Feisty, I can set up the printer and see it on the network and set it up as the default.  I can see and access windows shares on the network with no problem.

When I attempt to print (a test page, or from any application) I get the following error:

"Paused: job-hold-until-specified"

I have searched this forum and found at least 10 threads which reference this error.  It seems that it might be a "catch-all" message as the problems reported seem to happen it different environments.  I have however tried all of the suggested remedies with no success.

by the way, the printer works fine when connected directly to the fiesty laptop via usb.

I am pretty confident that this worked in Edgy, but am not sure of that.

I am a newbie Linux/Ubuntu user - so I sure that contributes to my inability to solve the problem.

I don't know where to turn next -- can anyone help?

---

### Post by DRHamp on 2007-06-19
I am now printing to the printserverr/network printer from Feisty and thought perhaps my update might help someone else.

Some further information regarding my environment.  I basically have a windows network with several XP machines connected to a Linksys router.  The printserver is also Linksys (WPS54GU2).  The printer off of the printserver is an HP Deskjet USB connected to the printserver.  I also have a Canon printer which is direct connected to one of the XP machines and is shared.  

I could print to either printer from any XP machine.
I could print to the Canon Shared printer from Ubuntu
I could not print to the HP printer connected to the Linksys printserver from Ubuntu.

When trying to print to the printer on the Linksys printserver - I would get the message:
Paused: job-hold-until-specified

Over the past several days, I setup and removed this printer several time through the Ubuntu Admin interface as well as through the CUPs (localhost:631/) -- always setting the printer up as a windows / Samba printer.

Nothing worked. ........ but - here's the solution:

Go through the normal "New Printer" setup

Printer Type:  Select Network Printer
and in the drop-down window, select Unix Printer (LPD)
in the Host window - enter the ip address of the printserver/printer
in the Queue window - enter L1 if you're using a parallel printer, or L2 if your printer is usb connected.

This may not be a very elegant solution, but it works fine for me and the XP machines are unaffected.:D

I can't take credit for this solution - it was originally posted by jhuff in 2005  -  here's a copy of his orig post:

I have finally got my Brother HL-1440 printer working after I installed the Linksys PrintServer PSUS4. It was not easy to get working with the windows computers connected to my network, but I finally did get it working. I am connecting the server to a Belkin wireless router (this could be one of my problems). I must have turned everything on an off a dozen times trying to get everything squared away. I did set a static IP address for the server becuase I was getting network address conflicts. So I am still at a loss as to how I finally got the windows computers working correctly. As far as my linux box I did the following:

Added a new printer using "Unix Printer (LPD)"
Host = Server IP address (192.168.2.xxx)
Queue = L1

I initially tried using CUPS Printer (IPP) but whatever I printed just kept printing multiple copies until I cancled the print job.

It was easier getting my linux box working then the windows computers.

---

