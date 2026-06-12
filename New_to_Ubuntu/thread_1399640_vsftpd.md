---
title: "vsftpd"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by carparknz on 2010-02-05
Hi All
Sorry to add another post about ftp.
I had trouble with vsftpd and Fedora and then found Fedora needed updating often. So I went to Ubuntu server 9xxxx
I've loaded Ubuntu Server and all works fine, but to ftp my test website into /home/www/public_html via vsftpd is a major.
I've read hundreds of posts where most say vsftpd is the simplist to use?????? and I've used many samples of the vsftpd conf file but everytime I get different messages on my ftp software and like last time I end up running around in circles.
Errors like:
Won't continue because of root owner - so I change that
Failed to receive response after connect - current problem
OOPS: 500 file permission errors - ?????

All the directories have 777 permission for now
vsftpd anon_root dir set to  /home/www/public_html
 
Would someone be kind to direct me to a simple config file I can connect anon to /home/www/public_html just to get me started.   At least once I can connect I can go from there.

Best to you all

---

### Post by mushwars on 2010-02-06
vsftpd is not the easiest.

I use it and love it, but it is far from easy.

Looks to me like you need to chown -R apache:<GROUPX> /path/to/public_html

that group x should have your ftp user in it, apache in it, and you in it.

you need 775 permissions on folders and 664 on files.

also you dont want that to be anon_root then anonymous users can download your website source code.

---

### Post by carparknz on 2010-02-07
Thanks Mushwars
I apprecaite your response. It looks though as if everyone is just about up to eyeballs on ftp questions. But its strange way some think it easy and others don't. Most of the conf examples for vsftpd others posted more or less led me astray. In the end I just sat down and went through it step by step with file permissions and setting vsftpd confg file options one at a time, understanding what each one did. It was a mixture between Apache and vsftpd. I've got one website sample up and running on the server (very fast), now I'm looking at adding other websites on the same server via virtual setups. Phew!!
cheers

---

### Post by mushwars on 2010-02-07
> **carparknz said:**
>  now I'm looking at adding other websites on the same server via virtual setups. Phew!!
cheers
I am using vhosts right now I have 4 going
[http://mushwars.net](http://mushwars.net)
[http://dont.fear.jp/](http://dont.fear.jp/)
[http://azu.mushwars.net/](http://azu.mushwars.net/)
[http://brett.mushwars.net/](http://brett.mushwars.net/)

---

### Post by carparknz on 2010-02-07
Hi Nushwars
Any chance of some sample setups with this virtual thing. And how do I access each website.
I've got everything on my local network server for testing via a local IP address (not accessable to to www)
My idea is to run my websites up to bebug before loading to a seperate hosting service.
I'm setting up now, like:
/home/1st site/public_html
/home/2nd site/public_html
/home/3rd site/ public_html
/home/.........
Then I'm adding users,  user '1st site', passwd 'abcdef', user '2nd site', passwd '123456'
Am I heading in th right direction ??
Thanks in advance
Best

---

### Post by mushwars on 2010-02-07
you dont want to create users for apache, it doesnt work like that, you need only to create users for FTP, so your on the right track if you plan to do that.

What you need to look for is /etc/apache2/vhost.d/ <-- thats what it is on my server, I am not sure exactly on ubuntu, but you need to find virtual hosts, then you need to create aliases... let me show you an example.

```
<VirtualHost *:80>
        ServerName dont.fear.jp
        ServerAdmin mushwars@gmail.com
        DocumentRoot "/var/www/localhost/japan/htdocs/"

        <Directory "/var/www/localhost/japan/htdocs/">
            Options Indexes FollowSymLinks
            AllowOverride All
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule alias_module>
            ScriptAlias /cgi-bin/ "/var/www/localhost/japan/cgi-bin/"
        </IfModule>

        <Directory "/var/www/localhost/japan/cgi-bin/">
            AllowOverride None
            Options None
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule mpm_peruser_module>
                ServerEnvironment apache apache
        </IfModule>
</VirtualHost>

```

---

### Post by carparknz on 2010-02-08
Hi Mushwars
Thanks for that. Just a note back to say I've read your post. I've got to earn some real money (urgent job) for the next few days. I'll try your suggestions then and let you know.
cheers and best

---

### Post by carparknz on 2010-02-11
Hi Mushwars
Ive loaded up 4 sites, all have permissions set as required and according to Ubuntu HTPPD page I've set up the four virtualhost files for sites as:

/etc/apache2/site-available/default  (site1)
/etc/apache2/site-available/site2 
/etc/apache2/site-available/site3
/etc/apache2/site-available/site4

and set each them as per your code above (as per default file as well):

<VirtualHost *:80>
        ServerName host.site1.com
        ServerAdmin [EMAIL="me@site1.com"]me@site1.com[/EMAIL]
        DocumentRoot /home/site1/public_html

        <Directory /home/site1/public_html>
            Options Indexes FollowSymLinks
            AllowOverride All......................

The others are the same except site1 is replace with site2, .......

I also changed the <VirtualHost *:80> to <VirtualHost myipaddress:80> but apache2 spat the dummy when I restarted it

My problem now is how?? do I direct my web browser to the relevant local sites ??

I'm at a block here and I find conflicting howtos on the web.
Thanks for your help in advance
Best

---

### Post by bluekwak on 2010-02-11
> **mushwars said:**
> 
 
Looks to me like you need to chown -R apache:<GROUPX> /path/to/public_html
 
that group x should have your ftp user in it, apache in it, and you in it.
 
you need 775 permissions on folders and 664 on files.
 
also you dont want that to be anon_root then anonymous users can download your website source code.
 
Hi I'm in a similar situation.  I'm new to Ubuntu and Linux of any flavour.
 
I've installed Ubuntu 9.10 and Apache2, MySQL, PHP and it is running on a home network.
 
[http://baldrick/~blackadder/](http://baldrick/~blackadder/)  from a Windows client shows the page /home/blackadder/public_html which is what I wanted.
 
However "blackadder" is trying to upload from Windows to /home/blackadder/public_html using Dreamweaver and cannot.  The connection works and "blackadder" can see the files created on the Ubuntu box.
 
The error from DreamWeaver is Access Denied.
 
I have looked at the above and I tried the command:
[INDENT][COLOR=blue]chown -R apache:ftp /path/to/public_html[/COLOR]
 
[/INDENT]..however I get the error 'invalid user'
 
Sorry I am very new to this.  I have tried a lot of web searching to get this right but I'm stumped.
 
....be gentle with me, it's my first time.

---

### Post by carparknz on 2010-02-12
Hi 
Yes, there a lot of different ways and everyone's way seems to work (for them). However as I've found out, you have to understand what's actually happening. I started out by 'try this or try that', which is really good from other people and it gives avenues you would not think of. But you still need to sit back and look at the suggested logic in depth. My original failure was 'I can do all this on a Sunday arvo', yeah right?. It just might be a '.' or ':' or '/' missing or in the wrong place. Still lots to learn and a forum is the best place to do it. I'm still working on my problems with the help of Mushwars. I'll post once I've sorted. 
Best

---

