---
title: "Sharing Ubuntu printer with Windows XP"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Animortis on 2008-03-24
I have an Ubuntu 7.10 Desktop with an HP printer and scanner connected to it, wired to a wifi router. I also have a Windows XP laptop wirelessly connected to the network. I have succeeded in letting the Ubuntu PC access the laptop for file sharing (Though not the other way around, that's for later though) but I'd like the laptop to connect to the printer on my desktop.

Does anyone know a way to share this printer? I've tried the WIKI, but nothing had happened. I suspect I need a better means of determining my printer name for the network...

---

### Post by chuckH on 2008-03-25
Here's a short how to guide I wrote for my own use.
It's basic wired/wireless networking and has worked
for me in 7.10. With proper permission folders/printers
are shared. Don't forget to share your printer on the 
Linux box. Also a good hard reboot on your router
makes a difference or just wait a day or 2. 
Overall I have everything working that I want, with no trouble.
Read my notes and it's VERY,VERY easy & quick.
Let me know if I can help more. Cheers...

If you are at the point of seeing and accessing window shares from Linux, but can't access Linux
folders from xp try this. Install SAMBA FIRST!
Found at Synaptic package manager. I checked & installed the samba packages and the 
smb and swat packages. Also check system-administration-services
be sure samba is running in server settings

1. You cannot be logged in to Ubuntu more than once. So the windows xp box needs to log in with a different account than what is running on the ubuntu machine. 

2a. The second account needs to be both a ubuntu user (added in Users and Groups under administration) 

2b. The second account should be a basic user not with admin. permissions) Now create a samba user. From the terminal, type

sudo smbpasswd -a username 
first try is your root password, so replace username above with
the root password.
2nd is the new pass for the samba account
to add a samba user. Adding a user to samba will fail
if you didn't add that same user in the O.S. as a user.

It will then ask for a password. Just make sure the password AND the username are the same for Ubuntu and Samba. Hopefully you should be able to log in then from the XP machine.

Double check, you have made the folder sharing
in Linux and check the permissions.
Also System-administration-shared folders-General Properties
there you can change the domain name.

This has worked for me and everything is networked and shared with proper permissions
in less then 10 minutes.

Good luck

---

### Post by Animortis on 2008-03-27
That worked, actually. I had to bare-bones install 7.10 on a separate partition, but it worked. Now I can't get the XP laptop to detect the printer connected to the Gutsy print server. When it browses for printers on the network through the "Add a printer" wizard, it detects the server but won't display any printers on it.

---

### Post by superprash2003 on 2008-03-28
go to your terminal and type sudo gedit /etc/samba/smb.conf
 then look for the line
 ; printing = cups
  ; printcap name = cups

replace it with 
  printing = cups
  printcap name = cups

i.e. just remove the colon.Then restart samba by typing sudo /etc/init.d/samba restart

---

### Post by Animortis on 2008-03-28
> **superprash2003 said:**
> go to your terminal and type sudo gedit /etc/samba/smb.conf
 then look for the line
 ; printing = cups
  ; printcap name = cups

replace it with 
  printing = cups
  printcap name = cups

i.e. just remove the colon.Then restart samba by typing sudo /etc/init.d/samba restart

This did not work. The XP machine still cannot browse for network printers on the Ubuntu PC, even though it can safely file browse it.

Further, when I enter the URL for it via the net, [http://SERVERNAME:631/printers/PRINTERNAME](http://SERVERNAME:631/printers/PRINTERNAME), the "Add a printer wizard" in Windows crashes.

---

### Post by superprash2003 on 2008-03-28
in the add printer wizard try accessing like this \\servername\printername or \\servername\printers\printername

---

### Post by Animortis on 2008-03-29
> **superprash2003 said:**
> in the add printer wizard try accessing like this \\servername\printername or \\servername\printers\printername

Success! This worked as needed and now I have a networked printer serving everything I need for printers! I am very happy since this was a huge pain in the butt when there was only a few steps involved. Someone needs to update the wiki... I can but I doubt that anyone would let me.

Thank you!:KS

---

