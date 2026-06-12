---
title: "How to install a network printer TCP HP Direct?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by marianlibrarian on 2009-07-22
Kubuntu 8.04.2 Fresh install - No other operating system - only Kubuntu
Printer: HP LaserJet 6P

I have installed our network printer on Ubuntu (several versions) with ease. My printer has its own ip address and the port in Ubuntu is 9100.

However, when I put this information in the Add Printer section of Kubuntu, the printer cannot be found. It is working today with the Ubuntu computers so I know the printer is accessible over the network.

There are several choices in the Add Printer section of Kubuntu. 

[LIST]
[*]In the step that is called "Backend Selection" I chose "Network Printer (TCP).
[*]Next - Network Printer Information:
[LIST]
[*]I type in my http:// printer ip address
[*]I type in the port number 9100
[*]I click on Next
[*]Error Message: No printer found at this address/port
[/LIST]
 
[*]I went back and chose: Network Printer w/IPP (IPP/HTTP)
[LIST]
[*]I type in my http:// printer ip address
[*]I am not asked for the port number
[*]I click on Next
[*]Error Message: No printer found at this address/port
[/LIST]
 
[*]There are no other network printer choices
[/LIST]
I selected the "Scan" function on both choices and it found nothing.

Perhaps there is a problem with the Subnet settings?
127.0.1. - 0-255
port 9100

But Kubuntu still unable to locate network printer. The only item left that I can change is the 127.0.1  - 0-255

Has anyone else experienced this problem?

EDIT: I can type in the ip address of the printer in my browser and the system settings for the print server are available on the Kubuntu computer. The Kubuntu printer wizard is not able to find the printer with this ip address.

---

### Post by marianlibrarian on 2009-07-22
I guess no one has had this question or problem before. So I am exploring on my own. I found that you can enter in the browser address bar:

