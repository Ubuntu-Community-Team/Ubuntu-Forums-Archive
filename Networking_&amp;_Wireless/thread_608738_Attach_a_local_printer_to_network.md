---
title: "Attach a local printer to network"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by DalekClock on 2007-11-10
As my networks main printer is not working well, I'm thinking about attaching my local USB attached printer to the network under Ubuntu 7.10. What I want to know is how to do this and whether or not Windows will recognise it with the drivers installed.

---

### Post by SpiritIsReality on 2007-11-10
howdy
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
> Samba is not necessary to:Have your Windows computer use (via a network) a printer that is attached to a Linux computer, you do not need Samba. CUPS can be configured to make the printer accessible to the network.
System > Administration > Printing > Add New Printer > click on your Printer > Forward > Select Printer > Forward >
Select Model > Forward > Printer Name > Apply  (write down or remember the printer name)
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
> Ubuntu Print Server
1.

 ... On the server machine (the one the printer is attached to) open up printer manager with
 sudo gnome-cups-manager  
Or System->Administration->Printing.
2.
 ... Under Server Settings check, i.e, turn on, the Share published printers connected to this system .
3.
 ... Click on the Apply button;

Ubuntu Client Machine

Now on the client(s) (the one that you want to link to the shared printer that is in server machine):
1.Open up the printer manager System->Administration->Printing
 Or open the Terminal:
 sudo gnome-cups-manager 
2.Under the Server Settings check the Show Printers shared by others systems option.
 Click on the Apply button;
