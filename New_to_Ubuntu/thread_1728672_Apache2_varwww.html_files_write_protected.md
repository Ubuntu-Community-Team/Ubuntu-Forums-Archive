---
title: "Apache2: /var/www/*.html files write protected?"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Vintermark on 2011-04-14
Ok, got a 32bit ubuntu server set up. Got Apache working, can see webpages from my Windohs computer using the the 192.168.0.xxx and with my ISP assigned IP. ALL GOOD. 

The login/user is use is the one I created while installing the server.

So now I want to make a web site, wich I decided it would be easiest to do on my windows computer.

Problem: get my index.html from Win to my server at /var/www/

Solution 1: I set up vsftpd, got it working. used Win with command prompt to pull the index.html from my servers /var/www/. Edited the index.html and tried to send it back, first trying to overwrite it, but acces denied. And also uploading a second file called webpage.html, also acces denied. Got the /var/www/ folder and index.html set to chmod drwxrwxrwx and -rwxrwxrwx (execute might be exxsecive but i wanted it to be failsafe.)
Well it failed obviously!

Solution 2: SSH and Windows PuTTY SHCP command line thingy,  same story as FTP.

While writing I  came to think of apache, do I have to slap him unconsious before I kidnap its children and DNA modify them and put them back into its nest?? :P
Or in plain do I need to stop the apache service before uploading/editing to the /var/www/ and its files?

---

### Post by sanderj on 2011-04-14
This is how I handle this:

login on the Ubuntu system, as root create a file in the /var/www, then chown it to my ownership, and then remotely edit it.

So:
ssh sander!<ubuntu>
sudo touch /var/www/myfile.html
sudo chown sander:sander /var/www/myfile.html

then edit the file remotely

---

### Post by falko on 2011-04-14
If you use FTP, you must either log in as the user that owns the upload directory (/var/www should be owned by www-data by default), or you run chown to change the ownership of the upload directory to your FTP user.

Instead of FTP, you can download WinSCP to your Windows computer. Enable the root account on Ubuntu...
```
sudo passwd root
```
... and log in as root using WinSCP - your permissions problems should be gone. But use with care, keep in mind you are root now!

No, you don't have to stop Apache to upload files.

---

### Post by Vintermark on 2011-04-15
Ok it was easy as setting ownership... well, i chown:ed the files in var/www and the folder /var/www into my name. 

First only changed ownership on the index.html and it let me write to it but not write any new files in the www directory. Hence i changed the ownership of that folder also.

Thanks alot!  Cookies to all! :)

---

