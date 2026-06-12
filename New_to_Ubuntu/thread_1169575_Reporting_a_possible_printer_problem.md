---
title: "Reporting a possible printer problem?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by HugoB on 2009-05-25
I have a problem with connecting to a printer on another Windows machine.

There are 2 machines connected onto a network. The one machine is running Ubuntu Linux and the other machine is running Windows.

Ubuntu Linux was able to connect to the Windows machine to access files from it on the network, but following the printer setup guide on the pocketguide pdf, I ran into a problem:

The instructions I followed is stated below:
Go to System > Administration > Printing > Click on new > Choose network printer from the devices listed > Choose Windows Printer via Samba > Click on Browse... button > 

Now here is the problem

A new window appears (a collapsed node list) showing the computer on the network. Expanding the node it creates one more level and expanding it once again the list of windows just closes with no error message or anything.

I'm using an HP 5610-Officejet All-in-one series printer connected to the Windows machine.

Anyone had this problem before?

---

### Post by HugoB on 2009-05-25
[UNSOLVED]

Not fixed

  :|

---

### Post by bleedpurple on 2009-06-16
I have the exact same problem.  How did you fix it?

---

### Post by bleedpurple on 2009-06-16
I got it to work too.  Is this a bug though?  I'm running 9.04. 

I went to the Windows box and checked the properties of the printer to get the network name then entered MSHOME/MAINPCDELL/HPPSC2100 in the "SMB Printer" prompt box.  MSHOME is the name of my network and MAINPCDELL is the name of my computer which has the printer attached.  The printer name on the network is HPPSC2100.  Very imaginative names all, I know. 

Clicking the BROWSE button led down a level to where I got the network name and the PC name and then when i clicked the chevron again to get the shared printer name the box disappeared with no error message. :?:

---

### Post by HugoB on 2009-06-17
_There are 2 problems (but the one was easy to fix):_

_List of problems:_
Setting up and installing the printer (fixed)
Making the printer print something (not fixed)

_Setting up and installing the printer (fixed)_

[LIST=1]
[*]Click System > Administration > Printing
[*]Remove the printer you want to install via SAMBA
[*]Click on Server menu > Choose Printer
[*]Expand Network Printer and choose Windows Printer via SAMBA
[*]Options on the right hand side should appear starting with SMB Printer
[/LIST]

_This was the fix for my machine:_

[LIST=1]
[*]Instead of clicking browse, type the path manually in the textbox
[*]WORKGROUP: Provide the windows workgroup name (on the server where Windows is installed)
[*]SERVER: If it is a static IP (which mine is), follow the workgroup name with a "/" and type the IP address (of the server) ending it with a forward slash (/)
[*]The other paths was ignored and then I just clicked browse button (after providing the above path). If the information in the textbox was typed correctly, it then detected the printer when I clicked the "Browse..." button (showing an expanded list on the server side where the printer could be located at).
[/LIST]
After choosing the printer in the list, more information had to be provided:

The manufacturer as well as the model number. The exact model number could not be given because it is a 5610 Officejet All-in-one printer, so it was assumed that the OfficeJet 5600 driver had to be selected.

After going through the setup process Ubuntu Linux states that the printer driver was installed and it was online, however this is the second problem I am faced with and I have not found a fix for it yet.

_Making the printer print something (not fixed)_
By surprise, the first time I remembered getting it all setup and going, the 5600 driver printed one line on a piece of paper ("Test") through the printer connected on the windows pc.

The second time something was sent to the printer, Ubuntu Linux reports a message stating that the print job went through successfully, although this was not the case.

The printer detected that a page was going to be printed and then it just hangs, printing absolutely nothing (the LCD screen on the printer shows a message like "waiting" / "loading", something like that).

Any help would be appreciated thanks :)

---

