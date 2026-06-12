---
title: "file permissions in folder"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by anatak on 2009-08-21
Is it possible to setup the permissions so that files created in a directory are created with the same permissions as the directory ?

the directory has 755 permissions (read and execute for group and all) but when I create a file it is created with 744 permissions (only read for group and all)

How can I change this ?

---

### Post by mthalis on 2009-08-21
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by anatak on 2009-08-23
I read the document.
I understand that if you use the -R option you give the permissions to all the files in a folder and I did that.
BUT when I create a new file in that folder it does not have the permissions of the folder. 

How can I setup the folder so that every file created in the folder will have the same permissions as the folder ?

---

### Post by scorp123 on 2009-08-23
> **anatak said:**
>  the directory has 755 permissions (read and execute for group and all) That's necessary for a directory, yes. "Executing" a directory means "being able to go into it". If you take away the execute bits on a directory then you will not be able to access it any longer.

> **anatak said:**
>  but when I create a file it is created with 744 permissions  You probably mean "644"? That would be _normal_ for a file. Why should an ordinary file have execute permissions for everyone (e.g. 755)??? [COLOR="Red"]**That's dangerous.**[/COLOR] 

If the files we're talking about are programs or shell scripts that belong to you then they should be set to 750 ... but 755 means really everybody can execute them.

Normal document files (texts, music, pictures, and what not) have no business having their permissions set to 755.

Can you give more details? Why do you want to set file permissions to 755?

---

### Post by anatak on 2009-08-23
the files are in a www directory of apache.
The folders need the executable to be able to browse in the folders with a webbrowser 
The files need also executable I think.

---

### Post by scorp123 on 2009-08-24
> **anatak said:**
> The files need also executable I think. Normal HTML files don't need to be executable, a 644 should be sufficient. It's far more important who the owner of those files is, e.g. those files should belong to Apache's system account. What is it called ... "www" or "www-data" or something?

---

### Post by anatak on 2009-08-24
but if the files are owned by the apache system account can I still edit them ?

---

### Post by scorp123 on 2009-08-24
> **anatak said:**
> but if the files are owned by the apache system account can I still edit them ? Of course not. You're not supposed to edit them like this anyway, that's way too unsafe.

Read here:
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)

The guide was originally written with Ubuntu 6.10 in mind but it's still valid. 

And this one contains a section about how you're supposed to _SAFELY_ edit files so that it all works as it should in the end:

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

Relaxing permissions way too much on your web pages that are then served out by Apache to the rest of the world is a great way of getting hacked BTW, so unless you don't mind getting hacked and people doing illegal things with _YOUR_ setup for which _YOU_ will be made responsible ("But I got hacked! Really! ..." won't count in court unless you're able to provide hard proof ...) I suggest you take security and file permissions more serious.


EDIT: forgot to add the second link.
.
.
.
.

---

### Post by anatak on 2009-08-24
ah sorry I forgot to tell you.
this is on a dev system. not on a live system.
I know that relaxing file system permissions is a way to lower the security of your pc.

thanks for the guide I ll read it and try to implement it but my original question still stands.

How do you edit a folder to make sure that files in the folder have the same permissions as the folder ?

---

### Post by The Cog on 2009-08-24
> **anatak said:**
> How do you edit a folder to make sure that files in the folder have the same permissions as the folder ?
I don't think you can (unless using ACLs can do it). And if you could, it would be a really dumb thing to do, as has already been pointed out. Even on a dev system, it's not a good idea to start making all your data files executable or to get into the habit of circumventing security measures. It would be too tempting to transfer those habits (executable files?) to the production system.

---

### Post by decoherence on 2009-08-24
> **anatak said:**
> How do you edit a folder to make sure that files in the folder have the same permissions as the folder ?

To my knowledge, POSIX permissions do not do this. You'd need to use ACLs. The link mthalis provided has information on how to set this up, [here]("https://help.ubuntu.com/community/FilePermissions#ACLs").

Often the same functionality can be accomplished by setting up task-specific groups and giving them appropriate access to your files. Since POSIX permissions are hugely more simple than ACLs, this is generally the preferred way, when possible.

Another tempting option is to play with the umask, but I'd strongly recommend against that as it will change the system in ways that aren't relevant to your issue.

If none of the answers really solve your issue, perhaps you could elaborate on what it is you want to do? It could be there is a whole other solution that doesn't involve custom permissions.

---

### Post by anatak on 2009-08-26
Thank you for the answer.

So it is not really doable. Probably with good reasons as pointed out.
now I still need to get the file permissions sorted out for the webdev thing.

I will probably (surely) be back in a while after I played around with some stuff.

Are php files considered CGI files ?

---

### Post by anatak on 2009-08-26
Thank you all.
I read the guide how to setup the file structure for an apache site and now everything works as it should without having to change file permissions.

thank you all and especially scorp123

as you know I am new to Ubuntu and this forum. Is there a way to close a topic or somehow mark it as solved ?

EDIT I ran into my next problem. Now I can't access mysqlphpadmin anymore.
I guess I have to enable the phpmyadmin site too. 
does anybody know wich of the phpmyadmin folders need to be enabled ?
I searched on my system and I have
/etc/phpmyadmin
/usr/share/phpmadmin
/usr/share/dbconfig-common/data/phpmyadmin
/usr/share/doc/phpmyadmin
/var/lib/phpmydmin
/var/lib/mysql/phpmyadmin

and a host of filenames with phpmyadmin

---

