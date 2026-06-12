---
title: "Connecting to University Windows Printer Nework"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by Trenchcoat on 2008-11-12
Perhaps this is a silly question, but I would like to know if it is possible to connect my laptop to my university printer network.

The University provides instructions for how to connect laptops running Windows, and I have previously had success running VMWare. However, I am no longer using VMWare. The instructions that they provide say that this is only possible through Windows. Not knowing enough about this sort of thing, I don't know whether to believe them.

I have copied the instructions as the Uni gives them below. They can also be found here:
[http://www.students.ucs.ed.ac.uk/helpdesk/student/system/show.cfm?documentID=7769](http://www.students.ucs.ed.ac.uk/helpdesk/student/system/show.cfm?documentID=7769)


> a) How to print from your own laptop

It is now possible to print to the printers in the open access labs from your own laptop.

Note: At present, this facility is only available on laptops running Windows XP.

    * To print, your laptop must be connected to the university wireless network (either central or central-wpa) or LapLAN2.

If you need help connecting to the network, see one of the documents Wireless Guide for Windows XP or LapLAN2 for Windows XP. Alternatively, email [email]student.support@ed.ac.uk[/email], or call in at one of the student support helpdesks with questions about any aspect of this guide.
Check your print credit

When printing from your laptop, money will be deducted from your print credit account, just as if you were printing from the open access computers. However, if you don't have enough credit in your account, the print job will fail without warning, so you should check your credit before you try to print:

    * Go to [https://www.printbalance.ucs.ed.ac.uk](https://www.printbalance.ucs.ed.ac.uk)
    * Log in with your universal username and the password you use to log in to the open access computers.

Your print balance will be displayed. Printing costs 5p per sheet for single-sided, 8p per sheet for double-sided, and 30p per sheet for colour.
Choose a printer name

In most open access computing labs, there will be one black & white printer and one colour printer (where available) which can be used by laptops. These printers have an -M after their names, which stands for mobile printing. You should not attempt to use any other printer from your laptop.

The list of suitable printers is given here: [www.ucs.ed.ac.uk/usd/student/laptop_printers.html](www.ucs.ed.ac.uk/usd/student/laptop_printers.html)

Choose one, and make a note of its name and print spooler. Some examples:

Location
	

Printer Name
	

Print Spooler

Darwin Library
	

SWANA-M
	

pcsp4

Hugh Robson building
	

HRBA-M
	

pcsp1

JCMB level 3 Microlab
	

JCMB3A-M
	

pcsp4

Main Library level 2
	

LIB2A-M
	

pcsp2

Main Library level 3
	

LIB3A-M
	

pcsp1
Set up your computer for printing

    * Right click on your Desktop, and select New and Shortcut.
    * Enter the following address in the Location box: \\spooler.ucs.ed.ac.uk

but replace spooler with the print spooler name you noted down in the previous section. For example, \\pcsp1.ucs.ed.ac.uk.

    * Follow the instructions on screen to create the shortcut. Make sure you give it a descriptive name, such as pcsp1 uni print spooler.
    * Double-click on the shortcut you have just created.

      Shortcut
    *

      You will be asked for a username and password. In the User name box, enter ed\ followed by your universal username, e.g. ed\s0654321. In the Password box, enter the password you use to logon in the open access computing labs.

Note: You must put ed\ before your username or you will not be able to connect.

    * Click OK.

A window with a list of printers will appear. Go to the View menu and click Details. You should now be able to sort the printers by name, or by comments. If you click on the Comments column heading, the printers whose names end in -M will be sorted to the top of the list, making it easier to find them. (Remember to only use printers whose names end in -M.)

mprinters

    * Right click on the printer and choose Connect.
    * Click Yes to continue. (You may be asked for your computer's administrator password at this point.)

Print your files

Once you have connected to the spooler and installed the printer driver (as above), you can print.

    * Open the file you wish to print, click on the File menu, and select Print.
    * Select your chosen printer from the Name: box, and click OK.

Note: When you click OK, your file will be sent straight to the printer. You will not be asked for confirmation.
The next time you want to print

If you wish to use the same printer again after rebooting your computer, follow the instructions below to reconnect to the spooler. (Note that if you wish to use a different printer, you will have to start again from the Choosing a printer name section.)

    * Double-click on the pcspX uni print spooler desktop icon.
    * Enter your username and login password, and click OK. (Remember to put \ed before your usual username.)

You can now print. Just make sure that you select the correct printer in the Print window.

---

### Post by superprash2003 on 2008-11-12
you could try this

[http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

in the smb:// place type spooler.ucs.ed.ac.uk so it would be smb://spooler.ucs.ed.ac.uk .. then your username and password as mentioned there, something like ed/xxxxx .. hope that works..

---

### Post by superprash2003 on 2008-11-12
double post...

---

### Post by Trenchcoat on 2008-11-12
Sadly no joy.

---

### Post by WrathofthePenguin on 2008-11-12
You may be running into a (presumably) samba bug. If you want to test this, boot from a 8.04 live CD and attempt to print. In 8.10 samba is dropping the last character from directory and file names in communications. I've filed a bug on this, my original post about it is here:

[http://ubuntuforums.org/showthread.php?t=968407](http://ubuntuforums.org/showthread.php?t=968407)

While I specifically experienced this using file shares I would suspect that this would affect any communication that involves samba.

Depending on how technically comfortable you are you could install wireshark and perform a packet capture to see if the last character is dropping.

Are you seeing any error messages when you try this?


EDIT:

Boy, talk about foolish...I answered a question you weren't asking. Sorry. Try this:

Go to System->Administration->Printing

Click on New Printer.

After it's done searching, a Select Connection window comes up. In the list on the left, select Windows Printer via SAMBA. On the right, in the box for smb://  enter either the IP address or fully qualified domain name (such as pcsp1.ucs.ed.ac.uk). Click the box for Authentication Required and enter the username and password (in the document above, they tell you to make sure you put the ed\ before your username - ex. ed\s0654321 ).

Now here's the fun part - it's going to contact the printer and try to determine what driver to install. I saw that there were some HP printers in the list (not the one you posted, but on one of the pages on the website the documentation referenced) which may be supported. You can look and see.

Now, back to my original answer - this may not work simply because of the samba bug. If it does not, I would not assume that it is because you set it up wrong - you may want to try the same thing under a live CD.

---

### Post by Keen101 on 2008-11-12
This should be possible without samba. It also depends on what brand of printer though. If it's an HP, then it should be fine.

I've done this once, but it was a couple years ago. Basically what you need to do is go to the printer properties on windows, and get the ip address for it. Set up printer in ubuntu, and put in the ip address. It should work fine.

---

### Post by Trenchcoat on 2008-11-14
Sorry to say that I won't have access to a live cd for a while, nor do I have user privileges for the Windows computers. I fear I may be on a hiding to nothing here.

---

### Post by matchewg on 2008-12-11
Try checking the Uni open access computer printing configurations. You can boot some of the machines in Ubuntu from the grub menu. From what I recall the machines in Appleton Tower have this ability.

---

