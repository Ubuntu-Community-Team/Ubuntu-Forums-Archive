---
title: "how do i mail my self in a bash script?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-08
I have a script that at the end i want to email me that it has run because crontab dos not seem to like libnotify. I was given this command 

mail - "update done on ubuntu" [email]lancebermudez@gmail.com[/email]

I have no email program but thunderbird installed on my computer I have no idea what I'm doing please help me. below is the script

#!/bin/bash
sh /home/lance/bin/aptgetupdate; 
sh /home/lance/bin/aptgetdistupgrade; 
sh /home/lance/bin/updatavast; 
sh /home/lance/bin/setat2; 
notify-send -i /home/lance/bin/clock.png 'Lance update has gone off' -t 0;
mail - "update done on ubuntu" [email]lancebermudez@gmail.com[/email]

in the terminal i see

Exiting... (End of file)
warning: commands will be executed using /bin/sh
job 124 at Wed Jun  9 15:10:00 2010
warning: commands will be executed using /bin/sh
job 125 at Wed Jun  9 02:00:00 2010
/home/lance/bin/acerupdate: 7: mail: not found
lance@bermudezl:~/Videos$

---

### Post by doas777 on 2010-06-08
well, if you haven't configured a mail server (either to host yourself, or just config to connect to a server as a client), either in code, or as a system global setting of some kind (I don't know mailservers on linux yet), then you can't mail anyone. my guess is that whoever gave you the code, expected you to have sendmail installed and configured. as it is, there isn't a program on a default ubuntu desktop system called 'mail'.


Edit: this is prolly what you are looking for:
[http://www.debianadmin.com/how-to-sendemail-from-the-command-line-using-a-gmail-account-and-others.html](http://www.debianadmin.com/how-to-sendemail-from-the-command-line-using-a-gmail-account-and-others.html)
[http://ubuntuforums.org/showthread.php?t=1472520](http://ubuntuforums.org/showthread.php?t=1472520)

---

