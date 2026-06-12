---
title: "Home network with Ubunto and Windows XP"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Jou Moer on 2006-08-03
New to the World of Linux - it's my third day today.  I have a question though.  I did a bit of a search on the formus, but could not find what I'm looking for.  I few things that I thought I found, was too 'complicated' for me to get the hang of, so I'm still clueless as to what and how to do.  Still looking for an idiot's guide...

Anyway, this is what I have and what I want:  I want to set up a home network/workgroup with 2 machines and the availability to add another machine later on.  To complicate things there's a Windows XP machine involved.

I have BT broadband and the physical setup is as follows: Internet -- Voyager Router -- Netgear 8 port Switch. Connected to the switch I have my Ubunto machine and my Windows XP machine. (Star topology)  My idea for a later addition is to add an Edubunto thinclient box for my son to play on.  IP addresses are DHCP from the router in the 192.168.0.x range

I want the machines to see each other and share files.  As the Ubunto box has an additional harddrive, I want to use it as a file storage area. I want to be able to copy files from one to another and vice versa, even be able to RDP both ways.  My printer is physically connected to the XP box so I would like to be able to print to it from the Ubunto box.

Phew; that's it...

BTW, love Ubunto, it reminds me of the Homeland...

---

### Post by huygens on 2006-08-03
What you need is Samba.
It is pretty easy to set-up in Ubuntu and quite the same on Windows XP. And you will be able to share directories and printers.

_**Sharing Directories**_
So let's start by looking for a shared directory. So, I’ve used Nautilus to navigate to my home folder (Menu item “Places” -> “Home Folder”). I have created a new directory and I have right click on it after. In the menu, I have selected “Share Folder”. You might be prompt to install Samba or NFS for file sharing if those packages have not yet been installed. To share files with Windows, it is recommended to use the Samba service. You will then get a dialog box.
[IMG]http://jcberthon.free.fr/ice_and_fire/wp-content/ubuntu-settings-share-folder.png[/IMG]
In “Share with”, you should select SMB which stands for the protocol name used by Microsoft for file sharing (recently Microsoft changed the name, but SMB still stick to it…) and also as a shortcut for Samba.
You will get a new window like this:
[IMG]http://jcberthon.free.fr/ice_and_fire/wp-content/ubuntu-settings-share-smb.png[/IMG]

Basically, you should only need to set a network share name in the field “Name:”, and validate your entry. You might want to have a look at the other options to tune the way your share will be available.

Also, if you have changed the default Windows XP workgroup on your Windows system, it would then be recommended, to click on the “General Windows sharing settings” button and modify the “Domain / Workgroup” field to match the one you specified under Windows.


 However, if you just installed Samba during this phase you are not completly done. You should first activate Samba. This is done in the menu “System” -> “Administration” -> “Services”. There you scroll down and look for the Samba service, and you just have to activate it by checking it. Samba is now running.

Nevertheless, you are still not ready. If you try from Windows to access your Linux box, you will see it, but strangely you cannot connect to it, eventhough you have entered the correct login and password. This is because Windows XP and Samba are configured by default to send password encrypted over the network (this was not the case with Windows 98 and earlier release!)


 On Linux, you need an additional step for each user that needs to be authenticated on the network. This step will simply add a “network user” with a encrypted password in the Samba configuration. You need to go in a terminal (menu “Applications” -> “Accessories” -> “Terminal”) and there you type the following command where you will replace *username* by your username (must be a valid Linux login).
 $ sudo smbpasswd -a *username* This script will probably prompt you for the “sudo” password, and then it will prompt you for the SMB password. Please, set there the password you wish to enter from Windows.


 You could add this operation when creating new user, so it would become transparent for you. I do not have right in mind how to proceed, I might update this article soon, when I feel the need for this feature.


 Also, if you want to authorise a friend to access a network share but not to have a login possibility on your Linux. You need to create a Linux account for him and disallow login. This featute is hidden inside the “Advanced” tab of the User account creation window (see “System” -> “Administration” -> “Users and Groups” -> “+ Add User”). You need to select “/bin/false” for the Shell, and type “/dev/null” (without the double-quotes of course) for the home directory. In the “User Privileges” tab, deselect everything. Once this user has been created, you can perform the step, mentioned above using smbpasswd command, to create the corresponding network user. In that way, your friend will have no possible login via Gnome or a shell. But can access your shared folders. 

