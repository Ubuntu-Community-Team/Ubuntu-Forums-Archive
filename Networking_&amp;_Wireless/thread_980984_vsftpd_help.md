---
title: "vsftpd help"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by mab1376 on 2008-11-13
is there a way to set a custom home directory for ftp logins rather than /home/username

for instance another harddrive 

/media/External/FTP

also for anonymous users can i set bandwidth restrictions and lock them in the home directory as listed above?

---

### Post by superprash2003 on 2008-11-13
use gproftpd instead.. it has a GUI and easy to configure [http://prash-babu.blogspot.com/2008/07/how-to-install-ftp-server-gproftpd-in.html](http://prash-babu.blogspot.com/2008/07/how-to-install-ftp-server-gproftpd-in.html)

---

### Post by jonobr on 2008-11-13
Not sure if its just me, but I found vsftpd to be quite limited, and didnt have the patience to play around with it a lot, 
I want to customise it as you said, however it didnt seem obvious.

One thing I would recommend you look at (if your feeling adventurous and have the time) is rsync, its secure and more reliable and only copies across differences on two systems.

I have a laptop (xp for home and work) and desktop (ubuntu) for work.
Anything I do and I want replicated I store in a certain directory in ubuntu.
On XP at the end of the day, i run a small batch file I created to sync the two,
You could automate this and the config file and options allow you to be more inventive about how it works.
Heres a couple of resources
( I think rsync is on your ubuntu by default - type  rsync enter, and it should get you the help)
on the terminal window type man rsync
on the web
[http://www.samba.org/rsync/](http://www.samba.org/rsync/)
On a windows platform you can have cwrsync 
[http://www.itefix.no/i2/node/10650](http://www.itefix.no/i2/node/10650)

And of course for the best support ever, you can always try [http://ubuntuforums.org](http://ubuntuforums.org)   :)

Hope this was useful

---

