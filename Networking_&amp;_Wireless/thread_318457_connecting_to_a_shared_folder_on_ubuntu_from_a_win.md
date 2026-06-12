---
title: "connecting to a shared folder on ubuntu from a windows pc"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by mixhard on 2006-12-14
im running ubuntu off a bootable disc, and i have a usb harddrive with files i cannot access from a windows machine. they are saved in an EFS format. i can view the files with ubuntu, so i want to share the folder on my home network so i can copy the files over to a windows pc. but when i install samba, i still cannot access the ubuntu machine from my windows xp machine. i go to add a network place, and when i try to open/explore the ubunu machine it asks for a username and password, and i've tried the ubuntu as the username and nothing as the password, as well as i have tried changing the admin password and still cannot log in to view the shared folders. i've also tried adding another user account with admin type privleges. and it still wont log in with that info. i dont get an error, it just brings me back to the login window.


any help would be greatly appreciated.

---

### Post by Cderugg on 2006-12-14
First I'm assuming you went to System->Administration->Shared Folders and installed samba
open terminal and run $ ifconfig
remember your ip
Samba prompts for a password even if you haven't set a password up.   So set one in the terminal with
$ sudo smbpasswd -a ubuntu  
enter password

Next add your windows users
$ sudo gedit /etc/samba/smbusers
on the first line type
ubuntu="ubuntu"

Then in Shared folders add your share

On windows run \\your.ip.addr.ess
you should see your share

---

