---
title: "Create a folder called 'ampache' in /var/www  help please"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Peterfc on 2010-11-18
Hi 

I am trying to setup Ampache an Internet Radio.

 [http://www.muktware.com/a/50/379/16/2010/470?page=0,1](http://www.muktware.com/a/50/379/16/2010/470?page=0,1)

I have downloaded the tar.gz file i am asked to create a folder Ampache in /var/www and extract the tarball into it. In /var/  there is no folder WWW 
I have tried to create a folder called WWW and place it into the /var/ but it says. Error while moving WWW   when i show more details it says Error moving file  Permission denied. 

On my desktop I have created a folder Ampache and extracted the tarball into it. I have created a folder called WWW and placed the ampache folder into it with the extracted into it. Still i cant put the WWW folder into the /var/

I am normally quite good at following instructions but this sorry i need help.

Thanks for reading

---

### Post by ubudog on 2010-11-18
Is Apache installed?  Normally it should create the /var/www directory.  Also, since there may be a permissions issue, you may be better off just extracting the file to your home directory, then copying it like this:

```
sudo cp -a Ampache /var/www/
```

(Make sure you have Apache installed, and the Ampache fully extracted to your home directory) 

Hope that helps. :)

---

### Post by Peterfc on 2010-11-18
Hi and thanks for the help

I used " sudo apt-get install apache2 " to install Apache.

I downloaded Ampache and tried to extract it to /var/www and i got the error message  below


Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///var/www"

Peter

---

### Post by ubudog on 2010-11-18
Ok, then Apache is installed correctly - great.  Now, extract the Ampache file into the home folder.  Then, open a terminal (Applications>Accessories>Terminal) and type the following.  

```
sudo cp -a Ampache /var/www
```

That will copy the Ampache directory to /var/www, and it should be accessible via "localhost/Ampache" in Firefox or any browser.  Also, nitko is a great security auditing tool, you may want to look into that. 

PS: sudo asks for a password, it is normal that it is blank

---

### Post by Peterfc on 2010-11-18
Hi Ubudog

Thanks that has worked i now have /var/www with a folder Ampache in it and when i open all seems to be there. 

I must now go to work but i will be back on the task tomorrow.

Thanks

Peter

---

### Post by ubudog on 2010-11-18
Cool!  Let me know if you need anything else.  Also, for hosting, check out Amazon EC2.  Very, very cool stuff. :p

---

### Post by Peterfc on 2010-11-19
OK i have the first part done. Now i need help with MYSQL?


The Error message i get is Error: Unable to make Database Connection Access denied for user 'root'@'localhost' (using password: NO) 


In Synatic Manager i am shown as having Mysql server is installed


In the Terminal i did Mysql versionand the version i have is mysql  Ver 14.14 Distrib 5.1.49, for debian-linux-gnu (i686) using readline 6.1


    * A MySQL Server with a username and password that can create/modify databases
    * Your webserver has read access to the /sql/ampache.sql file and the /config/ampache.cfg.php.dist file

---

### Post by ubudog on 2010-11-19
Check out this page: [https://help.ubuntu.com/community/ampache](https://help.ubuntu.com/community/ampache)

---

### Post by steev182 on 2010-12-09
I followed the instructions in that gguide, but I seem to have problems:

I setup a vm of Ubuntu 10.10 Server to use as an Ampache server.

I installed ampache with sudo apt-get install ampache

Then I added an alias in apache...

/etc/apache2/conf.d/ampache

```
Alias /ampache /usr/share/ampache

<directory />
DirectoryIndex index.php
Options Indexes MultiViews
AllowOverride None 
Order allow,deny 
Allow from all
</directory>
```

When I try to navigate to [http://myampacheserver/ampache](http://myampacheserver/ampache) I get a forbidden error. When I go to [http://myampacheserver/ampache/www](http://myampacheserver/ampache/www) the page works.

How can I make it so I can just use [http://myampacheserver/ampache?](http://myampacheserver/ampache?)

---

### Post by steev182 on 2010-12-09
I found the fix in another thread.

Basically the symlink to the default ampache.conf file isn't created during installation.

to do it yourself, you need to remove any symlinks created earlier or dodgy config files you tried writing earlier and then do this:
```
sudo ln -s /etc/ampache/ampache.conf /etc/apache2/conf.d/
```

then you need to restart apache
```
sudo service apache2 restart
```

---

### Post by ubudog on 2010-12-09
So does everything work now?

---

### Post by emma_peel on 2010-12-16
It worked for me.

---

