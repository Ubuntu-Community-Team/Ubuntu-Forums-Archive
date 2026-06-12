---
title: "Networking with Windows XP"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by BPak on 2008-08-12
I have TWO computers

Main computer has Windows XP SP2 and connects to internet with dial up modem.

It also acts as the server for LAN through Workgroups (mshome).

My other computer has two  hard drives 
(a) windows XP and is networked to the Main computer. Works fine.
(b) Ubunto 7.04 and is networked to Main computer. Can obtain data from Main Computer over to Ubunto ok.

Problem is when on the main computer I can not get access to the Ubunto HD.

Windows XP asks for User name and Password:

I have tried different Username and Password but Windows just puts up the User computer name and wont allow me to enter.

Any clues please?

---

### Post by Iowan on 2008-08-12
Do you have the Samba Server installed? (Client usually comes installed - that's why you can see the Windows boxes.) If so, have you set up a user (easiest with same Windows username) on Ubuntu and in Samba?

Is that 7.04 (Feisty?) or 8.04 (Hardy)?

---

### Post by BPak on 2008-08-13
Yes Samba is Installed.

> If so, have you set up a user (easiest with same Windows username) on Ubuntu and in Samba?


Do I set that up on Ubuntu?

If so How?

I dont have to log on in Windows on that computer. 

Thanks.

---

### Post by Iowan on 2008-08-14
**smbpasswd** is the command to set up a Samba user (you'll want to check the **man smbpasswd** page for options).  I'm not sure what Windows uses as a username if it doesn't require a login.

Check post #5 [here]("http://ubuntuforums.org/showthread.php?t=886370") for how to verify Samba server is running.

---

### Post by BPak on 2008-08-14
Thanks. Will work with that.
Tried setting permissions on HOme folder yesterday thinking that would do it. Set the Owner  - BPak Access read write and Group - bpak access: read write  others access: read only.  But alas it caused a message to come up this morning when loading Ubuntu.

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

They originally had just a dash line for the ACCESS  -  
How can I set 644 for the Home Folder and BPak folder, please?

EDIT:

Found answer to this $HOME/.dmrc problem at:

[http://ubuntuforums.org/showthread.php?t=890244&highlight=chmod](http://ubuntuforums.org/showthread.php?t=890244&highlight=chmod)

Thanks

---

