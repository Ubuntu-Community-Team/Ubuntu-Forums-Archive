---
title: "Samba Nobody (File ownership) problems returns"
date: 2017-01-07
forum: Networking &amp; Wireless
---

### Post by stephen67 on 2017-01-07
Scenario

Samba is installed and used on server running Ubuntu 16.10. In addition to server software, normal desktop programs are installed. Certain folders are shared. Guests may access and create files. Windows computers copy files to the shared folders. These files have ownership of nobody:nobody I have two Windows 10 computers. The problem happens with both,

Desired behaviour

These files are given ownership of the owner of the directory.

Method

The samba.conf file has an entry for each shared folder, like this:

[public]
       comment = Stephen Public
       path = /home/stephen/Public
       writeable = yes
;      browseable = yes
       guest ok = yes
       force user = stephen
       force group = stephen

Situation

This has been working as desired since I did a new install of 16.10. Today I noticed the nobody ownership problem. I had it after the install of 16.10 because I forgot to update samba.conf. Hence the return of the problem.

It has been a week since I did a file copy that worked as desired. I copy files infrequently.

It is worse. A sudo chown to change permissions to stephen:stephen executed without error. But within nautilus the context menu on the files had the commands to rename and delete greyed out. Even though the permissions section of the properties did say the ownership was changed.

I have not made any configuration changes. I have performed one, maybe two, system updates. There has also been a Windows 10 update.


Any and all help appreciated.

---

