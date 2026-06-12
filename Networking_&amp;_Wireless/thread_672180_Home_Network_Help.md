---
title: "Home Network Help"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by durdensbuddy on 2008-01-19
Completely new to linux, maybe a week here and lost!  I am attempting to follow the walkthrough for setting up a home network/configuring samba [B][http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)
[/B]
but when i get to the **sudo smbpasswd -a system_username** command and enter in a password i receive the following error ** Failed to modify password entry for user system_username**

I tried several p/w including my current root user p/w same message.  I then thought, HEY, maybe I need to create a user first!  so i skipped to the next line of instruction **gksudo gedit /etc/samba/smbusers**  edited the file and saved.  Then i tried **sudo smbpasswd -a newusername**  as asked for a password and received the same error.  

I would appreciate any help.  And bear with me, I may be presenting as needing to be spoonfed, but Ubuntu is so completely alien to me. 

Also, I am running Ubuntu 7.10 amd64

---

### Post by sisco311 on 2008-01-19
> **durdensbuddy said:**
> Completely new to linux, maybe a week here and lost!  I am attempting to follow the walkthrough for setting up a home network/configuring samba [B][http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)
[/B]
but when i get to the **sudo smbpasswd -a system_username** command and enter in a password i receive the following error ** Failed to modify password entry for user system_username**

I tried several p/w including my current root user p/w same message.  I then thought, HEY, maybe I need to create a user first!  so i skipped to the next line of instruction **gksudo gedit /etc/samba/smbusers**  edited the file and saved.  Then i tried **sudo smbpasswd -a newusername**  as asked for a password and received the same error.  

I would appreciate any help.  And bear with me, I may be presenting as needing to be spoonfed, but Ubuntu is so completely alien to me. 

Also, I am running Ubuntu 7.10 amd64
replace system_username with your username (ex. **sudo smbpasswd -a** durdensbuddy)

---

### Post by durdensbuddy on 2008-01-19
WOW, Here's my sing.  Thanks for the help.  that allowed me to get through and finish the walk through yet, I'm still unable to see my network, or be seen by the other computer a winxp

---

