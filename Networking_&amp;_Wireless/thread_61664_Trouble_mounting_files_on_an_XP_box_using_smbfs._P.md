---
title: "Trouble mounting files on an XP box using smbfs. Please help!"
date: 2005-09-01
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2005-09-01
Hi, I'm trying to set up a home network between a Windows XP box, and an old box running XFCE in Ubuntu. I have Samba on the Ubuntu machine, and have successfully set up Samba to allow the XP box to read files on the Ubuntu box. However, I'm having trouble getting file-sharing to work in the other direction.
On the XP box, I have enabled sharing on the folder "itunes_music". 
The ip of the Ubuntu box is:  68.113.210.173
The ip of the XP box is: 68.113.210.199
The workgroup name is: @HOME
The netbios name of the XP box is: Cm35669-A
And the hostname of the Ubuntu box is: mcomp
On the XP box, the username with admin priveledges is: "Jake"
This username uses the password: "password"
(The username and password I've listed here are, of course, fake. But all the information is coherent nevertheless   :smile: )

I use the following command to mount the folder as a filesystem in Ubuntu:

sudo mount -t smbfs //68.113.210.199/itunes_music/ /media/smb -o username="Jake",workgroup="@HOME",password="password",netbios="mcomp",debug="4"

Which returns the following output:

passthrough options 'netbios=mcomp'
mount.smbfs started (version 3.0.10-Ubuntu)
added interface ip=68.113.210.173 bcast=68.113.210.255 nmask=255.255.255.0
Connecting to 68.113.210.197 at port 445
8433: session request ok
Serverzone is 18000
8433: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

I've also tried it using the XP box's netbios name substituted for the ip address:

sudo mount -t smbfs //Cm35669-A/itunes_music/ /media/smb -o username="Jake",workgroup="@HOME",password="password",netbios="mcomp",debug="4"

This returns the exact same output.

Does anybody have any idea what the problem is here? Or how I can debug it? 
Thanks.

-Jake

---

### Post by otakuj462 on 2005-09-01
Here's more info. I tried to use smbclient to return a list of shared folders, and it failed too:

smbclient --user="Jake" --list="Cm35669-A"

And then, when prompted, I entered the correct password. It returns the following error message:

session setup failed: NT_STATUS_LOGON_TYPE_NOT_GRANTED

Trying again, if I enter no password, it returns different output:

Domain=[@HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[@HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

Finally, if I use a false password, it again returns:

session setup failed: NT_STATUS_LOGON_TYPE_NOT_GRANTED


Perhaps the difficulty is with the password? But why would that be? Again, any info or ideas would be appreciated. 
Thanks.

-Jake

---

