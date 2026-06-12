---
title: "Adding Network Printer"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by Dhrystone@comcast.net on 2010-03-26
Hi everyone.

I'm an absolute beginner to Ubuntu (9.04) Linux, and have a pretty decent grasp on most things within the Ubuntu desktop, except one item: getting a network printer added.

I've gone through the process outlined in documentation on this Website, but for some reason the system doesn't recognize that there's a printer to be added. FYI: The printer is added to a Windows desktop machine, and I'm trying to get it added to my Dell Inspiron 1525 laptop.

Do I have to determine whether or not the printer has Linux drivers available for it in order to add it, or should it be able to be added nonetheless?

Thanks in advance!

Dhrystone

---

### Post by jaycee23 on 2010-03-26
Is the Windows machine on your network - if so can you see any shared files on it from Ubuntu?

The biggest problem is getting Ubuntu to see your network - assuming it a windows network.

I found this link useful if it is a Windows share issue
[http://ubuntuforums.org/showthread.php?t=1169149&highlight=Failed+retrieve+share+list+server](http://ubuntuforums.org/showthread.php?t=1169149&highlight=Failed+retrieve+share+list+server)

Hope this is of some use!

---

### Post by plucky on 2010-03-27
> **Dhrystone@comcast.net said:**
> Hi everyone.

I'm an absolute beginner to Ubuntu (9.04) Linux, and have a pretty decent grasp on most things within the Ubuntu desktop, except one item: getting a network printer added.

I've gone through the process outlined in documentation on this Website, but for some reason the system doesn't recognize that there's a printer to be added. FYI: The printer is added to a Windows desktop machine, and I'm trying to get it added to my Dell Inspiron 1525 laptop.

Do I have to determine whether or not the printer has Linux drivers available for it in order to add it, or should it be able to be added nonetheless?

Thanks in advance!
Dhrystone

It might help if you tell us the Make and Model of the printer.

---

### Post by Gixxy on 2010-03-27
I think the biggest question here is....

Is it an actual networked printer (has a network card in the printer) or is a shared printer from your windows box?

---

### Post by Dhrystone on 2010-03-27
The printer is an HP DeskJet 5550 Series inkjet printer, and it's connected to a Dell Dimension desktop machine running Windows Vista Home edition. Printer sharing is turned on. My apologies, as it's not a true "network" printer (no NIC in the printer).

---

### Post by jimmy the saint on 2010-03-27
Go to:
System> Administration > Printing

Then inside the printing dialog
Server> Settings

Check the "show printers shared by other systems" box.

Reboot your system (or restart cups, but rebooting is easier IMHO)

The shared printer should show up when you go to pring documents.  Worked for me.

---

### Post by Morbius1 on 2010-03-27
[] Can Ubuntu even see the printer?

Open **Terminal**
Type **smbtree**
[COLOR=Blue][I]This should list any shares you have on Vista including the printer. 

[/I][COLOR=Black]If it outputs any errors post then.[/COLOR][/COLOR] If it can't see anything it might be something as simple as the Windows firewall getting in the way.

[] How are you trying to add the printer? Something like this:

Administration > Printing > New > Windows Printer via Samba > Browse.

Sometimes it needs a little help. If it can't find anything you may have to fill in the dialog box, examples:

[smb://workgroup_name/MACHINE_NAME/WinPrinter](smb://workgroup_name/MACHINE_NAME/WinPrinter)
[smb://machine_name/WinPrinter](smb://machine_name/WinPrinter)
[smb://192.168.0.100/WinPrinter](smb://192.168.0.100/WinPrinter)

Are you sure CUPS is running?

Open **Terminal**
Type **sudo service cups restart**
[COLOR=Blue]*This will start it if it's not running or restart it if it is.*[/COLOR]

---

### Post by Dhrystone on 2010-03-27
How do I determine whether CUPS is running or not?

---

### Post by Morbius1 on 2010-03-28
>  		How do I determine whether CUPS is running or not? 	

My apologies, I didn't quite make that clear in my post:
> Open **Terminal**
Type **sudo service cups restart**
[COLOR=Blue]*This will start it if it's not running or restart it if it is.*[/COLOR]

The "sudo service cups restart" will start it if it's currently running or not.

I'm guessing though that you ran that command anyway and it did not resolve your problem. Did "smbtree" show you the Windows shared printer?

---

