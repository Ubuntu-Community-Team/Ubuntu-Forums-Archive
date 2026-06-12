---
title: "File permissions - NFS"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by thgthg on 2011-02-02
Hello,

I have recently installed a Readynas Duo NAS that should be available for all users in the network. Everything works just fine except for the trouble I have with file permissions. I can change permissions on all existimg files with chmod command, but as soon as I create a new file other users have no access to that file. Is there a way to give corect file permissins to all files, existing and new files in a certain folder?

Thank you for your advice !

---

### Post by Morbius1 on 2011-02-02
Not exactly sure why you are posting this question in the Ubuntu forum unless I don't understand the question. This is a ReadyNAS question. I looked at the User's manual out of curiosity and it appears they use Samba with their own front end:
> ***Advanced CIFS Permission***. The Advanced CIFS Permission section offers options for setting the default permission of new files and folders created through CIFS. The default permission of newly created files is read/write for the owner and owner’s group and read-only for others (that is, everyone). Permission for newly created folders is read/write for everyone. If the default does not satisfy your security requirement, you can change it here.I would check out the "Advanced CIFS Permissions" section and modify the permissions on newly created files.

---

### Post by thgthg on 2011-02-02
I am using NFS protocol and have the NAS mounted to a local folder /MAS where I can set file permissions. CHMOD -R 777 gives full control for all users on existing files in the folder

---

### Post by Morbius1 on 2011-02-02
Ah, wasn't able to discern that from your original post. Sorry, I have no knowledge of NFS.

In consolation I would like to offer a suggestion: Change the title of your original post to something like: "File permissions - NFS". You're likely to get the NFS'ers to respond.

---

### Post by thgthg on 2011-02-02
OK,  thanks for your help

---

