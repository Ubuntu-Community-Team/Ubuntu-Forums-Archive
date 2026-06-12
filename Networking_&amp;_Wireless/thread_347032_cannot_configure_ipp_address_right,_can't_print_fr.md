---
title: "cannot configure ipp address right, can't print from client, cups not cooperating"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by dsimpson on 2007-01-26
Hi, I finally got cups working on my system again, but when configuring it through the cups website, I am not able to get the client computer to connect to the host and the printer. My host computer has the printer and is wireless, the client is connected via ethernet cable to the router. I can access the client computer from my host computer but the client doesn't see the host, and when trying to print from the client it doesn't access the printer. My host computer address is 192.168.2.3, while my client is 192.168.2.2, and the router is 192.168.2.1. I have a psc HP 2500 series printer and is connected as a local printer. I tried configuring it like it says it Ubuntu guide and I messed up my cupsys and that took me a week to fix. I tried lpadmin -p (hp  psc 2500) -E - v [http://192.168.2.3:631/printers/hp](http://192.168.2.3:631/printers/hp) psc 2500 series USB#1 on the client computer, and that did nothing. I really don't have a clue as to how to find the address that I can point to to get the client computer to see the printer. I have tried manually through printer preferences, through changes made on the cups online site (localhost:631) and trying to make changes through the terminal. My computer's name is eaglesoldier and the printer is under computer/HP  psc 2510. Any ideas on how I can make this work will be greatly appreciated. I have been trying for a couple of weeks to figure this out and haven't had any luck.:confused:

---

### Post by dsimpson on 2007-01-27
Hello out there. hasn't anyone tried to connect two Ubuntu computers on a network and enabled printing? I see dozens of posts concerning windows to Ubuntu but there certainly must be a few that have gone strictly Ubuntu and connected two computers on a network. 
I am unable to even connect my host computer to the printer through cups, I must connect it as a local printer in order for it to print. I think that as a result I then cannot be found by my second computer, I really need someone who is familiar with cups, networking to explain what I may be doing wrong. All of the reading on the Ubuntu book and Ubuntu desktop guide so far hasn't given me the answer, it is too general, saying ipp://enter location/printers/printer name etc. but doesn't go into detail as to how to enter the location (computer name or dns numbers?), do you just enter "printers" or do you identify the printers on your network? Do you identify your printer by the model # or do you input the model series that identifies the driver for your computer? So many questions. so far no answers.
If anyone out there has dealt with this issue. please post. whether you have successfully worked out a solution or are still trying, maybe together we can work out the answer. This is frustrating, but not to the point of where I would ever consider dropping Ubuntu, I just want to resolve these issues and then move on to computing for the joy of computing and not to be constantly fixing something. :)

---

### Post by dsimpson on 2007-01-29
**Update on this problem.** Changed the cupsd.conf on both computers, seems to be no conflicts, 

I was able to print the test page from the client computer but the printer is still not detected, when I try to print from a document, the web, or an email, the printer does not work. I receive the following on a printout from my printer when the document tries to print 
[ [COLOR="Blue"]12345X@PJL ENTER LANGUAGE=PCL3GUI 17H1-1M126Ao0M1-2Hg20WXX  XX  u600Dr4812Sr1AP58Yb0Vb23W[/COLOR]] I really don't have a clue as to what this means but this is the only thing that will print from the client computer. 

Additional problems, I show 3 sometimes more printers in my Printers dialogue, and when I try to remove or delete the printers to install a new printer, I am unable to, and all jobs sent to any of the other printers that pop up when a job is sent for printing are all routed through one of two printers that will not delete. The jobs are then just pending as these 2 printers (Queue, and HP PSC 2500 - the identity of the two permanent printers) are constantly in "pause" and I have been unable to enable them for printing. 

My goal right now, would be to remove or delete all printers, install the new default printer and attempt to configure that one to print from the client computer. I have tried to remove by deleting throught System/Administration/Printers, no luck, I have tried going to the CUPS web interface and deleting, it shows that the printers are deleted or removed, but when I go to the Printers dialogue under system/administration/printers they are still there, and when I try to print from the client computer both show up plus the new printer created by the new print job. 

If there is anyone out there that has resolved the issue of deleting printers via another method, i.e. terminal or someway similar, I would really appreciate your help. I also would like to know how to get my printer to its final config so it will print from the client. If you know what the printed message [COLOR="Blue"](printed in blue above)[/COLOR] is asking for I would appreciate help in that area also.:confused:

---

### Post by Jango on 2007-02-07
try this page: [https://launchpad.net/ubuntu/+source/cupsys/+bug/55828](https://launchpad.net/ubuntu/+source/cupsys/+bug/55828)

I used that adbive by Pascal De Vuyst  at 2006-08-15 12:02:46 UTC

"Forget about the workaround I mentioned before by setting up a raw queue on the server.

When setting up an IPP printer with gnome-cups-manager on a print client you always have to associate a PPD with it by selecting the manufacturer, model and driver for your printer.
This doesn't make sense for a network printer, since you have already configured the manufacturer, model and driver on the print server.

To make it work you can setup your printer manually with the following command:
$ lpadmin -p printername -E -v ipp://10.0.0.40/printers/dj3820

Another possibilty is to activate browsing on the server to let your print client autodetect the printers.
You can easily enable browsing on an Ubuntu print server by running the following command:
$ sudo /usr/share/cups/enable_browsing 1
Then start gnome-cups-manager on the print client an activate Global settings > Detect LAN printers. Now wait 30 seconds and your printers will appear.

In both cases you will see that the "Paper" and "Advanced" tabs are disabled in the "Properties" of you printer in gnome-cups-manager, this is normal.

Associating a PPD with an IPP printer with gnome-cups-manager worked in CUPS 1.2.0 and 1.2.1, this behaviour seems to have changed in CUPS 1.2.2.
This could be a bug in CUPS 1.2.2, but IMHO setting up an IPP printer associated with a PPD file doesn't make sense since you already configured the printer on the server. Therefore gnome-cups-manager should be altered so it doesn't ask the manufacturer, model and driver for an IPP printer.
Also printing options should be visibile in the "Paper" and "Advanced" tab of the printer "Properties". These options should be read from the server which is perfectly possible now from the following command line:
$ lpoptions -d printername -l
These printer options are set on the server but gnome-cups-manager should allow for an override on the client in ~/.cups/lpoptions."

I used the LAN DETECTION (from the GLOBAL settings menu). It worked just fine,
good luck!

---

