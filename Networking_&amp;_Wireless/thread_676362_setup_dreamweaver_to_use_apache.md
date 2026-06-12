---
title: "setup dreamweaver to use apache?"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by erosion on 2008-01-23
Hello,
I set unbuntu server with LAMP , I then went to configure Dreamwever to use the Apache web server as a testing server though the network . 
Unfortunity it doe not work and after reading for days i am still confused. 
The problem seem to be that after placing a file on the server and confirming that it is on the server , then using the browser to see the file is says that it cannot be found!.
I looked into the apache config file in /etc/apache2/apache2.conf and within that it read ( apart from other things):
```
# The following lines prevent .htaccess and .htpasswd file from being viewed by web clients
<Files ~"^\.ht">
Order allow,deny
Deny fron all
</Files>
```
does this meen that a web browser cannot see the file or am i confused, I am new to the configeration of Apache and would like to know how to make this work, has anyone got any idea as to what to do?:confused:

---

### Post by erosion on 2008-01-25
No! I is not.

---

### Post by erosion on 2008-01-25
well, i live and learn, after configuring that ubuntu server hosts file and the XP's host file and the laptops Hostfiles, it was found that silly me had 2 firewalls on. I had norton which i knew about and i discovered that silly me had also the windows firewall, The ICM files had to be configured on norton be br able to ping.
Now I can ping from every machine to every machine and get a reply !:)
So this proves that the computers can see and reply to each other.
So that is the first step.......
The next step is to learn about how to set up Apache, all the business about virtual servers.
 so I can have multiple websites running on the testserver, I need to understand the various directory structures and  how a url maps onto a part of the directory structure
this wll help in the configuration of Dreamweaver, so webfiles get put in the right place.
The hurdle are falling..slowly ,but, surely. I will let you all know how it progresses

---

