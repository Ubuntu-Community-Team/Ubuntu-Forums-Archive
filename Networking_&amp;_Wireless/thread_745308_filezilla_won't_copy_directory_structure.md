---
title: "filezilla won't copy directory structure"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by asteinmetz on 2008-04-04
I am trying to use filezilla to copy files from a windows machine to a feisty machine.  I have installed ssh on the feisty machine, connected with sftp  using a username/password from filezilla on the windows machine and done  single file copies with now trouble. Anything requiring creating a directory fails with filezilla indicating I don't have sufficient permission.  

Using Putty I can use "sudo mkdir" from the same user on the windows machine so I guess I need to mimic the sudo functionality with filezilla.  How do I do that?  Thanks.

---

### Post by Oldsoldier2003 on 2008-04-05
> **asteinmetz said:**
> I am trying to use filezilla to copy files from a windows machine to a feisty machine.  I have installed ssh on the feisty machine, connected with sftp  using a username/password from filezilla on the windows machine and done  single file copies with now trouble. Anything requiring creating a directory fails with filezilla indicating I don't have sufficient permission.  

Using Putty I can use "sudo mkdir" from the same user on the windows machine so I guess I need to mimic the sudo functionality with filezilla.  How do I do that?  Thanks.

Filezilla uses ftp raw commands so that will not be a supported command. The solution for this would to be either create the proper directory structure for the user, or give the user the proper permissions.

---

### Post by conryf on 2008-04-21
he's right, just use, from the commandline... 

<code>sudo filezilla</code>

---

