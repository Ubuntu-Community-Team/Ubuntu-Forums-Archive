---
title: "how to use software installed in another user"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by the_robust on 2011-07-17
Hello All,

I am new to ubuntu and yestarday i created two three users on my newly installed ubuntu OS.
i get logged in into first user and have installed couple of photo-editing softwares on the user and when i log into other two users, i cannot see those s/w installed.
could anybody help me wid how could i use those softwares in other two users also?

Regards

---

### Post by dasan on 2011-07-17
while installing the software for multiple user install it as root..
from your explanation what i understood is like the installation went to one users home folder.
as root user you can access the folder and run it or give permission for this user to run it.
please give some more details like path of installation

---

### Post by raja.genupula on 2011-07-17
> **dasan said:**
> while installing the software for multiple user install it as root..
from your explanation what i understood is like the installation went to one users home folder.
as root user you can access the folder and run it or give permission for this user to run it.
please give some more details like path of installation



hey 
i think to install any application in ubuntu we should have  to be as root . so if he installed means he did it as root . either terminal or software center both needs root password to install applications .

---

### Post by azertyh on 2011-07-17
hello,
in the others users, doesn't the program run even if you launch it in a terminal?

---

### Post by CatKiller on 2011-07-17
Anything that you install through Synaptic or the Software Centre (or apt-get from the command line) is installed for all users. That's why you need to do so as root.

How did you install the software you installed?

---

### Post by nkdnkd on 2011-07-17
hi,
I think you should login to any of the other user account and do the followings :-
sudo updatedb
after the command finishes execution 
sudo locate <name of your installed software>
This should show you the location where the program has been installed. Invariably it will be the home folder of the user account which you used during installing the software, so you browse to the folder 
sudo cd <full path>
Now execute the software !
Hope that helps
thanks 
nishith

---

### Post by The Cog on 2011-07-17
If installing software for use by multiple users, it is normal to install it in a shared area. /usr/bin, /usr/lib and /usr/share are common places for this. Only root is allowed to write to these areas. All software from the Ubuntu repositories is installed this way.

If a user installs their own software, they would normally install in their home directory. If other users want to use such software, then they have to have read and execute access to the place where the owner installed it. This is not the normal thing to do, and it implies a great deal of trust in the owner of the installed software - they could replace it with malware any time they choose.

---

### Post by dasan on 2011-07-20
> **raja.genupula said:**
> hey 
i think to install any application in ubuntu we should have  to be as root . so if he installed means he did it as root . either terminal or software center both needs root password to install applications .

It is true for all synaptic controlled and .deb files but there are other third party application like eagle(i hope) provides an installation package which will simply extract and put files to some part of home directory and put a link in menu.

---

