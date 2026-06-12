---
title: "Weird Filesharing Problem"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by bdoe on 2008-04-28
I'm having a really strange problem with my Samba shares on my network.  I have a file server running Ubuntu Feisty, and have protected shares set up on it.  My Windows computers can access the shares just fine when the volumes are mounted with the proper credentials. 

I recently installed Ubuntu Hardy on my laptop, edit fstab just like I had with previous Ubuntu versions, and the shares mount on my laptop just fine.  I can access my files, read them, create new files, rename, delete, the whole nine yards. BUT - if I open a file, edit it, and save the change, the file's group changes from "users" to "lpadmin", and the file is no longer accessible from any other computer other than this one. This is especially annoying when trying to save edits on OpenOffice documents because OpenOffice complains about not being able to create a backup (so I save the file locally, copy it to the shared directory, delete the original, and rename it). I've also noticed that files I copy or create on the shared directory inherit this "lpadmin" group. Further, if I inspect another file's permissions, I notice that it's set for rwx for owner and group ("users"), but when I check it again, it's rwx for owner only, group is changed to "lpadmin", and nobody else has access.

Anyone have any idea what's causing this weirdness?

---

### Post by jetsam on 2008-04-28
Odd, and I'm not really sure, but...  

If you're mounting with cifs, there's a nosetuids option that seems promising for a fix.  Here's the man mount.cifs entry:
>  nosetuids
          The  client will not attempt to set the uid and gid on on newly created files, directories, and devices (create,  mkdir,  mknod)  which will  result  in  the  server setting the uid and gid to the default (usually the server uid of the user who mounted the share).

If you're mounting with smbfs, perhaps it's contributing.  Smbfs has been deprecated for a while, and it may not have received a lot of testing under Hardy.    

Posting the mount details you're using in your fstab may help me or another forum-ite understand the problem better.

---

### Post by bdoe on 2008-04-28
Sure. Here's the pertinent fstab entry:
```
//192.168.1.100/DOENET\040Shares    /media/DOENET\040Shares    cifs    credentials=/etc/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777    0    0
```Now, out of curiosity (I've been trying to figure out the difference between CIFS and smbfs), but - since my server is running Feisty, it's configured with samba and is likely using smbfs - or does this make any difference?

I'll try that nosetuid option, and see if that makes any difference.

Edit: nosetuid made no difference whatsoever.

---

### Post by jetsam on 2008-04-28
In this context, smbfs vs. cifs is a decision you make about client access.  Cifs is newer and better, so you're better off with it.  Your Feisty server should support either kind of client access.  

I think there's two things going on here:
**The weirdness**: 
Unless you specify a uid and a gid for your cifs mount, you'll get seemingly random reporting of apparent groups from the server.  This happens because the underlying group id numbers and user id numbers are not consistent from one computer to another.  This is normal if you haven't set up a system to unify ids across the network like NIS or LDAP.  The normal, easy way to cover up this problem is to tell cifs to lie to you.  You can do this by changing your mount command to:
```
//192.168.1.100/DOENET\040Shares    /media/DOENET\040Shares    cifs    credentials=/etc/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777, **uid=<your_username>,gid=users**    0    0
```  
Note the changes in bold to the mount command.  Change <your_username> to your actual username.  If you make these changes, your cifs mount will report everything as belonging to your user and to the group 'users'. 

If you want to see the actual owner and group on the server, you'll have to log onto the server to do so.  Awkward, but better than the system telling you utterly confusing things like the new group is "lpadmin", and much easier than setting up directory services.

**The access problem:** 
You want everything you create  and modify on the share to belong to the users group.  You can set this in your smb.conf on the server by adding:
```
force group = users
```
to your share definitions and then restarting Samba.  Hopefully that will fix the access problem.

Hope that helps.

---

### Post by bdoe on 2008-04-28
Okay, almost there! The change to my fstab fixed the weirdness. The user group is now being retained, and that "lpadmin" problem is no more.

However, even after adding force group = users to my server's smb.conf file, the access problem remains.

For example: When I view the output of ls -l on one of my shared directories, I see that a file has the permissions -rwxrwxr-- 1 bdoe users. When I edit the file and save it, the permissions change to -rwx------ 1 bdoe users.

Any ideas?

---

### Post by jetsam on 2008-04-28
Try adding:
```
create mask = 0775
directory mask = 0775
```
To the share definition.  This should be sufficient.  Sometimes it takes a few iterations to figure out the best masks and modes, so report back the results.

---

### Post by bdoe on 2008-04-28
I was one step ahead of you there. After my last post, I decided to log into my server's SWAT and see if I could find the problem there and, sure enough, I had my share's create and security masks set too restrictively (create mask was set to 0700).  So I reset those to 0774, and all is well again, sort of.  OpenOffice still complains about not being able to create a backup when I save edits to an OO document, but I can select "Save As" and overwrite the file, and all is well.  I'll have to poke around OO a bit to see what the problem is, but at least my network shares are working properly again.

Thank you so much for your help! :)

---

### Post by jetsam on 2008-04-28
You're welcome, and I'm glad it worked.  :)

Swat's great for checking the details of the smb.conf because all the documentation is right there.  

I think I read somewhere about OO doing something strange with network shares, but I can't remember the details.  Good luck on the search.

---

