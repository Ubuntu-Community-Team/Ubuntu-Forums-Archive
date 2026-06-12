---
title: "wish to access my ubuntu box without typing in ip address"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by linducky on 2008-07-29
Good day to you all.

I have my machines networked via a wireless router and i have a very simple samba configuration where i can allow my windows box to access the contents of my linux box.

the shared folder on my computer is an external hard drive and i would like for my mother and sister to access the files off of this drive. However due to the fact that i dual boot so when my friends come over we can play FIFA i don't always get the same ip address on my linux box everytime the machine restarts.

my sister and mother are also not extremely technologically savvy so i cannot expect them to enter in "\\192.168.1.xxx" whenever they wish to access the drive.

is there some way i could simply allow them to type in the name of my computer e.g. "\\oyoh-desktop" or have me set it up as a network drive on their machine without having to specify the ever changing IP address so that every time i restart it works well...

i have included a copu of my smb.conf file in case it is of any help.

  > GNU nano 2.0.7              File: smb.conf                                    

[global]
   workgroup = WORKGROUPNAME
   server string = COMPUTERDESCRIPTION
   security = share
[Shared]
path = /media/disk
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes

---

### Post by Endwin on 2008-07-29
I would either edit their hosts file and add in the name you want to use pointing to the IP of your machine, or just map a network drive for your machine. You can do both in windows. The hosts file in windows is under: **c:\windows\system32\drivers\etc\hosts** You may need to change Windows for winnt depending on your install. 

As for mapping a network drive in Windows, just right click on My Computer and go to map network drive. Just fill out the information for the share keeping a double \ before the IP like this \\192.168.1.77\pub

---

### Post by linducky on 2008-07-29
no, i dont think you understand, every time i restart my linux box my i.p address of the box could change, so where it could be 192.168.1.3 now when i restart it could be 192.168.1.5 later, if i edit that in the win machine wouldn't it still only point to one address...

i want to find out how to give my ubuntu box an alias name so that i could tell my windows machine to just connect to *oyoh-desktop* and map to that **name** instead of having to search for my ip addy and then connecting to it from windows.

---

### Post by Iowan on 2008-07-30
Check [Post#4]("http://ubuntuforums.org/showthread.php?t=852029").

---

### Post by chili555 on 2008-07-30
Why not use a static IP on your machine?

---

### Post by linducky on 2008-07-31
i was considering that. but i dont quite know how to get it done :s

will look up on it though

---

### Post by linducky on 2008-07-31
> **Iowan said:**
> Check [Post#4]("http://ubuntuforums.org/showthread.php?t=852029").

i dont think this is quite what i need.
from my understanding the problem its the other way around

---