[http://127.0.0.1:631/](http://127.0.0.1:631/)

The Common UNIX Printing System 1.3.7 appears. If I change the port to 9100 the page is empty. So I have narrowed it down to a port number problem?

I click on add printer link.
It asks for name: I typed in the server name that is listed at the printers ip address
I click continue
Next is "Device for Printer name" many choices:

[LIST]
[*]AppSocket/HP JetDirect
[*]Backend Error Handler - I could use one of those
[*]Hal Printing Backend
[*]HP Fax (HPLIP)
[*]Internet Printing Protocol (HTTP)
[*]Internet Printing Protocol (IPP)
[*]LPD/LPR Host or Printer
[*]LPT #1
[*]Print into PDF file
[*]SCSI Printer
[*]Serial Port #1
[*]Windows Port via SAMBA
[/LIST]
Since I know that I have used HTTP to connect to this printer successfully in Ubuntu, I am trying that one.

Will edit here when I get some kind of results.

---

### Post by marianlibrarian on 2009-07-22
That is the weirdest way to add a printer I have EVER seen. 

Don't use Kubunuts Printer Wizard. That was just a backend error handler. :confused:

Use 127.0.0.1:631

click on add printer
this happened so fast I hope I remember all the steps.

[LIST=1]
[*]It asks for name. I put the name of my print server here (I got it from the name that I found at the printers ip address.
[*]Then you have a bunch of drop down choices. I chose Internet Printing Protocol (IPP)
[*]Then I had a series of choices to type in. I chose ipp://my printer name/ipp/
[*]Clicked on continue and ... it added my printer!?!?!?
[/LIST]
Now I am at the "Set Printer Options Screen. :D
I can't believe it worked this way. WOW.

Oh one more thing: It will ask for your user id and password for kubuntu before it adds the printer.

---

### Post by marianlibrarian on 2009-07-22
Darn

Tried to do a test page:
**"Unable to locate printer 'PS-727463'!"**


**Description:** 
**Location:** 
**Printer Driver:** HP LaserJet 6P - CUPS+Gutenprint v5.0.2
**Printer State:** stopped, accepting jobs,  published. 
**Device URI:** ipp://PS-727463/ipp/  

So back to the beginning. Ideas / experiences are welcome.

---

### Post by marianlibrarian on 2009-07-22
Found an error log. Not sure what any of it means. 

E [22/Jul/2009:10:31:49 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [22/Jul/2009:10:44:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [22/Jul/2009:10:44:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [22/Jul/2009:12:52:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [22/Jul/2009:12:53:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [22/Jul/2009:13:07:50 -0500] [Job 1] Unable to locate printer 'PS-727463'!
E [22/Jul/2009:13:07:50 -0500] PID 7860 (/usr/lib/cups/backend/ipp) stopped with status 4!
E [22/Jul/2009:13:10:42 -0500] Resume-Printer: Unauthorized
E [22/Jul/2009:13:10:45 -0500] [Job 1] Unable to locate printer 'PS-727463'!
E [22/Jul/2009:13:10:45 -0500] PID 7872 (/usr/lib/cups/backend/ipp) stopped with status 4!
E [22/Jul/2009:13:11:08 -0500] CUPS-Set-Default: Unauthorized
E [22/Jul/2009:13:11:26 -0500] CUPS-Set-Default: Unauthorized
E [22/Jul/2009:14:07:38 -0500] Resume-Printer: Unauthorized
E [22/Jul/2009:14:07:40 -0500] [Job 1] Unable to locate printer 'PS-727463'!
E [22/Jul/2009:14:07:40 -0500] PID 7906 (/usr/lib/cups/backend/ipp) stopped with status 4!
E [22/Jul/2009:14:08:42 -0500] Cancel-Job: Unauthorized
I have not restarted this computer since I installed Kubuntu. I will try that and come back.

---

### Post by marianlibrarian on 2009-07-22
still trying to get my hp laserjet 6p to print from a kubuntu computer. It is working with the other Ubuntu computers.

Here is something that I googled. The printer is an HP just not the same model. Is this something that will work?
> 

[LIST=1]
[*]Completely uninstall the repository's hplip
 aptitude purge hplip
[*]Download the latest hplip package from [HP Linux Imaging and Printing]("http://hplipopensource.com/hplip-web/gethplip.html")
[*]Add all packages that hplip needs.  This may vary depending on your system; this list is *only what I had to add to my existing packages*.
 aptitude install libtool libsnmp-dev libsane-dev cupsddk cupsddk-drivers dbus-x11
[*]Remove any printers that no longer exist
 I think an existing printer driver for an older printer that I had disconnected caused a problem. Remove it from System Settings/Computer Administration/Printers.
[*]Run the latest hplip installer.
 sh hplip-3.9.2-run
 Your filename may vary.
[*]Test printing and scanning.
[/LIST]
  **If it fails with the dreaded foomatic-rip-hplip message**

 
[LIST=1]
[*]Clear out the existing installation
 sudo rm -rf /usr/share/hplip
[*]Run these commands **within the hplip-3.9.2 directory**
 ./configure --enable-foomatic-rip-hplip-install
make
checkinstall
I use [CheckInstall]("https://help.ubuntu.com/community/CheckInstall") to install any custom builds as individual packages.
[/LIST]
 That should do it - at least, *it worked for me*.
 
I think I could follow these instructions even though they make no sense whatsoever. But I don't know if they are legitimate.

---

### Post by LookTJ on 2009-07-22
> **marianlibrarian said:**
> Darn

Tried to do a test page:
**"Unable to locate printer 'PS-727463'!"**


**Description:** 
**Location:** 
**Printer Driver:** HP LaserJet 6P - CUPS+Gutenprint v5.0.2
**Printer State:** stopped, accepting jobs,  published. 
**Device URI: ipp://PS-727463/ipp/**  

So back to the beginning. Ideas / experiences are welcome.
should be socket://IP(not name):9100 I think

---

### Post by LookTJ on 2009-07-22
More Info from [CUPS]("http://www.cups.org/documentation.php/network.html")


> **AppSocket Protocol**

  The AppSocket protocol (sometimes also called the JetDirect protocol, owing to its origins with the HP JetDirect network interfaces) is the simplest, fastest, and generally the most reliable network protocol used for printers. AppSocket printing normally happens over port 9100 and uses the socket URI scheme:
  socket://*ip-address-or-hostname*
socket://*ip-address-or-hostname*?waiteof=false
socket://*ip-address-or-hostname*:*port-number*
socket://*ip-address-or-hostname*:*port-number*?waiteof=false
 The "waiteof" option controls whether the socket backend waits for the printer to complete the printing of the job. The default is to wait.



---

### Post by marianlibrarian on 2009-07-22
[SIZE=4][B]Solved!
[/B][/SIZE]
Do not use the Kubuntu Add Printer Wizard IF you are adding a NETWORK PRINTER

There is a weird thing with the subnet number. It opens with the subnet number 127.0.1.* but you can change this. I changed it to 127.0.0.* (the * designates the second field with numbers or the last digit or digits after the last dot) This allowed me to find "localhost" but did not let me allow me to add a network printer.

I got a message:
You are about to scan a subnet (127.0.0.*) that does not correspond to the current subnet of this computer (127.0.1.*). Do you want to scan the specified subnet anyway?

Yes - and it will find "localhost" Then I am guessing you can add a LOCAL printer.

Use your browser to add a NETWORK printer.
[http://127.0.0.1:631](http://127.0.0.1:631)

This opens up a really nice page that belongs to CUPS. 

Even though I had used :631 in my web browser, when I added my printer, I used:
APPsocket/HP Direct which was at the top of the list. Then I used the following:
socket://192.168.1.41:9100

There were not many steps and when it was finished, I was able to do a test print.

The URI in my printer information window:
URI: ipp://localhost:631/printers/PS-727463

I was going to delete all my previous posts but this forum doesn't allow deletion. I wanted to document what I was doing just in case... Thank you LookTJ for ... Looking! :)

---

### Post by LookTJ on 2009-07-22
Glad you solved your issues.

And thanks for posting your solution as someone may learn from it.

Have a good day:D

---

