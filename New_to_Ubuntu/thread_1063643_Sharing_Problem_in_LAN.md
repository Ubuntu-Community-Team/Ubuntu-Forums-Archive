---
title: "Sharing Problem in LAN"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by bipinbaglung on 2009-02-08
I have installed samba  in my ubuntu 8.10 desktop edition
I tried to share folders from this location /media/BACKUP/Tools
"I click on sharing options after Right click. Check on the "Share this Folder" Checkbox. Then click on "Create Share"."
As I click it eports as this : 'net usershare' returned error 255: net usershare add: cannot share path /media/BACKUP/Tools as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.
Now how can i add the mentioned line. Or how can I share folder from drives.

---

### Post by jimv on 2009-02-08
If you edit /etc/samba/smb.conf
you can add that line anywhere under the heading [global]

---

### Post by Kellemora on 2009-02-08
Hi BPL

You MAY NOT want to do it that way, because it gives ANYONE access!

I would think your best bet would be to change the permission on the folder to the group you want to allow access to it.

For example, I have a folder named File-Server on sdb that I only want myself and members of the group to have access to.
So I changed the ownership of that folder.
```
sudo chown -R user:group /media/sdb/File-Server/
```
```
sudo chmod -R 755 /media/sdb/File-Server/
```

Also you have to put the users names in the smbusers folder and assign them a group in System/Admin/users and groups.

Now, everyone listed in smbusers has access to the File-Server folder, which is where virtually EVERYTHING in the way of data is stored.

TTUL
Gary

---

