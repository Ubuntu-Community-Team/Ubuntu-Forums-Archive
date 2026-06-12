---
title: "Can see shared folder but can't access contents"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by brawd on 2009-06-30
Hi All,

My wife and I use the same computer, each of us with our own account. So I set up my clipart folder in my home directory for sharing. I think.

When she wants some of my clipart she can see the folder via places/computer and places/network. But when my dear wife (who is sat by my side) opens my clipart folder all she sees is an icon representing a bit of clipart. The folder has as many icons are there are samples of clipart.

When she tries to use my clipart she gets the message:

Could not load image
Access denied.

When I set up the share I ticked everything including guests.

Should it work like that or should I set up something in the 'Public' folder instead?

regards,

brawd.

---

### Post by Miljet on 2009-06-30
How did you set up sharing for the folder?

I think that your problem is a matter of permissions. If you are using nautilus (file browser), right click on any file in the folder, click on properties, and finally the permissions tab. You will probably find that the file (and all the others in the directory) belong to you and to the group that has your name. 

If you and your wife are the only ones who use this computer, you should be able to change the permissions for "others", (any user) to read and write. You will have to do that for each file in that directory.

Another option. if you only want you and your wife to have access, is to create a new group, with a unique name, and make sure that both you and your wife belong to that group. Then change the group ownership of all the files to the new group.

---

### Post by superprash2003 on 2009-07-01
post content of the /etc/samba/smb.conf file

---

