---
title: "Help with ftp, WordPress and Some sort of Control Panel"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by macmike on 2010-05-27
Hi well with the help of the forum I got my Web Server doing Virtual Name Hosting.
Now I am needing information on the following. 

Getting ftp going - I have installed vsftpd and proftpd. Not sure which one is best to use. Want to use that for adding content to the mikealrhughes.com web site.

Need help with installing and getting wordPress going on my wilmingtoncoc.com site. Probably want to install it in my wilmingtoncoc DocumentRoot folder.

I know the fellow that helped me get the directories sorted got in by way of Samba and SSH. I don't know how to use those either. 

Also what do you recommend for a control panel? Someone told me ebox was good someone else said Webmin. I did see that C panel is out of my price range. Something similiar to C panel would be great. Also need to know how to get into these programs to configure.

Anyone know how to set up ebox? It is asking me for the URI of the LDAP server to use. I have no idea!

Any help appreciated. 

Mike Hughes

---

### Post by halitech on 2010-05-27
both vsftpd and proftpd are good. There are instructions here on setting up vsftpd:
[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

here is some info on wordpress: 
[http://codex.wordpress.org/Getting_Started_with_WordPress#Installation](http://codex.wordpress.org/Getting_Started_with_WordPress#Installation)

for a control panel, I would go with ebox because webmin has some issues with the way Debian and Ubuntu package things and could break things.
[https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)

---

### Post by macmike on 2010-05-28
Good morning. I made a lot of progress last night with my Linux Server. At least I have learned to get into some areas without having to be at the server. I can now do it remotely. I have one website completely on the Server. Will need to get a CGI script somewhere to get my mailing forms going again. 

I am trying to attempt to put WordPress on another site on the box. I have downloaded it to this computer and will ftp it over to the server into the documentRoot Wilmingtoncoc. In reading the download instructions it is telling me to create a MySQL database. I know I have MySQL on here but don't know how to create a database. It is also telling me to go to phpMyAdmin. Has anyone done this that can give me a hand?

Mike

---

### Post by halitech on 2010-05-28
there are instructions here for setting up the atabase using both phpmyadmin and the terminal
[http://codex.wordpress.org/Installing_WordPress#Using_phpMyAdmin](http://codex.wordpress.org/Installing_WordPress#Using_phpMyAdmin)

you may need to install phpmyadmin if you don't already have it

---

