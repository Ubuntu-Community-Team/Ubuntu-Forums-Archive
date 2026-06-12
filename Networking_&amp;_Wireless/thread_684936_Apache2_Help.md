---
title: "Apache2 Help"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by MCAccord on 2008-02-01
Hey Everyone. I just got a Linux Server up, and I'm just kind of goofing around. I've not really done anything productive as I can't seem to get anything to work, so I thought I'd try to focus on one thing. Here's as far as I got.
I've got 7.10 32-bit server
Running over SSH to my MacBook
Decided to use Wedmin
I'm trying to upload via FTP to the apace web server so that I can put a website up there that can be accessed by all of the computers on my network. When I log in with my FTP uploader I can get in, but I don't have the privlages to modify or alter anything within the /var/www/apache 2 blah blah blah folder.
Can anyone help my on setting the appropriate privileges with Webmin?

---

### Post by eric_1982 on 2008-02-01
You will need to make sure the ID you are using to connect with has the correct access. I believe the /var/www folder is owned by root.

You may need to do a chmod to that folder to allow access for the id that you are using to connect with. You will need permission to write to the folder. 

You could login with SSH and then do a chmod on the folder or you could use sudo in front of your commands. I know Apache has some documents on the best practice for security, but if the site is not going to be accessed by the outside world  then there is not to much to worry about.

If you want to login with root account you will need to change the default password. This can be done system > user and groups select root and then click on properties. You will also need to change some configuration settings to allow remote access with the root id. (its probably not the most secure but if the machine is not exposed to the outside world or some crazy guy on your network you should be ok)  By default this is disabled. I hope this can get you on the right track.

---

### Post by MCAccord on 2008-02-02
I kind of stumbled upon that, but unfortunately I can no longer get access to my web server when I type in the IP address. Whereas before I could type in the address and it would show up with the directory listing, you know? Do you know what that could be about? Kind of a noob question, but does the Server OS have a GUI that I could use opposed to the CLI? I got a little curious when you said system -> user etc.

---

