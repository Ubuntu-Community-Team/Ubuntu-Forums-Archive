---
title: "Other side of the fence"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by carparknz on 2010-02-13
Hi All
I've spent over week now sorting out my server after my original setup took next to no time. But now I'm stumped.
I have set up 4 virtual sites on a server on my local LAN as a test for our websites. All appears to be working but my browser does not see any of them. I have FTP all the data to the directories and that all works ok. (permissions set, etc)

But when I [http://xx.xxx.xx.x](http://xx.xxx.xx.x) (IP) to the server all I get is 

Index of/
Name last Mod Size Desc...

Apache/2.2.12 (ubuntu)Server at xxx.xxx.x.x Port 80 

and I see our favicon in the browser tab ??(weird)

when I [http://xxx.xxx.xx.x/mysite/index.htm](http://xxx.xxx.xx.x/mysite/index.htm), I get

Error 404 Page not found

Root directories are /home/mysite1/public_html, /home/mysite2........... and the virtual directories have the root doc path the same.

All the virtual sites are setup in /etc/apache2/default
All have been loaded using the a2ensite command
And Apache2 restarted.

I won't fill the page with lots of conf code but will respond in part with code as requested. And of course Dreamwearver won't connect either. I've seen 100's of different ways people conf Apache2 and I'm amazed at the different ways people have gone about it. Never the less none of it seems to work for me. I'm almost there, I just can not open the gate !!
Any help is appreciated 
Best to you all

PS Apache2 restart had no errors

---

### Post by bodhi.zazen on 2010-02-14
configuration of Apache is slightly different on various hosts, but it sounds as if you have not properly defined your virtual hosts.

Since yo did not post your config files I will point you to a wiki page :

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

---

### Post by carparknz on 2010-02-14
Hi, Thanks for the feed back. I had done all as per the link you posted and.still nothing

Here are some bits from the conf files.

From /etc/apache2/sites-enabled/000-default

<VirtualHost *:80>
         ServerAdmin [EMAIL="webmaster@mysite1.com.au"]webmaster@mysite1.com.au[/EMAIL]
         ServerName mysite1
         DocumentRoot /home/mysite1/public_html
         DirectoryIndex index.htm index.html
         <Directory />.................................

<VirtualHost>

The other 3 sites are the same with mysite2, mysite3,......
They are all grouped in the one file

From /etc/apache2/sites available/default

<same file as above..............>

From /etc/apache2/conf.d/virtual.conf

NameVirtualHost *:80

From /etc/hosts

127.0.0.1           Localhost
xxx.xxx.xx.x      mysite1.mysite1       mysite1
xxx.xxx.xx.x      mysite2.mysite2       mysite2
xxx.xxx.xx.x ............................

"xxx.xxx.xx.x being my local LAN server IP)

Believe me, I've been through the mill trying to analyize what's going on, but I can not seem to nail it. Thanks for your help and suggestions in anticipation. Best

---

### Post by carparknz on 2010-02-14
Hi All

Just looking at all my settings and can not find faults. But there must be something, my browser does just not see any of my virtual sites. Help !!

Thanks in advance.

---

### Post by bodhi.zazen on 2010-02-14
Please read the wiki page as it gives detailed instructions.

First, it is one configuration file per virtual host, not all in one file.

so ...

/etc/apache2/sites-available/site_1
/etc/apache2/sites-available/site_2
/etc/apache2/sites-available/site_3
/etc/apache2/sites-available/site_4

Each must have a unique document root (they can not all point to /home/user/html ).

Also your syntax is off. 

[http://httpd.apache.org/docs/1.3/vhosts/examples.html](http://httpd.apache.org/docs/1.3/vhosts/examples.html)

Finally, what are the permissions of the document root ?

See also : 

[http://heriman.wordpress.com/2008/08/05/enabling-apache-user-home-public_html-directory-in-ubuntu/](http://heriman.wordpress.com/2008/08/05/enabling-apache-user-home-public_html-directory-in-ubuntu/)

---

### Post by carparknz on 2010-02-16
Hi. Thanks for the info. I'm sinking deeper. You suggest that each virtual site must have its own file, yet the Apache link you suggested shows 2 in one file?? However I've done one only (mysite1 to get started), a2ensite, and reloaded apache2 

As:
/etc/apache2/sites-available/mysite1

All the doc roots direction go to different directories for each site. mysite1 is as:

/home/mysite1/public_html

Permissions sample (644)

-rw-r--r-- 1 root root 1379 2010-02-16 21.49 mysite1 

Still no joy. As mentioned before when browse to the IP address of the server, it connects but just shows an empty directory. If I  IP/mysite1/index.htm, I get a 404 or broken link error.

Thanks in advance

---

### Post by Peter09 on 2010-02-16
You can have more than one website ([www.xxx.xxx]("http://www.xxx.xxx")) pointing to the same document root by using the alias command. 
You define one virtual host and give it several aliases. I do this, and then through php I differentiate using the 'sitename' directive - and sorry I cannot of hand remember what the sitename directive is really called, but it returns the called website name.

---

### Post by bodhi.zazen on 2010-02-16
> **carparknz said:**
> Hi. Thanks for the info. I'm sinking deeper. You suggest that each virtual site must have its own file, yet the Apache link you suggested shows 2 in one file?? However I've done one only (mysite1 to get started), a2ensite, and reloaded apache2 

As:
/etc/apache2/sites-available/mysite1

All the doc roots direction go to different directories for each site. mysite1 is as:

/home/mysite1/public_html

Permissions sample (644)

-rw-r--r-- 1 root root 1379 2010-02-16 21.49 mysite1 

Still no joy. As mentioned before when browse to the IP address of the server, it connects but just shows an empty directory. If I  IP/mysite1/index.htm, I get a 404 or broken link error.

Thanks in advance

Hard to tell from what you posted. The last time you posted a config file your syntax was off.

Perhaps if you posted your config file.

My other thought is that you do not understand the document root ? 

does the directory "/home/mysite1/public_html" even exist ?

Are you sure it is not /home/you/mysite1/public_html ??

In that case, you enter simply

[http://ip_address/index.html](http://ip_address/index.html)

in you browser, not [http://ip_address/mysite1/index.html](http://ip_address/mysite1/index.html)

And if your config file and DNS is working, simply

[http://mysite1](http://mysite1)

---

### Post by carparknz on 2010-02-17
[FONT=Arial]Ok Guys, here&#8217;s the full blown thing:[/FONT]
  
  [FONT=Arial]In   &#8216;/etc/apache2/sites-available/mysite1&#8217; I have:[/FONT]
  
  [FONT=Arial]<VirtualHost 192.168.0.9:80>[/FONT]
  [FONT=Arial]        ServerAdmin webmaster@mysite1[/FONT]
  [FONT=Arial]        Servername mysite1[/FONT]
  [FONT=Arial]        DocumentRoot /home/mysite1/public_html[/FONT]
  [FONT=Arial]        DirectoryIndex index.htm index.html[/FONT]
  [FONT=Arial]        <Directory />[/FONT]
  [FONT=Arial]                Options FollowSymLinks[/FONT]
  [FONT=Arial]                AllowOverride None[/FONT]
  [FONT=Arial]        </Directory>[/FONT]
  [FONT=Arial]        <Directory /home/mysite1/public_html>[/FONT]
  [FONT=Arial]                Options Indexes FollowSymLinks MultiViews[/FONT]
  [FONT=Arial]                AllowOverride None[/FONT]
  [FONT=Arial]                Order allow,deny[/FONT]
  [FONT=Arial]                allow from all[/FONT]
  [FONT=Arial]        </Directory>[/FONT]
  
  [FONT=Arial]        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/[/FONT]
  [FONT=Arial]        <Directory "/home/mysite1/public_html/cgi-bin">[/FONT]
  [FONT=Arial]                AllowOverride None[/FONT]
  [FONT=Arial]                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch[/FONT]
  [FONT=Arial]                Order allow,deny[/FONT]
  [FONT=Arial]                Allow from all[/FONT]
  [FONT=Arial]        </Directory>[/FONT]
  
  [FONT=Arial]        ErrorLog /var/log/apache2/error.log[/FONT]
  
  [FONT=Arial]        # Possible values include: debug, info, notice, warn, error, crit,[/FONT]
  [FONT=Arial]        # alert, emerg.[/FONT]
  [FONT=Arial]        LogLevel warn[/FONT]
  
  [FONT=Arial]        CustomLog /var/log/apache2/access.log combined[/FONT]
  
  [FONT=Arial]    Alias /doc/ "/usr/share/doc/"[/FONT]
  [FONT=Arial]    <Directory "/usr/share/doc/">[/FONT]
  [FONT=Arial]        Options Indexes MultiViews FollowSymLinks[/FONT]
  [FONT=Arial]        AllowOverride None[/FONT]
  [FONT=Arial]        Order deny,allow[/FONT]
  [FONT=Arial]        Deny from all[/FONT]
  [FONT=Arial]        Allow from 127.0.0.0/255.0.0.0 ::1/128        <<<<<<<<< What&#8217;s this ????? The problem ??????[/FONT]
  [FONT=Arial]    </Directory>[/FONT]
  [FONT=Arial]</VirtualHost>[/FONT]
   
  [FONT=Arial]There are three other files in the same directory and in each case they are called mysite2, mysite3 and mysite4 each pointing to the relevant file[/FONT]
  
  [FONT=Arial]There are four full blown websites in separate directories as:[/FONT]
  
  [FONT=Arial]/home/mysite1/public_html[/FONT]
  [FONT=Arial]/home/mysite2/public_html[/FONT]
  [FONT=Arial]/home/mysite3/public_html[/FONT]
  [FONT=Arial]/home/mysite4/public_html[/FONT]
  
  [FONT=Arial]in /etc/apache2/conf.d/virtual.conf I have[/FONT]
  
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# Multiple Virtual Sites[/FONT]
  [FONT=Arial]#[/FONT]
  [FONT=Arial]NameVirtualHost 192.168.0.9:80[/FONT]
  [FONT=Arial]Listen 80[/FONT]
  
  [FONT=Arial]All have been activated by the command  a2ensite and apache2 reloaded.[/FONT]
  
  [FONT=Arial]In  etc/hosts I have[/FONT]
  
  [FONT=Arial]127.0.0.1         localhost[/FONT]
  [FONT=Arial]192.168.0.9     mysite1.mysite1  mysite1[/FONT]
  [FONT=Arial]192.168.0.9     mysite2.mysite2  mysite2[/FONT]
  [FONT=Arial]192.168.0.9     mysite3.mysite3  mysite3[/FONT]
  [FONT=Arial]192.168.0.9     mysite4.mysite4  mysite4[/FONT]
  
  
  [FONT=Arial]If I enter [http://ip_address/index.html]("http://ip/") how do I access the four sites separately ??[/FONT]
  
  [FONT=Arial]I thought I would have to   [http://ip_address/mysite1/html](http://ip_address/mysite1/html) (or [http://ip_address/~mysite1/html]("http://ip_address/%7Emysite1/html"))[/FONT]
  
  [FONT=Arial]When I use "Putty&#8221; to access my server with logon and password [/FONT]
  
  [FONT=Arial]I&#8217;m at:
justme@servername:~$  
I assume this is root.  When I check my directory (to see if it exists) I end up at:  
justme@servername:~$ /home/mysite1/public_html (all the html files and other sub directories)[/FONT]
  
  [FONT=Arial]Find the error I have and I&#8217;ll consider you my &#8216;Best&#8217;est Buddy&#8217;. Have fun and many thanks in anticipation. By the way, we are heading up to 7 sites now, once I get all this working.[/FONT]
  
  [FONT=Arial]I&#8217;m still on the wrong side of the fence.  [/FONT]

---

### Post by bodhi.zazen on 2010-02-17
> **carparknz said:**
> [FONT=Arial]Ok Guys, here’s the full blown thing:[/FONT]
  
  [FONT=Arial]In   ‘/etc/apache2/sites-available/mysite1’ I have:[/FONT]
  
  [FONT=Arial][/FONT]<clip>
   
  [FONT=Arial]There are three other files in the same directory and in each case they are called mysite2, mysite3 and mysite4 each pointing to the relevant file[/FONT]
  
  [FONT=Arial]There are four full blown websites in separate directories as:[/FONT]
  
  [FONT=Arial]/home/mysite1/public_html[/FONT]
  [FONT=Arial]/home/mysite2/public_html[/FONT]
  [FONT=Arial]/home/mysite3/public_html[/FONT]
  [FONT=Arial]/home/mysite4/public_html[/FONT]
  
  [FONT=Arial]in /etc/apache2/conf.d/virtual.conf I have[/FONT]
  
  [FONT=Arial]#[/FONT]
  [FONT=Arial]# Multiple Virtual Sites[/FONT]
  [FONT=Arial]#[/FONT]
  [FONT=Arial]NameVirtualHost 192.168.0.9:80[/FONT]
  [FONT=Arial]Listen 80[/FONT]
  
  [FONT=Arial]All have been activated by the command  a2ensite and apache2 reloaded.[/FONT]
  
  [FONT=Arial]In  etc/hosts I have[/FONT]
  
  [FONT=Arial]127.0.0.1         localhost[/FONT]
  [FONT=Arial]192.168.0.9     mysite1.mysite1  mysite1[/FONT]
  [FONT=Arial]192.168.0.9     mysite2.mysite2  mysite2[/FONT]
  [FONT=Arial]192.168.0.9     mysite3.mysite3  mysite3[/FONT]
  [FONT=Arial]192.168.0.9     mysite4.mysite4  mysite4[/FONT]
  
  
  [FONT=Arial]If I enter [http://ip_address/index.html]("http://ip/") how do I access the four sites separately ??[/FONT]
  
  [FONT=Arial]I thought I would have to   [http://ip_address/mysite1/html](http://ip_address/mysite1/html) (or [http://ip_address/~mysite1/html]("http://ip_address/%7Emysite1/html"))[/FONT]
  
  [FONT=Arial]When I use "Putty” to access my server with logon and password [/FONT]
  
  [FONT=Arial]I’m at:
justme@servername:~$  
I assume this is root.  When I check my directory (to see if it exists) I end up at:  
justme@servername:~$ /home/mysite1/public_html (all the html files and other sub directories)[/FONT]
  
  [FONT=Arial]Find the error I have and I’ll consider you my ‘Best’est Buddy’. Have fun and many thanks in anticipation. By the way, we are heading up to 7 sites now, once I get all this working.[/FONT]
  
  [FONT=Arial]I’m still on the wrong side of the fence.  [/FONT]

I do not see anything wrong with your config file, at least nothing obvious.

The only problem I see is some confusion with your url.

With that configuration, it you use

[http://ip_address](http://ip_address) => You should get the default site.

If you want site1 use

[http://[FONT=Arial]mysite1](http://[FONT=Arial]mysite1) , without an ip address.

Of course you need either DNS or [/FONT][FONT=Arial]mysite1 in /etc/hosts on the client[/FONT]

---

### Post by carparknz on 2010-02-18
Hi

If I [http://ip_address](http://ip_address) I get (from post #6)
 
"As mentioned before when browse to the IP address of the server, it connects but just shows an empty directory."

If I

[http://mysite(n](http://mysite(n)), [http://mysite(n)/index.htm](http://mysite(n)/index.htm), [http://ip_address/mysite(n](http://ip_address/mysite(n)), [http://ip_address/~mysite(n](http://ip_address/~mysite(n)) 

or any other variations bear no fruit ???

DNS has been setup as in above post (#9/#10)

Confused, yes so am I.

best

---

### Post by carparknz on 2010-02-21
Hi All

I just can not get my browser to see the virtual sites. I've read another couple hundred suggestions and they all it's easy?????????????  
I'm at an empasse. total stop and meltdown. If someone could look at my code as above and adise what I'm doing wrong. It's all there, I just can not get to it.

If I  [http://xx.xxx.xxx.xx](http://xx.xxx.xxx.xx) I get the "Index of"  blank page. If I try anything else I get a 404 error.

Most greatfull for any suggestions.

---

