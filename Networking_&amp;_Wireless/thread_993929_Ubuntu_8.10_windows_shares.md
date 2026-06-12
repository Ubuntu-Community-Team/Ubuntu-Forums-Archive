---
title: "Ubuntu 8.10 windows shares"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by windows_cleaner on 2008-11-26
I have a home network with 4 wired windows XP boxes plus wireless access. I have another box with Ubuntu 8.10 and samba. There is a folder on that with sharing enabled, allowing others to write and guest access. This allows the sharing of files to anybody on the network, including guests with a wireless connection.

I want to create another folder where only designated users can have access (I want to keep these files away from the kids and their friends).

I have so far had only limited success. I have created a Ubuntu user and a samba user with the same name as a windows user. A folder in that users home folder is then shared, allowing others to write but NOT guests.  This seems to work, when you are logged on to windows as that user you can read and write to that folder. When you are not logged on to windows as that user and try to access it windows shows the “Connect to Server” dialog box and no combination of users / passwords I have tried will give access.
Now the problem, I want to do the same for myself. I create a Ubuntu account in my windows user name without administrator privileges and repeat what I did before. When I try to access it from windows it requires a user name and password and none work!
What have I done wrong?

---

### Post by renzokuken on 2008-11-26
on the linux box are you creating normal users or samba users?

---

### Post by windows_cleaner on 2008-11-26
> **renzokuken said:**
> on the linux box are you creating normal users or samba users?
I am doing both, a normal user( no admin rights) and a Samba user (both have the same user name and password, the same as the windoes user name

---

### Post by windows_cleaner on 2008-11-27
I have managed to sort it out for myself. My mistake was in not seeing samba as completely separate from the operating system itself. My solution was to create a folder Ubuntu would share with anyone (Right click it and select Sharing options, Tick all 3 boxes, Share this folder, Allow other people to write, Guest access).
Then restrict access outside the Ubuntu box by editing the smb.conf file adding at the end

[<foldername>]
path = </home/myname/Desktop>
# restrict write access with  
write list <myname> <another <yetanother>
# restrict read / write access with  
valid users <myname> <another> <yetanother>
# After mapping the drive on the windows boxes hide from other users with
browseable = no

---

