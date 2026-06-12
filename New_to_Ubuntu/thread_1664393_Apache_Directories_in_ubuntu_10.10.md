---
title: "Apache Directories in ubuntu 10.10"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by JLSwin on 2011-01-10
I must confess I am totaly new to ubuntu or Linuz for that matter. I installed hoping to use the advantages that it is suppose to have over windows when using apache, mysql, and php. I am working on putting together a wordpress blog and for the life of me I can not find where the apache dir's are to install the files that need to run wordpress. Any help is much appreciated.

---

### Post by Mr.Luz on 2011-01-11
Hi mate,
I was in the same situation a couple of weeks ago and know exactly your pain. So I going to help you out.
1. The apache folder (or directory as is known in the linux world) and files are locates at /etc/apache2
2. Windows brain washed like us are used to the httpd.conf file to configure stuff, well as far as I can tell, at least on ubuntu (probably in linux in general) you can just forget about it. The file exists at /etc/apache2/httpd.conf but is empty and the system does not read it.
2. Instead of httpd.conf you will configure your settings at etc/apache2/sites-available/default
3. Your public_html (your website) files lives at /var/www. You can change it at the conf file mentioned on point #2. You could set it to /home/[user]/www (I have done that).
3. The conf file from point 2 is protected and only the root user can modify it. So open your command line terminal and type gksu nautilus . A file manager will open up with root user permissions for that instance only.

Hope it helps.

---

### Post by Mr.Luz on 2011-01-11
I forgot to mention. You will have to restart apache if you perform any change in the conf file. The commands are:
sudo /etc/init.d/apache2 restart
you can use also
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

Your regular user permissions are able to do this.

---

### Post by maryeliezka on 2011-01-11
I think you should download this than using that:

[http://biznetnetworks.dl.sourceforge.net/project/appserv/AppServ%20Open%20Project/2.5.8/appserv-win32-2.5.8.exe](http://biznetnetworks.dl.sourceforge.net/project/appserv/AppServ%20Open%20Project/2.5.8/appserv-win32-2.5.8.exe)

---

### Post by ditatompel on 2011-01-11
> **maryeliezka said:**
> I think you should download this than using that:

[http://biznetnetworks.dl.sourceforge.net/project/appserv/AppServ%20Open%20Project/2.5.8/appserv-win32-2.5.8.exe](http://biznetnetworks.dl.sourceforge.net/project/appserv/AppServ%20Open%20Project/2.5.8/appserv-win32-2.5.8.exe)
.exe file? That's for win* users bro..

Btw, I found quite good tutorial there [URL="http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick"]http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick
[/URL]
Hope it can be useful.

---

### Post by dysentry on 2011-01-11
Just to clarify some things for everyone (until you know this, things are a bit confusing when reading up on the web):

a default install of apache2 will put the website in /var/www

Configuration of the webserver can be done a few ways:

1) Add your website to /etc/apache/httpd.conf (which is blank by default in ubuntu 10.10).  This means all your website configuration is stored in one file.

2) Add your site as a file in to /etc/apache2/sites-available/mysite  then run the command "a2ensite mysite"
the a2ensite command = Apache2 ENable SITE (a2dissite to disable).  By running this command it creates a symlink from /etc/apache2/sites-**enabled**/mysite to /etc/apache2/sites-**available**/mysite

3) A mixture of 1 and 2

personally I would recommend option 2.  reason being is that you can have multiple sites (say the domains example.com, something.net & whatever.us) and disable one,some or all as you wish without getting the configuration mixed up between them all.

---

### Post by maryeliezka on 2011-02-15
@ditatompel:huh? so we couldn't use appserv in ubuntu???O.O

---

