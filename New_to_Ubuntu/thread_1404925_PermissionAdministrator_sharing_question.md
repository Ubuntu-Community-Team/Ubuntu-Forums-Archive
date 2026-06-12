---
title: "Permission/Administrator sharing question???"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by TheMustangZone on 2010-02-12
Hey all,
    I've been using Ubuntu exclusively now for over a year and I'm glad I ditched Windoze for good.  Anyway, I'm been working on trying to share files on my external hard drive, but I've hit a glitch.  I've gotten to the point where I can right click on the folder, go to the "share" tab, and click on "share this folder".  My problem is, I then get a message telling me to change the global folder in the "smb.conf" file to "usershare owner only = false".  The problem then becomes, I get a message telling me that only an "administrator" has access to change this folder.  How can I change my privileges to be an "administrator" without logging in as root?  Is that even possible?  Thanks in advance for any help.

Rob

---

### Post by semi_fiction on 2010-02-12
Open a terminal and type "gksu nautilus" (without the quotes) and navigate to the folder you want to change, you should be able to edit the folder then.

---

### Post by Shark_AtK12 on 2010-02-12
Sudo will granted you "root" privileges temporarily just by typing sudo <rest of command> and then the Password(which is your user's PW).
 
GKsudo(or gksu) opens a graphical program as the root. So the command the person above posted "gksu nautilus" opens the file manager as the root.

---

### Post by Cheezespread on 2010-02-12
> **semi_fiction said:**
> Open a terminal and type "gksu nautilus" (without the quotes) and navigate to the folder you want to change, you should be able to edit the folder then.

Pardon my ignorance . If we even create a file using the sudo in the command line , wouldn't it be against the root's name when we list its attributes ?

So wouldn't he  have to use " gksu nautilus" every other time if he needs to amend something ?

So , I was wondering if the ownership of the file is changed , wouldn't it make it easier for him for future. Sorry , I am just trying to see if that would be better off .May be I have gone completely crazy ! ( i do understand that config files are better left with root to amend them .still)

---

### Post by 3rdalbum on 2010-02-12
> **Cheezespread said:**
> Pardon my ignorance . If we even create a file using the sudo in the command line , wouldn't it be against the root's name when we list its attributes ?

So wouldn't he  have to use " gksu nautilus" every other time if he needs to amend something ?

So , I was wondering if the ownership of the file is changed , wouldn't it make it easier for him for future. Sorry , I am just trying to see if that would be better off .May be I have gone completely crazy ! ( i do understand that config files are better left with root to amend them .still)

1. Correct, it will be owned by root.

2. Correct, he will have to edit it as root.

3. smb.conf is root-owned for a reason. You can't let any old program running on your desktop have the ability to modify system files! Making smb.conf writable by ordinary users opens up a pretty large security hole, where if an attacker gains control over a regular user program such as Firefox or Acrobat Reader, they could modify smb.conf in such a way as to gain root permission, or to attack other users who are logging into the share.

Wherever possible, retain the default permissions for files that the system has created. Linux developers carefully craft their programs so that they have maximum security, and if you mess with this you're pretty much guaranteed to open up holes or cause parts of your system to stop working.

---

### Post by Cheezespread on 2010-02-12
Thanks a lot mate .

---

### Post by TheMustangZone on 2010-02-12
Thanks for all of the help, guys.  I will work on this some more when I get home.:D

---

