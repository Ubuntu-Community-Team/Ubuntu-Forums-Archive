---
title: "Unable to access localhost"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by bbishop02 on 2007-11-27
I have installed apache2, php, and Mysql.  I checked to make sure everything is running with ps aux, and all three were running.  I put the php test page in the www folder.  

The only error I get when starting apache is could not determine servers fully quilified domain name, using (the ip address of my computer)

So here is my issue:  when I try to access [http://localhost](http://localhost) firefox times out and says the server is taking to long to respond.  
However if I go to another computer on my network and put in the ip address of my computer, it access the php test page without a problem.  

Why would I be able to access this from another computer but not on the server computer itself?

Running:
Ubuntu 6.06
network manager applet 0.6.2
wpa_supplicant

Thanks in advance!

---

### Post by smartbei on 2007-11-28
Try:
> 
gksudo gedit /etc/apache2/httpd.conf

and add
> 
ServerName localhost

to the end.

Then, run:
> 
sudo /usr/sbin/apache2ctl restart

to restart apache and try again.

These commands were taken from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).

---

### Post by bbishop02 on 2007-11-28
Worked Like a charm!  Thanks!  :)

---

