---
title: "Questions, Questions"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by macmike on 2010-05-08
Ok here is what I have so far and what I want to do. I want to host my 2 websites and a mailman mailing list. 1 Site I do using Dreamweaver to write and edit the files. The other site is coming from a .mac account hosting so I want to make it new in WordPress. Of course the mailman is a mailing list currently hosted by a company. 

I have installed Ubuntu 10.04 Desktop and lamp server files. Have it configured. I have apache2.2 configured for Virtual hosting of the two websites. Done nothing on mailman yet. Now I need to know how to install a FTP server, which one is best and a Control Panel which would be best. I need to get this where I can install without having to be local to the server. Also how and where do I install the Word Press files. I have set up the folders for the WordPress site. It is /var/www/wilmingtoncoc.com is that where I would put the wordpress files?
 
Any and all help appreciated. Feel free to email me if you would like as well.
mail at mikealrhughes dot com.

Thanks in advance

Mike

---

### Post by johngreth on 2010-05-08
The wordpress files are in a good spot, assuming that that is the folder that the virtual server points to.

Also, I use vsftpd for my ftp because of the security, but I have a lot of problems with it because I never really figured out how to configure it. Now I have to log in to the server remotely and change the permissions every time I upload something. It's a pain, but I'm sure its possible to configure so you don't have to do that, I just don't know how. I also installed webmin to help configure it, but it didn't do much good.

I also don't know much about email. I started playing around with it, but decided I didn't need it.

these may help:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/Servers#File%20Server](https://help.ubuntu.com/community/Servers#File%20Server)
[https://help.ubuntu.com/10.04/serverguide/C/file-servers.html](https://help.ubuntu.com/10.04/serverguide/C/file-servers.html)
[https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto](https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto)
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

I know you are using ubuntu desktop, but these may help anyway.
For the remote access you may be able to just enable it using remote desktop instead.

Also, did you install the server using tasksel?

---

### Post by macmike on 2010-05-09
Didn't know anything about Tasksel until you mentioned it. I went and used that still no luck. 
I tried installing the proftpd program still no avail. I have my wilmintoncoc.com mapped to my public IP right now. I don't know if that is the problem or not. Haven't gotten to anything where I can do a User Name and Password in yet. I don't know if I need a blow this install away and start over with Ubuntu Server and use the Tasksel to install. I guess I need a check list to go through for a good install. I know I need two websites on this box and the mailman list. Need some type of FTP some kind of control panel. Then WordPress for the one Website and a mailman install. Can you give me a check list install this do this setting, and etc.?

Mike

---

