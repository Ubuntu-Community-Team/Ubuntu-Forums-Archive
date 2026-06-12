---
title: "[SOLVED] Sharinf From Ubuntu To Ubuntu Works Fine But Not To Windows (Printer Works F"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by DasCrushinator on 2008-02-26
I have read several thread over the past year trying to solve this problem, but they all seem to be for Ubuntu not seeing Windows shares, and not the other way around.

Ok, I have a network with three Ubuntu boxes and one Windows box.

One is purely a print server and the all four boxes can print from it.

One is a guest computer that will also be used to share files from.

One is my dad's Windows laptop.

And finally is my Ubuntu laptop.

The Guest computer and my laptop (both running Ubuntu) can see shares fine between each other, but the Windows computer can not connect to the Ubuntu shares.

My process for sharing folders is 'System'->'Administration'->'Shared Folders'-><PASSWORD>->'Add'->'Windows Network (SMB)'

I can't for the life of me figure out why the Windows machine can't connect to the Guest computer.

Also, is it possible to share an external USB drive?  I tried right clicking on it, and it didn't have the option to, but I figured I would ask.

Thanks in advance!!!

---

### Post by Technophobia on 2008-02-26
You have a few options for better samba control that I know of.

1) [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_public_folders_with_read_only_or_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_public_folders_with_read_only_or_read.2Fwrite_permissions_.28Authentication.3DNo.29)

 If you just want access to file sharing with no restrictions.

and

2) Webmin 
[http://www.webmin.com/](http://www.webmin.com/)
[http://prdownloads.sourceforge.net/webadmin/webmin_1.400_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.400_all.deb)

If you would like a clean interface (in my mind) to Samba file sharing. Webmin lets you do remote administration of a computer from your web browser.



This video may be helpful as well. [http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)


As for the external drive, it gets mounted to the /media folder. From the media folder select the folder that is the name of your drive and share it from there.

---

### Post by DasCrushinator on 2008-02-26
> **Technophobia said:**
> You have a few options for better samba control that I know of.

1) [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_public_folders_with_read_only_or_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_public_folders_with_read_only_or_read.2Fwrite_permissions_.28Authentication.3DNo.29)

 If you just want access to file sharing with no restrictions.

and

2) Webmin 
[http://www.webmin.com/](http://www.webmin.com/)
[http://prdownloads.sourceforge.net/webadmin/webmin_1.400_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.400_all.deb)

If you would like a clean interface (in my mind) to Samba file sharing. Webmin lets you do remote administration of a computer from your web browser.



This video may be helpful as well. [http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)


As for the external drive, it gets mounted to the /media folder. From the media folder select the folder that is the name of your drive and share it from there.

Looking into all of this, thanks!

---

### Post by DasCrushinator on 2008-02-26
Worked perfectly!!

Thank you so much!

---

### Post by Technophobia on 2008-02-27
no problem and Good to hear.

---

