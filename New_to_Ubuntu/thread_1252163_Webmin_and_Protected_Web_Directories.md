---
title: "Webmin and Protected Web Directories"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by andwest on 2009-08-28
Hi there.

I have converted an old XP box into a headless web server/torrent slave machine. I used information from a few different tutorials and eventually ended up with a machine running Ubuntu Server 9.04 with OpenSSH, Apache, MySQL, PHP, ProFTPd, Torrentflux, and Webmin.

Now, the majority of the server works great. I have been able to do anything I needed to do through SSH from another machine, or through Webmin, because I am fairly new to this and still like to have some sense of what I'm doing through a GUI.

The problem I'm having right now has to do with when I try to use the Protected Web Directories in Webmin. I set up protection for a folder in my /var/www/ folder (my Apache DocumentRoot), and the module screen says it is now protected. I add a user on the next screen. But when I access that directory, I don't get an authentication dialog; I simply get the directory's Apache index.

Similarly, I don't think my folder redirects are working for Apache, either. I have tried to set up a few redirects to various folders (one for Webalizer from http://my.serv.er/webalizer to /var/webalizer/, for example), but these don't seem to be working either.

This leads me to believe it is some issue with Webmin's ability to write to .htaccess or .htpasswd files, OR an issue with Apache's ability to use these files. I don't know a lot about .htaccess or .htpasswd.

I have done a fair amount of Googling and searching online, but I still can't find a solution. Has anyone else had this problem? Am I missing something here?

Thanks.

---

### Post by pazzypunk on 2009-08-28
I'm having the same question.

---

### Post by ermski2k on 2009-10-26
This has occurred several times to me. I have recently due to hardware issues had to do a clean server install and copy over my web contents. Reinstalled webmin and manually checked the .htaccess etc files and all seems to be okay, however i no longer get an authentication login screen. Initially before this was a problem and when I got it working the first time it was by luck.

---

### Post by skodama on 2010-02-02
Hi, 
 
This might be already solved, but just in case, please try the following :
(I'm using Webmin ver.1.490)
 
1. Login to webmin
2. Select Servers->Apache Webserver
3. Select the virtual host you want to enable the password authentication (i.e. default server)
4. At "Per-Directory Options" in the lower end of the page, select "Directory /var/www/html"
5. Select "Document Options"
6. At "Options file can override..." in the middle of the page, make sure "Selected" is checked, and add check for all the options in the "below..." box
7. Restart Apache server
8. Done!!
 
Ref: see the "AllowOverride" section in Apache document
 
I hope this helps.

---

### Post by heiNey on 2013-01-06
> **skodama said:**
> Hi, 
 
This might be already solved, but just in case, please try the following :
(I'm using Webmin ver.1.490)
 
1. Login to webmin
2. Select Servers->Apache Webserver
3. Select the virtual host you want to enable the password authentication (i.e. default server)
4. At "Per-Directory Options" in the lower end of the page, select "Directory /var/www/html"
5. Select "Document Options"
6. At "Options file can override..." in the middle of the page, make sure "Selected" is checked, and add check for all the options in the "below..." box
7. Restart Apache server
8. Done!!
 
Ref: see the "AllowOverride" section in Apache document
 
I hope this helps.

sorry to bring up an old thread, but i followed this, and now it asks for a password like i want, but i cant log in with the correct user and password.  it keeps saying the credentials are wrong.

any have any ideas?

---

### Post by overdrank on 2013-01-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

