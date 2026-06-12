---
title: "Cannot use Sudo when logged onto MS network"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by espresso_steve on 2009-10-21
Hi. 
 
I'm totally new to Ubuntu / linux. I'm a Microsoft network admin guy... Don't hate me .. it's my job! Anyway, I wanted to improve things, so when we needed a webserver I went for Ubuntu server 9.04. Installed it with no issues. Installed Xampp (incl. apache / MySql / php etc.) and finally to get it talking to the rest of the MS SBS 2003 active directory, I used 'Likewise' ... and , hey, that works ok too! 
 
BUT... now I'm logged into the local MS network on the Webserver as MSDOMAIN\Administrator and it will not let me use the Sudo command, saying user not in Sudoer file. 'Likewise' forum has a few older version instances of Sudoer file being deleted - but mine is still in tact. I cannot edit or add users to it as I cannot use Sudo. I can't start the Xampp tools either as i need root permissions to start these services. 
 
Any ideas on how to overcome this? 
 
Cheers

---

### Post by lavinog on 2009-10-21
How are you entering commands into the webserver?
are you using a terminal or ssh?

In order to use sudo the user needs to be a member of the admin group.  The only user that will be a member of the admin group will be the user you setup during the install.

---

### Post by espresso_steve on 2009-10-21
I'm using a Terminal. Can a MS network user be added to the local admin group?
 
I just tried going in as the username at setup & if I try 'sudo adduser MSDOMAIN\Administrator' it doesn't like the slash.

---

