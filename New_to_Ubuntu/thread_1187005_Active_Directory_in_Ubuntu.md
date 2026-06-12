---
title: "Active Directory in Ubuntu?"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by nVee on 2009-06-14
Hey everyone!

Well i am a LONG time windows user and my Linux skills are about 3, so please be patient with me and my questions as I will most likely ask them in a Microsoft way :)

At our office, we want to move away from the MS enviroment and take the Ubuntu approach. We currently have a "file server" running XP Pro :) and about 10 desktop clients.

Our needs at this stage is to run an actual server OS (ubuntu server) on our server and then have the desktop users (or herewith referred to workstations) connect to the server and enforce workstation or group policies to the actual workstations like you can find in MS active directory. This is handy because you can force desktop background, disallow access to the hard drive, disable downloading or installing applications ect) which is an effective solution for us to make sure our workstations will be trouble free at all times.

Other requirements are:


[LIST]
[*]File server with username and password access to the server
[*]Bandwidth monitoring
[*]Use the server as our internal mail server
[*]Running the server as a testing server for our web based projects
[*]Printer management and monitoring
[/LIST]
That is it in a nutshell, would you say that Ubuntu or any other Linux server OS can provide us with a ideal solution for our needs?

---

### Post by luuke on 2009-06-14
nVee, this is definitely possible.  In fact, I would say it is EASIER in ubuntu than windows.

-For file server you could use an FTP server or Apache with .htaccess.

-Ifconfig has built in bandwidth monitoring but you could look into something more sophisticated like tc (traffic controller).

-For mailserver, you could follow this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

-Depends on what the project is, you probably want to install Apache.

-http://ubuntuforums.org/showthread.php?t=18395... also, google CUPS.

Hope this helps!

---

### Post by nVee on 2009-06-14
Thank you for your response!

That brings me to my last but most important topic, group policies? I have googled quite a number of terms and from the most of the info I have been receiving, it would appear that Ubuntu does not have a interface or application like Microsoft Active Directory to manage client and group policies. IS there a 3rd party application which we can get and install on Ubuntu server which can do these tasks for us?

---

### Post by Cheesemill on 2009-06-14
Not that I know of.

If you want to use group policies you're going to have to stick with a Microsoft DC.

---

