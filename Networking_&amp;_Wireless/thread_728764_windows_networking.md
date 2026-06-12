---
title: "windows networking"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by scaa on 2008-03-19
I have installed ubuntu 7.10 in a dual boot environment with vista basic. I have a few wired  netowrk  pc through ethernet card. All these machines run on xp and have static ip addresses as 10.0.0.1 thru x.
In windows I have no problem whatsoever in sharing contents of these pc s either way vista/xp.
In ubuntu only the windows network icon appears but nothing else on d/click.
I have tried quite a few tutorials but without any positive result. 
Samba is already installed.
As I am nooby to linux but fascinated by ubuntu, I would request the learned in this forum to please help me access the windows network from ubuntu and vice versa.
I do have firestarter also enabled running in the background

---

### Post by superprash2003 on 2008-03-19
firstly make sure you setup firestarter right.. to access a windows pc type smb://192.168.1.10 where 192.168.1.10 is the ip of the windows pc.. type it in the nautilus browser(PLaces->computer) .. or alternatively.. go to places->Connect to server

---

### Post by superprash2003 on 2008-03-19
connecting to a ubuntu pc from windows... go to windows explorer and type \\192.168.1.10 where 192.168.1.10 is ubuntu pc's ip.. for more info on setting up samba go to [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by drdos2006 on 2008-03-19
Samba is the program to connect to Windows networks from Ubuntu.

The description below is the connection process between a Netgear DG834 router, Windows 2000 Pro and a Ubuntu box, version 7.10 x86_64.
You might be prompted to install Samba or NFS for file sharing if those packages have not yet been installed, while you follow the directions below. Please install the packages. 

Sharing Directories or Folders
To share an existing Ubuntu directory with Windows networking.
From the menubar, 
select “System” -> “Administration” -> “Shared Folders” -> “Shared Folders”.
Select the folder path to be shared, share through “Windows networks (SMB)”.
Select the properties name, for instance “Big Video”, untick “Read Only” if you want Windows network users to add videos to the folder. Click “OK”.
Now select the “General Properties” and in the “Windows Sharing” section, enter the Windows Domain/Workgroup name of the Windows network group to connect to the Ubuntu box. For the “WINS server” address, the IP address of the Netgear router ( gateway ) was entered. Close the shared folder settings.

To create a new Ubuntu folder and share it with Windows networking.

From the menubar, select “Places”, browse to where the shared folder is to be created, create a folder to be shared with “File” -> “Create Folder”.
Go to “Sharing Directories or Folders” above.



Domain/Workgroup
If you have changed the default Windows XP workgroup on your Windows box, it is recommended to alter the Domain/Workgroup on the Linux box to match the Domain/Workgroup you specified under Windows. 
From the menubar,
select “System” -> “Administration” -> “Shared Folders” -> “General Properties” tab and in the “Windows Sharing” section, enter the Windows Domain/Workgroup name of the Windows network group to connect to the Ubuntu box. For the “WINS server” address, the IP address of the Netgear router ( gateway ) was entered. Close the shared folder settings.

Activating Samba
You should first activate Samba. This is done via the menubar.
Select “System” -> “Administration” -> “Services”. 
Scroll down and look for the Samba service, and activate it by ticking the box. Samba is now running.

Encrypted Passwords
If you try to access your Linux box from Windows via “Network Neighbourhood”, you may see it, but you may  not be able to connect to it, even though the correct login and password have been entered have been entered on the Windows box. 
This is because Windows XP and Samba are configured by default to send encrypted passwords over the network (this was not the case with Windows 98 and earlier releases!)

Add a Network User
On Linux, you need an additional step for each user who needs to be        authenticated on the network. This step will simply add a “network user” with a encrypted password in the Samba configuration. 
From the menubar, 
select “System” -> “Administration” -> “Users and Groups” -> “+Add User” -> “Account”. 
Add the new user and enter the password.
Select “User Priveleges” and select/de-select those items allowed for this user.
Select “Advanced” and enter the Home Directory for this user ( see Disabled Login for other settings). For the “MainGroup”, enter the Windows Domain/Workgroup name of the Windows network group. Close and save.


Alternative from Terminal.
From the menubar, 
select  “Applications” -> “Accessories” -> “Terminal” and  type the following command where you will replace username by your username (must be a valid Linux login).

$ sudo smbpasswd -a username 

This script will prompt you for the “sudo” password, and then it will prompt you for the Windows password. Set the Windows password for the user to enter from the  Windows box.

Disabled Login
If you want to authorise users on the network to access a network share but not to have a login possibility on your Linux box, then you need to create a Linux account for each user and disallow login. 

This feature is hidden inside the “Advanced” tab of the User account creation window (see “System” -> “Administration” -> “Users and Groups” -> “+ Add User” or select an existing user to change the “Properties” of the existing user). 

Select “Advanced”, “/dev/null” for the home directory, “/bin/false” for the shell,  in “MainGroup”, enter the Windows Domain/Workgroup name of the Windows network group. Close and save.
In the “User Privileges” tab, deselect everything. 
Once this user has been created, you can perform the steps mentioned above to create the corresponding network user. In that way, your network users will not login via Gnome or a shell, but can access your shared folders.

Add a New Group
From the menubar,
select “System” -> “Administration” -> “Users and Groups” -> “Manage Groups”.
Select “+Add Group”, type in the Group name of the Windows Domain/Workgroup, tick the users to be added to the group. Close and save.

For the Windows Network, “Map a Network Drive”
From the menubar on the Linux box, 
select  “Applications” -> “Accessories” -> “Terminal” and  type the following command.
$ ifconfig
The first line will show the connection type and the hardware address of the network interface card. ( MAC address of the NIC ).
The second line will show the IP address (inet addr:) of the Linux box, e.g. 192.168.0.12. Use this IP address in the Windows box to map the network neighbourhood drive. From the Windows box, select “My Network Places”, right mouse click to “Map a Network Drive”, select a drive from the drop down list. 
In the Folder section, type in the IP address of the Linux box and the shared folder in the following manner.  \\192.168.0.12\Big Videoor browse to the Linux box and select the shared folder.


Sharing Printers
Once the user connected to the network drive, the printer should be able to be seen from the Windows box. 
Select “My Network Places” -> “Computers Near Me” -> the Linux box. 
Windows will require the Windows drivers for the respective printer. 
To enable the printing process from a Windows network, the CUPS configuration file needs to be added to.
Stop CUPS from the menubar.
Select “System” -> “Administration” -> Services”.
Untick the box “Printer service (cupsys)”, close and save.

From the menubar on the Linux box, 
select  “Applications” -> “Accessories” -> “Terminal” and  type the following command.

sudo gedit /etc/cups/cupsd.conf

Look for 

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

---

### Post by scaa on 2008-03-20
Thanks drdos2006.
The only clarification I need is whether ip address is to be as you have mentioned 192.168 etc or it is fine with the way I have configured(10.0.0.1 etc)

---

### Post by superprash2003 on 2008-03-20
you can use any ip address

---

### Post by drdos2006 on 2008-03-20
yes, that is correct. The IP address of the router gateway on my network is 192.168.0.1 and the IP address of my Ubuntu machine is 192.168.0.12.

I started the above breakdown of procedures as a more detailed description supplied by superprash2003 and others in this forum regarding connecting wired Windows network to Ubuntu box and printer. I hope it helps someone in the future. Feel free to add your comments when you have your network connected.

regards

---

