---
title: "Viewing Windows Shared Folders"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by ivanizm on 2008-02-05
When trying to find a way to transfer files from Windows to Ubuntu, I came accross this simple explanation: 

press ALT+F2 to begin the run dialogue, and enter:
smb:// followed by the ip address of the windows PC, followed by "/nameoffolder"
example:
"smb://192.168.2.9/shared"

It was found here: 
[http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php](http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php)

Convenient, and it worked. I bookmarked the folders for easy access from "Places" in Ubuntu.  

My question is, why is this not the most common method talked about?  And how would I have done this from terminal (ie, what are the commands).  The other options I read about involved getting Samba and going through terminal.  How exactly does the run dialogue bypass all this?

---

### Post by zarqoon on 2008-02-05
I dont really know about using smb with the console but there are commands like smbget and some others starting with smb that can most likely be used. I also think its possible to mount smb shares directly to a folder.

You dont have to get samba on your ubuntu machine because its already installed otherwise the smb:// would not work because that stands for samba. Typing that into the alt f2 menu starts nihilus which can access the samba client which in turn accesses the windows machine.

---

### Post by ivanizm on 2008-02-05
ah, of course...smb=samba.  i am a noob, as my user info suggests.  thanks very much.

---