_**Sharing Printers**_
Heee.... well for that one, I do not have a printer, so I do not know the exact step to reproduce it. But, I already done it in the past at my work and it was easy. I just cannot remember the steps... Sorry, hopefully someone will help you out :D

Huygens

---

### Post by ahh_Jebubs on 2006-08-23
> **huygens said:**
> You need to go in a terminal (menu “Applications” -> “Accessories” -> “Terminal”) and there you type the following command where you will replace *username* by your username (must be a valid Linux login).
 $ sudo smbpasswd -a *username* This script will probably prompt you for the “sudo” password, and then it will prompt you for the SMB password. Please, set there the password you wish to enter from Windows.
Huygens

Thank you,
I could connect to XP shares from Ubuntu but not other way around. One less problem to worry about now :)

---

### Post by huygens on 2006-08-23
> **ahh_Jebubs said:**
> Thank you,
I could connect to XP shares from Ubuntu but not other way around. One less problem to worry about now :)

I'm really happy it helped you :)

---

### Post by dannyboy79 on 2006-08-23
It is quite simple to access a shared printer from Ubuntu that is hooked to your WINXP box. First, in WINXP, go to your start menu and under settings go to printers and faxes. Then right click on your default printer, go to the sharing tab and check the box to share the printer and give it a name. Then go to your start menu and go to settings again and then go to control panel, then go to Add remove programs. Within there you want to click on Add Remove Windows Components. You want to look for something that says "Other Network and FIle Print Services" and you want to check the box. You might need to put in your WINXP cd for this I forget. Ok that should be it for the Windows Box. Go over to your Ubuuntu box and go to the Administration pull down and choose printing. Then click add printer, the choose network printer, then printer over smb I think (I am not at my ubuntu box so I don't exactly recall), then you'll have to enter your WINXP IP address in the host box and the EXACT name of the printer in the printer name box, then click on continue, then you need to look for the actual model of your printer within the pull down list of printers, hopefully you find it, chose it and you should be done. Do a test print to verify it works and you should be all set! If you get stuck send me a PM and maybe I can help when I am at home. 
PS (I also set up my Xubuntu laptop to print to my WINXP box using the CUPS web browser config page, I think you type in [http://localhost:691/printers](http://localhost:691/printers) or something like that in your browser, THAT'S NOT CORRECT BUT it's close I think)

---

### Post by wheels5894 on 2006-08-23
Thanks, Huygens! I have been studying the Samba file for ages tyring to work out what was wrong. Now everything is working. Great!! :-D

---

### Post by vycman on 2006-08-24
Hi guys! I'm trying to print with my Upuntu Dapper from a Windows Xp OS. I followed this guide: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) but nothing happens, when clicking "print" on XP. It appears that the XP sees my PSC-1400, because when I set it with this link: [http://192.168.0.175:631/printers/PSC-1400](http://192.168.0.175:631/printers/PSC-1400) , it accepts that, and make a Printer: [http://192.168.0.175:631](http://192.168.0.175:631) . What can I do? Please help me!!! Oh, I see this in the Administration-Printers section:

PSC-1400
Printing
4 jobs

---

### Post by gready on 2006-08-24
I have an issue browersing my xp box from ubuntu.  I can print from ubuntu to xp and can brows from xp to ubuntu but when I go Place -> Network Servers ->Windows Network->*workgroup*  I get *Sorry, couldn't display all the contents of "Windows Network: workgroup".*.

I can browers my xp box if I type in the ip address but not with the computer name

I am also having truble mounting the xp shares.

thanks

---

### Post by huygens on 2006-08-24
> **gready said:**
> [...]when I go Place -> Network Servers ->Windows Network->*workgroup*  I get *Sorry, couldn't display all the contents of "Windows Network: workgroup".*.[...]
Perhaps, could you open a terminal (or console) and go to this directory Samba log directory:
```
cd /var/log/samba/
```
Then, do you find a file named like 'log.<your_XP_hostname>'?
If yes, could you post here the most recent part of this file?

Huygens

---

### Post by huygens on 2006-08-24
So printing....
Well I do not use printer since ages, so I will tell you what I still remember from my past experience, but you will need to adapt it to Ubuntu.

For sharing a printer on the network, I was using the SMB protocol and sharing the printer, much like you do it under Windows. As I have no printer I do not know if there is a user intereface for it on Ubuntu, but here is how to tweak it from the configuration file directly.
You need to modify your file smb.conf which is in the /etc/samba directory. Let's first back-up it and then modify it.
```
cd /etc/samba
sudo cp -p smb.conf smb.bkp
gksudo gedit smb.conf
``` Then you have a graphical editor opened which can write inside the smb.conf file. You should look for the line containing: ########## Printing ##########
Under you will find 2 lines like this:
```
;   printing = cups
;   printcap name = cups
``` Simply remove the semi-colon ';' at the beginning of the line so it looks like this:
```
   printing = cups
   printcap name = cups
``` Click on the save button and exit the editor. Now that Sama configuration has been updated, you need to reload the Samba service so it will re-read its configuration file. Go back to the terminal and type this:
```
sudo killall -HUP smbd
``` Do not be scared by the name 'killall', it just means that it is going to send the signal SIGHUP (because I have the option -HUP) to any process that have smbd in their names. No one is hurt ;-)

Wait a short while and then from your other PC, go browsing your network. Find your Ubuntu computer sharing the printer, and explore its shares. You will see that there is a printer among the shares. Double-click on it should install it (under Windows XP, it is the way, do not know for other systems)

Huygens

**Note**: you must have your printer properly configured under CUPS (I mean that you can print from the PC where the printer is directly plugged)

---

### Post by vycman on 2006-08-24
Thanks, I tryed this, but the XP tells: Access Denied, unable to connect.

When I'm trying to print with URI, the document appears in the printing list, but my printer is flashing and writin: Error

---

### Post by huygens on 2006-08-25
> **vycman said:**
> Thanks, I tryed this, but the XP tells: Access Denied, unable to connect.

When I'm trying to print with URI, the document appears in the printing list, but my printer is flashing and writin: Error

When exactly do you get this "access denied"?
You need to define users allowed to access your shares, just like I explained in this message: [http://www.ubuntuforums.org/showpost.php?p=1333185&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1333185&postcount=2)
There is a paragraph starting with: "Nevertheless, you are still not ready." read and follow subsequent instructions written in this message from that point.

Huygens

---

### Post by Nosferatu on 2006-08-26
Okay, you guys make me feel like a genius! I just did it. Now I have a shared printer!  Thank you so much!
Nosferatu

---

### Post by tarclee on 2006-09-04
i have done as u say.but when i am in the window pc click the ubuntu pc,it ask me the username n password,so what should i put?

---

### Post by huygens on 2006-09-04
> **tarclee said:**
> i have done as u say.but when i am in the window pc click the ubuntu pc,it ask me the username n password,so what should i put?

The username you have to enter is the username that you would use on the Ubuntu PC to access the share drive you are interested in. As for the password, it is the password you set via the command smbpasswd.
You can set this password just like I explained in this message: [http://www.ubuntuforums.org/showpost.php?p=1333185&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1333185&postcount=2)
There is a paragraph starting with: "Nevertheless, you are still not ready." read and follow subsequent instructions written in this message from that point.
The username you have to use for the smbpasswd command is the same as the one I was mentionning above.

I hope this help,

Huygens

---

### Post by walter_j on 2008-03-08
thanks huygens. i had throuble logging into ubuntu from vista, but i can now.

maybe this is a similar issue to logging into mysql on ubuntu from vista?

---

### Post by ItalOz on 2008-03-08
> **huygens said:**
> What you need is Samba.
It is pretty easy to set-up in Ubuntu and quite the same on Windows XP. And you will be able to share directories and printers.

[snip]

Huygens

Thanks so much it worked like a charm!

---

### Post by dogdog on 2008-03-12
> **huygens said:**
> What you need is Samba.
It is pretty easy to set-up in Ubuntu and quite the same on Windows XP. And you will be able to share directories and printers.

_**Sharing Directories**_
So let's start by looking for a shared directory. So, I’ve used Nautilus to navigate to my home folder (Menu item “Places” -> “Home Folder”). I have created a new directory and I have right click on it after. In the menu, I have selected “Share Folder”. You might be prompt to install Samba or NFS for file sharing if those packages have not yet been installed. To share files with Windows, it is recommended to use the Samba service. You will then get a dialog box.
[IMG]http://jcberthon.free.fr/ice_and_fire/wp-content/ubuntu-settings-share-folder.png[/IMG]
In “Share with”, you should select SMB which stands for the protocol name used by Microsoft for file sharing (recently Microsoft changed the name, but SMB still stick to it…) and also as a shortcut for Samba.
You will get a new window like this:
[IMG]http://jcberthon.free.fr/ice_and_fire/wp-content/ubuntu-settings-share-smb.png[/IMG]

Basically, you should only need to set a network share name in the field “Name:”, and validate your entry. You might want to have a look at the other options to tune the way your share will be available.

Also, if you have changed the default Windows XP workgroup on your Windows system, it would then be recommended, to click on the “General Windows sharing settings” button and modify the “Domain / Workgroup” field to match the one you specified under Windows.


 However, if you just installed Samba during this phase you are not completly done. You should first activate Samba. This is done in the menu “System” -> “Administration” -> “Services”. There you scroll down and look for the Samba service, and you just have to activate it by checking it. Samba is now running.

Nevertheless, you are still not ready. If you try from Windows to access your Linux box, you will see it, but strangely you cannot connect to it, eventhough you have entered the correct login and password. This is because Windows XP and Samba are configured by default to send password encrypted over the network (this was not the case with Windows 98 and earlier release!)


 On Linux, you need an additional step for each user that needs to be authenticated on the network. This step will simply add a “network user” with a encrypted password in the Samba configuration. You need to go in a terminal (menu “Applications” -> “Accessories” -> “Terminal”) and there you type the following command where you will replace *username* by your username (must be a valid Linux login).
 $ sudo smbpasswd -a *username* This script will probably prompt you for the “sudo” password, and then it will prompt you for the SMB password. Please, set there the password you wish to enter from Windows.


 You could add this operation when creating new user, so it would become transparent for you. I do not have right in mind how to proceed, I might update this article soon, when I feel the need for this feature.


 Also, if you want to authorise a friend to access a network share but not to have a login possibility on your Linux. You need to create a Linux account for him and disallow login. This featute is hidden inside the “Advanced” tab of the User account creation window (see “System” -> “Administration” -> “Users and Groups” -> “+ Add User”). You need to select “/bin/false” for the Shell, and type “/dev/null” (without the double-quotes of course) for the home directory. In the “User Privileges” tab, deselect everything. Once this user has been created, you can perform the step, mentioned above using smbpasswd command, to create the corresponding network user. In that way, your friend will have no possible login via Gnome or a shell. But can access your shared folders. 

_**Sharing Printers**_
Heee.... well for that one, I do not have a printer, so I do not know the exact step to reproduce it. But, I already done it in the past at my work and it was easy. I just cannot remember the steps... Sorry, hopefully someone will help you out :D

Huygens


I have the same issue but my windows PC is Vista.

I am having problems following your instructions and have a number of queries:

1) Do I have to also install samba on my Vista PC (or will Vista capabilities be OK)?

2) How do I configure ubuntu firewall. I have used Firestarter to enter address of Vista PC to allow in bound traffic?

3) Is there some additional steps when using Vista rather than XP?

My aim is to access ubuntu PC from Vista PC.

Many thanks

---

