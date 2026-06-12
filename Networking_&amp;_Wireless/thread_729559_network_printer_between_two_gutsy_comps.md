---
title: "network printer between two gutsy comps"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by antisocialist on 2008-03-20
i a have wireless gutsy laptop and a wired gutsy desktop, printer is connected to desktop, how can i network the printer to also work from the laptop? all the guides i have seen have either been confusing or for dapper or for networking windows-linux

---

### Post by drdos2006 on 2008-03-20
Try this. It is for a Windows based network but it appears it would help you as well.

Sharing Printers
Once the user is connected to the network drive, the printer should be able to be seen from the Windows box. 
Select “My Network Places” -> “Computers Near Me” -> the Linux box. 
Windows will require the Windows drivers for the respective printer. 

To enable the printing process from a Windows network, the CUPS configuration file needs to be added to.
Stop CUPS from the menubar.
Select “System” -> “Administration” -> Services”.
Untick the box “Printer service (cupsys)”, close and save.

From the menubar on the Linux box, 
select  “Applications” -> “Accessories” -> “Terminal” and  type the following command.

sudo gedit /etc/cups/cupsd.conf

Look for : 
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all

Add the following line:
	BrowseProtocols all
Save the file and close, restart the printing service.

Start CUPS from the menubar.
Select “System” -> “Administration” -> Services”.
Tick the box “Printer service (cupsys)”, close and save.

From the Windows box, print a test page.

regards

---

### Post by HereInOz on 2008-03-20
You may also have to change this section in your cupsd.conf file

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 192.168.1.3:631

(192.168.1.3 is the IP address of the machine with the printer on it)

You then connect your other machine to that printer using an internet printer type of connection with the IP address, the port number and (from memory) /printers/name of printer.

---

### Post by antisocialist on 2008-03-22
@ first post
i have two gutsy comps, 0 windows ones, so not much use 2 me D:

---

### Post by drdos2006 on 2008-03-22
All the information you need is there but it appears you may need step by step instructions :)
Step 1: Have you installed your priter and shared your printer ?
If not, install your printer, then from the menubar, 
select System -> Administration -> Printing -> YourPrinterName -> Policies and tick the box "Shared".
[edit]
The other thing is that Ubuntu will require a laptop user name to allow the laptop to connec to the shared printer. You can set this up via 
 System -> Administration -> Users and Groups and add your laptop user name.
If you want to authorise users on the network to access a network share or shared printer but not to have a login possibility on your Linux box, then you need to create a Linux account for each network user and disallow login. 

This feature is hidden inside the &#8220;Advanced&#8221; tab of the User account creation window (see &#8220;System&#8221; -> &#8220;Administration&#8221; -> &#8220;Users and Groups&#8221; -> &#8220;+ Add User&#8221; or select an existing user to change the &#8220;Properties&#8221; of the existing user). 

Select &#8220;Advanced&#8221;, &#8220;/dev/null&#8221; for the home directory, &#8220;/bin/false&#8221; for the shell,  in &#8220;MainGroup&#8221;, enter the Windows Domain/Workgroup name of the Windows network group. Close and save.
In the &#8220;User Privileges&#8221; tab, deselect everything. 
Once this user has been created, you can perform the steps mentioned above to create the corresponding network user. In that way, your network users will not login via Gnome or a shell, but can access your shared folders.

regards

---

