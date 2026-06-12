---
title: "help with following a tutorial?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2008-08-10
Hello. I found a tutorial on these forums as this address
[http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+samba+windows+networkhttp://ubuntuforums.org/archive/index.php/t-6421.html](http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+samba+windows+networkhttp://ubuntuforums.org/archive/index.php/t-6421.html).
I followed the tutorial up to the point where is says "To create the folder type (inside a new terminal) ...". (use Ctrl + f in firefox to find the place please.)

I want to modify this to create a folder in another location. How can i modify this line of code to create a folder at the address "/home/mahela007/Public"? That is I want to create a folder inside the folder called public.

---

### Post by chili555 on 2008-08-10
Open a terminal and do:```
mkdir /home/mahela007/Public/nameofdirectory
```You can actually shorten this up a bit with ~ which is roughly shorthand for 'in the current user's home directory.' So the shortened version is:```
mkdir ~/Public/nameofdirectory
```Of course, you could also open Places -> Home Folder and double click Public to open it and the go to File -> Create Folder. A folder will be created called 'untitled folder' which is greyed out, welcoming you to type in the name you really want.

Of course the latter, GUI method looks easier but takes more steps than the terminal method. Sometimes you can do things easier in a terminal than with a GUI.

---