Then you can open any document, and try to print it. It should appear in the printer dialogs box the name of the shared Printer.
*please see this next link, 
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=network+printing&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=network+printing&titlesearch=Titles)
thanks to DrunkinRoxtar here [http://ubuntuforums.org/showthread.php?t=610043](http://ubuntuforums.org/showthread.php?t=610043)
and dj_penguin here [http://ubuntuforums.org/showthread.php?t=608633](http://ubuntuforums.org/showthread.php?t=608633)

#### SEE *** below for a way that worked for me ####
-----------------
This was not done on fresh install of ubuntu 7.10 or fresh install of xp. It should be to give it a fair test. What other kind of test is there.
So the above is good advice, the below is a ... well it's not much. I've been monkey wrenchin' at the both of them tryin' to learn a thing or
two, or fo000ur. And the one thing I just learnt is that I don't know why it didn't work. I will have to fresh install the both boxes to get any
kind of a semblance to an answer to your question. I've been learning about samba and LTSP (LinuxTerminalServerProject) which I got workin' in a beginner's sort of way, which I'm very happy about , but in no way satisfied with. I want to know how to get it to gallop, not just snort and buck me off. haha!
LInks
[http://ubuntuforums.org/showthread.php?t=608751](http://ubuntuforums.org/showthread.php?t=608751)
[http://ubuntuforums.org/showthread.php?t=608744](http://ubuntuforums.org/showthread.php?t=608744)
The System > Administration > Printing (The window did not close on it's own, after ubuntu print server 1.2.3 above. I left it alone until I tried printing from xp .
The Ubuntu printer server I am using has a static ip address.
The xp box can ping the Ubuntu print server.
On xp, Start Control Panel > Network Connections > Network Setup Wizard has been run before I shared the Ubuntu printer server.
Start > Control Panel > Printers and Faxes > Add Printer > Next > A network printer , or a printer attached to another computer > Next > Connect > Next > click on Connect to this printer (or to browse for a printer, select this option and click Next) > Next > Printer:type in the name of the printer from the ubuntu printer server (On the Ubuntu printer server, System > Admin > Printing, and the name will be in the left hand panel) > on xp , Click on the name of the ubuntu printer
server in the box marked Shared printers > Next > Error Message of Connect to Printer .. Windows cannot connect to the printer. Either the printer name was typed incorrectly or the specified printer has lost its connection to the server. For further information click Help. (xp can still ping the ubuntu printer server) (the name was typed correctly)
Hopefully someone else has better news
Clicked Help in the Connect to Printer error window > clicked only choice remotely valid is I can't install a local printer.
Left box checked,(or put a check in box)I want the troubleshooter to investigate setting on this computer. > Next >
Are you using a printer driver that is compatable with Windows XP?. ( I don't see the point of persuing that line of 
questioning) (I'll try printing from another xp box on the network)
 
I made a mistake the first time, where I didn't choose the first option of Browse for a printer. I ran the Add Printer Wizard
on the xp box again and chose the Browse for a printer. End result , same error message.
______________________
***
The Ubuntu printer server I am using has a static ip address.
The xp box can ping the Ubuntu print server.
xp Add Printer Wizard
Start > Control Panel > Printers and Faxes > Add Printer > Next > choose A network printer, or a printer attached to another computer > Next > Browse for a Printer > Double Click the Ubuntu printer server Name (anywhere on the line containing the Ubuntu printer server Name) > click on Printer Name (anywhere on the line containing the Printer Name)
> Next > a message window appears called Connect to Printer saying > You are about to connect to a printer on "it says your Ubuntu printer server Name" which will automatically install a print driver on your machine. Printer drivers may contain viruses or scripts that can be harmful to your computer. It is important to be certain that the computer sharing this printer is trustworthy. Would you like to continue? > click Yes > a message window appears called Connect to Printer saying > The server for the printer does not have the correct printer driver installed. If you want to search for the proper driver, click OK. Otherwise, click Cancel and contact your network administrator or original equipment manufacturer for the correct printer driver >  click OK > at
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP?highlight=%28printing%29%7C%28network%29](https://help.ubuntu.com/community/NetworkPrintingFromWinXP?highlight=%28printing%29%7C%28network%29) it says 
>  2) Windows will ask you to select a driver for the printer. If you have the Windows print drivers, you should use them. Click the "Have Disk" button and select the .inf file that describes your print drivers.
If you do not have the drivers for the printer or cannot load the .inf file, you should select the "MS Publisher Color Printer" driver from the "Generic" manufacturer. This driver should be found on all Windows 2000 and XP installations by default and it gives all the printing functionality one should need.  
>  an Add Printer Wizard window appears, saying, > Select the maufacturer and model of your printer. If your printer came with an installation disk, click Have Disk. If your printer is not listed, consult your printer documentation for a compatible printer > click Have Disk > a message window appears called Install from Disk saying > Insert the manufacturer's installation disk, and then make sure that the correct drive is selected below > place the disk in drive  (if you do not have a disk, see **** below) > at Copy manufacturer's files from: click Browse > a Locate File window appears. AT the Look in: ......click the expansion, downward pointing arrow. Choose a cd drive or a floppy drive that you put the disk in > (it will show the files in a window, I did NOT highlight any of them, I just clicked Open) click Open > the Install From Disk window appears, and it shows the drive letter of the drive you chose in the box under the words Copy manufacturer's files from: > click OK at the top right of the window > a message window Add Printer Wizard appears, saying > Select the manufacturer and model of your printer. If your printer came with an installation disk, click Have Disk. If your printer is not listed, consult your printer documentation for a compatible printer ...In the box named Printers, if your printer is listed there , click it once, to highlight it, it will turn blue.> click OK > a Copying Files... window appears, and it showed files being copied, and then it dissappeard, showing the Add Printer Wizard window in the last state you left it, I was kind of wondering what to do.... just wait for the Add Printer Wizard window to change, showing a heading of Default Printer, saying > Your computer will always send documents to the default printer unless you specify otherwise. Do you want to use this printer as the default printer? > the button in front of Yes had a dot in it. I left it at that > Next >
In the window that appears, you can check the details. >  Finish.
You can remove the disk from the xp computer.
You can close the Printers and Faxes window now if you want to. Try printing something on the xp box and see if it sends it to the Ubuntu printer server and the printer prints it.  For example, in Firefox, click File > Print > OK

****if you do not have a disk, then in the left hand window click on Generic, and in the right hand window, click on MS Publisher Color Printer > OK > a window will show files being copied > when the Add Printer Wizard window shows a heading of Default Printer, saying "Your computer will always send documents to the default printer unless you specify otherwise. Do you want to use this printer as the default printer?" > the button in front of Yes had a dot in it. I left it at that > click Next > Finish.
You can close the Printers and Faxes window now if you want to. Try printing something on the xp box and see if it sends it to the Ubuntu printer server and the printer prints it.  For example, in Firefox, click File > Print > OK
I tried this, after deleting the printer icon created in the Have Disk option above. I chose the General and MS Publisher Color Printer. It did not work on this network. In the Printers and Faxes window, I deleted the printer icon.

As I was working thru the No Disk steps, I remembered that I have read and followed directions almost to the word, from a forum on the internet. At that time, we were trying to share one xp's printer to another xp computer.  I don't know why I didn't think of searching for directions this time. The directions I followed then, could be included in this link [http://www.google.ca/search?hl=en&q=xp+share+printer+xp&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=xp+share+printer+xp&btnG=Google+Search&meta=)
I vaguely remember him saying something like that too! haha! I know I printed his post after the great struggle, it seemed to be at the time, to find any directions to do such a wild and wonderful thing. My Dad and I spent quite a bit of time trying to find directions that worked. Following along his directions was very difficult for us. We were not very experienced at running computers, and I'm still not now. One of us would  hold his finger on the directions so we wouldn't lose our place, because there were no [quotes] to make the great ones we get now,  just "." and to conserve space, the poster said he didn't break up the lines at every > mark, on purpose. When it came to clicking, my Dad would ask, where do I click? ... and once or twice? I didn't know either. It was good. It seemed a little rough at the time, but good and rough now. ha! He finaly got it going one late night while I was sawing logs. He finally double clicked the computer name ... And just like today, I misplaced the disk. Well this time I put it back in the xp's cardboard box that has all the driver disks and the install disk and the booklet the install disk came in. But, I put it in it's jacket backwards, so when I went looking for it, it just looked like a plain recordable cd thru the clear side of the envelope, not the printer's driver cd. I looked at it and put it back twice before I finally took it out to check. #!@#! haha! I'm not just typing that haha! I'm laughing. The printed directions are probably still in my gear somewhere ... I'm sure glad I finally double clicked the Ubuntu printer server Name, a fluke really. But I know one thing for sure, it wasn't a Ubuntu computer last time. It is this time, and that's good. I'm happy. I like this. A toast to all who got Gnu/Linux and the rest of the free operating systems and free software to where it is today. THANKS!!!  now I got somethin in my eye. gotta go. haha! I love this s###!!! That's stuff with one f.
trails
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=network+printing&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=network+printing&titlesearch=Titles)
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP?highlight=%28printing%29%7C%28network%29](https://help.ubuntu.com/community/NetworkPrintingFromWinXP?highlight=%28printing%29%7C%28network%29)
[https://help.ubuntu.com/community/UserPreferences?action=fullsearch&context=180&value=printing&titlesearch=Titles](https://help.ubuntu.com/community/UserPreferences?action=fullsearch&context=180&value=printing&titlesearch=Titles)
[https://help.ubuntu.com/community/DebuggingPrintingErrors?highlight=%28printing%29](https://help.ubuntu.com/community/DebuggingPrintingErrors?highlight=%28printing%29)

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
[http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)

---

### Post by dj_penguin on 2007-11-13
Hiya all,

I've been asked to reply here to my initial thread [[http://ubuntuforums.org/showthread.php?t=608633&page=2]](http://ubuntuforums.org/showthread.php?t=608633&page=2]).  I attempted adding the printer on the XPbox by browsing the network.  Now, my XPbox can see my Linux box but it can't see the printer attached to the Linux box.  The Linux box can see and access all the WinXP shares and printer.

Any suggestions guys?

---

### Post by SpiritIsReality on 2007-11-13
When you worked on the Ubuntu printer server settings, did you select share in the configuration of the printer?
System > Administration > Printing > click printer's name in left side of window >
Policies > now the boxes should have check marks in the Enabled , Accepting Jobs ,
and Shared.
In Settings tab, is there a Description and Device URI ... ?
In xp,  when you are running the Add Printer Wizard ,when you see the Ubuntu printer server in the box, did you double click on the name of your Ubuntu printer server ? When I did the double click, pop, out came the printer that's hooked on the Ubuntu printer server.I clicked on the name of the printer, and clicked OK or Next.
If you followed any of the instructions in the post #2 above, that could be your biggest problem. haha! Please let me know if you find something that's up'd.

---

### Post by dj_penguin on 2007-11-14
> **SpiritIsReality said:**
> When you worked on the Ubuntu printer server settings, did you select share in the configuration of the printer?
System > Administration > Printing > click printer's name in left side of window >
Policies > now the boxes should have check marks in the Enabled , Accepting Jobs ,
and Shared.
In Settings tab, is there a Description and Device URI ... ?
In xp,  when you are running the Add Printer Wizard ,when you see the Ubuntu printer server in the box, did you double click on the name of your Ubuntu printer server ? When I did the double click, pop, out came the printer that's hooked on the Ubuntu printer server.I clicked on the name of the printer, and clicked OK or Next.
.
Yes to all of the above.

---

### Post by dj_penguin on 2007-11-15
#BUMP#

Has anyone any suggestions?

---

### Post by Peter09 on 2007-11-15
I have just got my printing working by making a small change to the cups.conf file ....

at the bottom of there file hash out the existing line and replace by /etc/printcap. As below.

#Printcap /var/run/cups/printcap
Printcap /etc/printcap

---

### Post by dj_penguin on 2007-11-15
Anyone?

---

### Post by SpiritIsReality on 2007-11-17
> **Peter09 said:**
> I have just got my printing working by making a small change to the cups.conf file ....

at the bottom of there file hash out the existing line and replace by /etc/printcap. As below.

#Printcap /var/run/cups/printcap
Printcap /etc/printcap
***_ thanks pard/

---

### Post by dj_penguin on 2007-11-17
> **Peter09 said:**
> I have just got my printing working by making a small change to the cups.conf file ....

at the bottom of there file hash out the existing line and replace by /etc/printcap. As below.

#Printcap /var/run/cups/printcap
Printcap /etc/printcap
I have no such line in my cups.conf file.  My file reads;
```
<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
  <!-- Only root can send this message -->
  <policy user="root">
    <allow send_interface="com.redhat.PrinterSpooler"/>
  </policy>

  <!-- Allow any connection to receive the message -->
  <policy context="default">
    <allow receive_interface="com.redhat.PrinterSpooler"/>
  </policy>
</busconfig>
```

And my cups.conf file is located at /etc/dbus-1/system.d/

---

### Post by Peter09 on 2007-11-18
Never seen a cups.conf that looks like that! I should double check on things before you edit it.

---

### Post by dj_penguin on 2007-11-19
So has anyone any suggestions?  It's getting irritating having to transfer my files from my WinXP box to my Ubuntu box before printing.  Other than this, my transition from Windows to Linux has been seemless :smile:

---

### Post by dj_penguin on 2007-11-20
**_New Development_**
I made some changes to my cupsd.conf file following the instructions at <http://ubuntuforums.org/showthread.php?p=163882> and found that my WinXP box can now access the printer.  However, when I try to install the printer on my XP box, Windows hangs while 'connecting to the printer'.  Does anyone have any suggestions?

---

