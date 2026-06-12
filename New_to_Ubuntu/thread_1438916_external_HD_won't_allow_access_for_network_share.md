---
title: "external HD won't allow access for network share"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by nipsy on 2010-03-25
Well I'm back again for more insight from you wonderful helping hands.

I am setting up a desktop version of Ubuntu 9.10 as a server (no, we don't want the server edition). 

I have set up file share between the desktop,(ubuntu 9.10), and two laptops(one runs Windows Vista premium, the other runs a dual boot of Ubuntu and Vista). We have no problem going back and forth sharing files in these three computers.

Now we want to add the external. I have followed all and any advice from over 20 different tutorials and nothing is making sense or working.

The external hard drive is a USB and written in FAT format.

It will show on the 3 computers, but when we try and access, it says we don't have permissions. When we try and right click, the message in our "permissions" tab says 

[B]permission unavailable 1A01-2240 denied

[/B]All we want to do is add the external just like we did the computers. After trying many different options, the only thing I can think of next is to move all folders from there to the desktop, re-format the external, and move the folders back. This process will take over 6 hours alone. Did I happen to mention we were up until 5 am this morning trying to get in the external to share??  

Oh yes, the external is currently formatted for Millenium, not sure if that makes a difference..

Once again, I thank you all for your help and even with all these late night work sessions I'm still enjoying and learning so much more about computers and programming then I ever did and would in Windows..

---

### Post by gordintoronto on 2010-03-25
Is the external drive attached to the "server"? If it's FAT format, it must be small. How big is it? Is the data in a folder, and did you share the folder?

---

### Post by nipsy on 2010-03-26
sorry took me so long..

Yes, its in FAT, and its attatched to the "server" and we tried to share the folder but we don't have that option on the external. When I right click on the external, and go to properties >permissions, there is nothing there but previous stated information. There is no option to click and share or change permissions.

---

### Post by terdon on 2010-03-26
Have a look at: [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Samba_File_Sharing]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Samba_File_Sharing")

---

### Post by Morbius1 on 2010-03-26
An external usb drive formatted in FAT32 or NTFS will mount with owner = you and permissions to read and write only to you. Samba will allow you to share it but linux file permissions will not. There's an easy fix depending on how you set up your shares and what method of sharing you used ( there are two methods ). 

Please post the output of the following commands and we can tell you how to fix this:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by Morbius1 on 2010-03-26
I need to pack it in for the day so I'll cut to the chase and offer you this suggestion:

[] If you used Nautilus-share ( Nautilus > Right Click > "Sharing Options" ) then add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:

```
force user = morbius
```[COLOR=Blue]*Change morbius to your local server login user name*[/COLOR]

This will force all remote users to appear to linux to be you and right now you're the only one that can access the drive. This applies to shared folders only of course not your whole system.

[] If you used Classic-shares and your share definition is in smb.conf then add the line to the share definition itself - not the global section. For example:

[external]
path = /media/Seagate
guest ok = yes
writeable = yes
[COLOR=Blue]force user = morbius[/COLOR]

When you're done adding the line, save smb.conf and in a Terminal type: **sudo service samba restart**

---

