---
title: "folder on network mounted but unable to access"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by shelper on 2008-08-12
i met a strange problem when mounting a windows folder over network.
here is the command:
sudo mount -t cifs -o username=username //IP/folder/ /mnt/myfolder/
it worked and the system shows it is mounted
but can not access myfolder and the error comes out:
bash: cd: myfolder/: Not a directory

nautilus also says: the contents can not be displayed.

well, after i umount the folder, 'cd myfolder' works again though it is empty

also tried:mount -t smbfs -o username=username //IP/folder/ /mnt/myfolder/
the error becomes:
mount error 13 = Permission denied
:confused:
Refer to the mount.cifs ( 8) manual page (e.g.man mount.cifs)
any idea on this?
thank you!

---

### Post by ilrudie on 2008-08-12
First of all mounting to /mnt/<anything> is probably not the best idea.  You should probably mount it to /media/myfolder.  Second I can't tell if you simply cleaned up the command and removed your username from it but you should put your username in there (e.g. username=<myusername>).

Also you will probably need to use sudo which my be what caused your permissions denied message when using the smbfs type.

Also the easiest way to do this will be from the Places>Connect to Server... menu item.  Just select type "Windows Share" and enter all the credentials and you should be good to go.  No need to do any CLI work.

---

### Post by shelper on 2008-08-12
thank you for answering
that still does not work
actually that works for sharing an folder on windows XP
but what i wanna access is a shared folder by windows server
and i can easily access it by windows XP
now switch to ubuntu, seems just keep asking my password
it is behind a domain but i inputted that domain in the dialog, does not work

i also tried sudo

---

### Post by shelper on 2008-08-12
> **ilrudie said:**
> First of all mounting to /mnt/<anything> is probably not the best idea.  You should probably mount it to /media/myfolder.  Second I can't tell if you simply cleaned up the command and removed your username from it but you should put your username in there (e.g. username=<myusername>).

Also you will probably need to use sudo which my be what caused your permissions denied message when using the smbfs type.

Also the easiest way to do this will be from the Places>Connect to Server... menu item.  Just select type "Windows Share" and enter all the credentials and you should be good to go.  No need to do any CLI work.
i think the major issue is:
cifs works and smbfs does not work ( i use sudo for both )
but the folder mounted by cifs can not be recognized as a folder
so,
wonder there are sth wrong with it, anyway.

---

### Post by ilrudie on 2008-08-12
> **shelper said:**
> thank you for answering
that still does not work
actually that works for sharing an folder on windows XP
but what i wanna access is a shared folder by windows server
and i can easily access it by windows XP
now switch to ubuntu, seems just keep asking my password
it is behind a domain but i inputted that domain in the dialog, does not work

i also tried sudo

Did you enter your user name as <domain_name>\<user_name> ?

---

### Post by shelper on 2008-08-12
yes
and, i also tried your method using places-> connect to server-> windows fold, 
it just keeps asking password and username and domain name...

---

### Post by shelper on 2008-08-13
i think i found the problem
it has been reported that 
there is a bug for mount.cifs to mount the folder with dollar signs,
and seems has not been resolved:(

---

