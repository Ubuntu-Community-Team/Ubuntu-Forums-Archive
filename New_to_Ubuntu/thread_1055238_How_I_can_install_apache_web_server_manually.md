---
title: "How I can install apache web server manually?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by legolas_w on 2009-01-30
Hi
Thank you for reading my post.
I want to install apache http server in my ubunut 8.10. 
I want to install it manually because when i install it using the add/ remote program or synaptic I can not find configuration files, web root folder and so on.

If you know whether it copies the installation files like conf files, and where i should copy my html files which I need them to be served; let me know.

thanks.

---

### Post by RudolfMDLT on 2009-01-30
Hi legolas_w,

I think you have A LOT of reading up to do! :)

Start here:
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)
[http://httpd.apache.org/](http://httpd.apache.org/)

But, I think to make life easier, install WebMin.
[http://www.webmin.com/](http://www.webmin.com/)

Webmin allows you to do most of the basic configuration without having to hunt for config files or know exactly how to configure them.

Cheers,

Rudolf

PS: Apache "root" is in /var/www

EDIT - To answer your question directly - when you use synaptic or add/remove, they issue the manual command: "sudo apt-get install apache2"

---

### Post by mister_pink on 2009-01-30
Yep, the config files are in:
/etc/apache2/
And your top level html should go in 
/var/www/

Always much easier to find out how to use stuff rather than manually installing. I don't think that would solve your issues anyway - they would probably still be in the same place.

By the way, if you're used to apache on windows theres one other thing to note - permissions. You have to edit the config files as root (ie use "gksudo gedit filename") and the html files should be owned (or at least readable) by the user "www-data"

---

### Post by RudolfMDLT on 2009-01-30
Dude, Reading our posts again - we're not trying to avoid answering your question, it's just that running a webserver, even a very basic one on Ubuntu takes some know-how. 

Rather learn to use Apache as is, and post questions specifically related to problems that you have. Re-inventing one of the most successful web-servers is really not that wise! ;)

Good Luck,

Rudolf

OffTopic: If you are starting out with your own website, I recommend using webmin to do some initial configuration and then using bluefish editor to write your code - bluefish has a syntax checker and it tidies up code. [your code should be tidy to start with!] :)

---

### Post by rd123 on 2009-03-07
i am a complete newbie to LINUX and i am trying to setup a LINUX BOX it appears i have installed the apache2 server on ULTIMATE UBUNTU 1.8 and on 127.0.0.1 i get the default page index.html.

i now want to upload my website which as a windows user i would have thought was relatively easy but i cannot copy files to ///var/www/

why is this and how do i get round this

or 

how do i get my default webserver to point to a folder on my system

i have no idea what i am doing admitadly but as a long term windows user i know 

NO QUESTION IS A STUPID QUESTION please help

Anyone

Please:(

---

### Post by Mud.Knee.Havoc on 2009-03-07
> **rd123 said:**
> 
i now want to upload my website which as a windows user i would have thought was relatively easy but i cannot copy files to ///var/www/
why is this and how do i get round this

You need to use the sudo command to copy stuff there. This basically lets you run commands as root.

---

### Post by hexanol on 2009-03-07
You could also change the group permissions of /var/www to your group (you can get your group name and number with the "id" command) and change file permission of /var/www so group have write access. After that, you won't have to use sudo to copy/modify files in /var/www

Also, all we described can be done using the terminal.

---

