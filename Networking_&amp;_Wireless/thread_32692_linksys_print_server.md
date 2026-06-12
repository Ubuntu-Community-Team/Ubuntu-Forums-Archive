---
title: "linksys print server"
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by danip on 2005-05-09
I am contemplating putting Ubuntu on my parents computer now that I am home that way they wont call me every week because something went wrong.  The one question I have though is my parents have one printer and it is shared between all the computers in the house via a linksys print server.  I was wondering if anyone here has any experience getting a printer to work that is connected to a print server.  If it is not to hard of an issue to get working then I will be putting linux on one of their computers.

---

### Post by eivind on 2005-05-09
I take it that the print server is connected, along with the other computers, to a hub/switch. In such cases, it's generally no problem to get it work in whichever linux you have.

The one thing you have to know is the print server's IP address. Your setup sounds like some kind of lan, and a lan has a dhcp server handing out addresses, as you probably already know (this can also be the print server itself). You can right-click on the printer in windows, select properties and go to ports to find out this.

To get the printer work: Just install Ubuntu, go to the "System"-menu, -> Administration -> Printing (think those are the English terms), and double click "New printer". 
Select "network printer", HP Jetdirect type, and then add the address of the print server.
Click next, and choose your make and type of printer. This should basically be the cure. Let me know if you experience trouble, and we'll find out of them.


Cheers

Eivind

---

### Post by danip on 2005-05-09
very easy to setup thanks for your help.

---

### Post by tikkitembo on 2005-07-16
Wow!  I just had to comment on how easy this was to set up.  You have to go through major hoops in Windows to get a Linksys wireless print server set up.  There is a special print driver that has to be installed.  Then you have to configure the printer.  I believe you also have to start with a Linksys installation CD.  It took me numerous tried and an hour and a half to get it working with Windows XP!

In Ubuntu Hoary, I did the following and it worked the FIRST TIME!

1. Go to System/Administration/Printing
2. double click "New Printer"
3. Select "Network Printer" and select "HP JetDirect" as the type. (instead of default "CUPS")
4. In the "host:" box, type the IP address of the print server.  Mine was a wireless print server so I just went into the web configuration for the Linksys wireless router and found the IP address in the "DHCP Client Table" 
5. Leave the Port as 9100 (default for me already in box)
6. click the "Forward" button
7. Select the Printer manufacturer and the model from the lists
8. click "Apply."

After a few seconds, you should see a new icon for your printer.  I went straight to Firefox and was able to print a page!  It also worked great from OpenOffice.

I've been an off and on user of Linux since the mid 90's and I have to say that hoary is the most impressive client Linux I've ever seen.  (I've run Redhat, Mandrake and LinSpire and this is hands down the best client distribution!)

tikki

---

### Post by ptrok on 2005-07-20
Gidday,
I am a first time Linux user .... used UNIX way back in my uni days but this different again - and good fun too !!

I Tried using instructions above to install a laser printer which is attached to a Netgear FM114P wireless router/print server.
The printer adds OK but when I goto print a test page it tells me that

"The operation timed out when attempting to contact 192.168.0.1"

IP address is my for router (std address) .. is this wrong? do I need to add a port or something ?
Checked the router/print server reference and it says I need to configure LPR printing ???

Would appreciate any pointers from the wise.

Regards

Paul

---

### Post by lonetree on 2005-07-21
[QUOTE=ptrok]Gidday,
I am a first time Linux user .... used UNIX way back in my uni days but this different again - and good fun too !!

I Tried using instructions above to install a laser printer which is attached to a Netgear FM114P wireless router/print server.
The printer adds OK but when I goto print a test page it tells me that

"The operation timed out when attempting to contact 192.168.0.1"

IP address is my for router (std address) .. is this wrong? do I need to add a port or something ?
Checked the router/print server reference and it says I need to configure LPR printing ???

Would appreciate any pointers from the wise.

Regards

Paul[/QUOTE]

Hi,

there is a few things you need to get ready.

1) make sure that there is a valid driver for your printer in ubuntu.
2) your print server IP address, which I assume is "192.168.0.1", normally it should be the same IP as the gateway, i.e your router IP address.
3) you have to determine your print queue name, check with netgear for this, I am using Dlink DI-724P+ and the queue name is "lp", so perhaps you would want to have a try with this. For what I know, most of them use the same name.

If you have all the above ready and assuming you are using ubuntu 5.04 hoary, go to 

1) System | Administration | Printing. The printers windows should show up.
2) Double click on New Printer. "Add a printer" dialog should show up now
3) check on the "Network Printer" radio button and choose Unix Printer (LPD) and enter the IP address of your print server (for your case, it might be 192.168.0.1) for the **"host"** and *lp* for the **Queue** , then click "forward"
4)from here on, you should be able to carry on, choose the correct printer driver and do a test page after installing.


Hope this would help.


:-)
regards.

---

### Post by hillel213 on 2008-03-26
It was very difficult to setup this Linksys print server; however, it can be done!

There is a great post I would refer you to: [B]
[http://ubuntuforums.org/showthread.php?t=516747]("http://ubuntuforums.org/showthread.php?t=516747")[/B]

However, there is one point that is not clear...

When you input the ipp://[ip address]:631/ipp/P1, for example, ipp://192.168.1.44:631/ipp/P1, what is the 631?

The 631 is the open port.  So, the format is:  ipp://[ip address]:[port]/ipp/P1

You can find the port by typing the following in the terminal:

**sudo nmap [static ip address]**

for example, sudo nmap 192.168.13.254

When you get the result look for the http row.  My port number was 80 instead of 631,



if this does not work, you will need to install nmap prior to the above command...

**sudo apt-get install nmap**


In summary,

1. Read the above post and get the wireless print server to give you a static ip address
2. Add a printer and enter the appropriate ** ipp://[ip address]:[port]/ipp/P1 ** in the Device URI field

Good luck!

---

