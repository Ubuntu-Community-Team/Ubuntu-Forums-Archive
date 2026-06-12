---
title: "permissions not working"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by kapi on 2010-04-08
OK I've set the files and folders to read and write in order to install opencart software. However when starting the installation i'm informed that the files are unwritable. 

/var/www/store/download/  	Unwritable

but they are writable.

Any ideas

---

### Post by Steven_S on 2010-04-08
I'm sure they are writeable... but by who?

Have you tried to use the command "ls -l" (that is a small letter l) on the folder to check the permissions?

In Nautilus, you can check the same thing by right-clicking the folder, then *Properties*, then *Permissions*.

---

### Post by kapi on 2010-04-08
Have set the permissions via right click on folder and open as administrator then made changes for folder and contents to read and write but opencart seems to think otherwise.


**Directories	Status**
/var/www/store/system/cache/	Unwritable
/var/www/store/system/logs/	Unwritable
/var/www/store/image/	Unwritable
/var/www/store/image/cache/	Unwritable
/var/www/store/image/data/	Unwritable
/var/www/store/download/	Unwritable

---

### Post by Steven_S on 2010-04-08
The OpenCart.com documentation says: 

"
**Installation**

       **Linux Install**

       
[LIST=1]
[*]           Upload all the files and folders to your server from the "Upload" folder.
            This can be to anywhere of your choice.
            e.g. /public_html/store or /public_html
[*]           For Linux/Unix make sure the following folders and files are writable.
            
            chmod 0755 or 0777 image/
            chmod 0755 or 0777 image/cache/
            chmod 0755 or 0777 cache/
            chmod 0755 or 0777 download/
            chmod 0755 or 0777 config.php
            chmod 0755 or 0777 admin/config.php
            
            If 0755 does not work try 0777.
[*]           Make sure you have installed a MySQL Database which has a user assigned to it
            **DO NOT USE YOUR ROOT USERNAME AND ROOT PASSWORD**
[*]           Visit the store homepage
            e.g. [http://www.example.com](http://www.example.com) or [http://www.example.com/store/](http://www.example.com/store/)
[*]           Follow the onscreen instructions.
[*]           Delete the install directory."
[/LIST]
Does that help?

---

### Post by kapi on 2010-04-08
Yeah thanks thats the instructions I followed to initially set up the program. The index page loads ok but the following page that specified the permissions gives me the faults or apparent faults because the folders do possess the correct permissions.

Cheers though, it's appreciated

---

### Post by Steven_S on 2010-04-08
I have noticed that the software has its own forum (for example: [http://forum.opencart.com/viewtopic.php?f=19&t=10085&p=49424&hilit=Unwritable#p49424](http://forum.opencart.com/viewtopic.php?f=19&t=10085&p=49424&hilit=Unwritable#p49424)). Maybe you will have better luck gathering experiences there. 

Wishing you good luck! ;-)

Edit: I also read that some hosts have support for OpenCart. Perhaps yours does and there is a one-click install via your host?

---

### Post by kapi on 2010-04-08
It's ok I guess I'll have to get better at CLI and using the terminal and less lazy. It inspired me to do some revision on command line inputs and now they seem to have a better effect than via the GUI.

Thanks to all of you for the input

Kapi

---

