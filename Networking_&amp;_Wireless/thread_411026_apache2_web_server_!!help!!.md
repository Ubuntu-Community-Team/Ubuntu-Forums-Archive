---
title: "apache2 web server !!help!!"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by kylet450 on 2007-04-16
hi,

im kylet450 and i have had some trouble with apache2 in making a web server. i followed the book called 'ubuntu hacks' and its a good book but i'm still stuck.

heres the tutorial i followed ( from ubuntu hacks )
------------------------------------------------------------
THE BITS I HAVE PUT IN *ITALICS* I AM NOT SURE ON.

ANY HELP WOULD BE GREATLY APPRECAITED, 

KYLET450


Serve web content using the massively popular and capable Apache web server.

Ubuntu makes an ideal web-server platform, with Apache and a huge range of supporting software available quickly and easily from the official Ubuntu archives. But just installing the software gets you only halfway there: with a few small tweaks, you can have a very flexible and capable web-hosting environment.
Install Apache

First, install Apache:

**$ sudo apt-get install apache2**
            


Then, make sure Apache is running:

**$ sudo /etc/init.d/apache2 restart**
            


The Apache installation will create a directory at /var/www, which is the document root of the default server. Any documents you place in this directory will be accessible via a web browser at [http://localhost/](http://localhost/) or the IP address assigned to your computer.
Install PHP

PHP is a server-side scripting language that is commonly used by content-management systems, blogs, and discussion forums, particularly in conjunction with either a MySQL or Postgres database:

**$ sudo apt-get install libapache2-mod-php5**
            


Restart Apache to make sure the module has loaded:

**$ sudo /etc/init.d/apache2 restar**t
            


To check that the module is loaded properly, create a PHP file and try accessing it through the web server. PHP has a built-in function called phpinfo that reports detailed information on its environment, so a quick way to check if everything is working is to run:
[I]
sudo sh -c "echo '<?php phpinfo( ); ?>' > /var/www/info.php"[/I]


and then point your browser at [http://localhost/info.php](http://localhost/info.php) to see a page showing the version of PHP that you have installed.

One possible problem at this point is that your browser may prompt you to download the file instead of displaying the page, which means that Apache has not properly loaded the PHP module. Make sure there is a line in either /etc/apache2/apache2.conf or /etc/apache2/mods-enabled/php5.conf similar to:

AddType application/x-httpd-php .php .phtml .php3


If you make that change, you'll need to stop and start Apache manually to make sure it re-reads the configuration file:
[B]
$ sudo /etc/init.d/apache2 stop[/B]
**$ sudo /etc/init.d/apache2 start**
            


Configure Dynamic Virtual Hosting

Web servers typically host multiple web sites, each with its own virtual server, and Apache provides support for the two standard types of virtual server: IP-based and name-based:


IP-based

    These virtual servers use a separate IP address for each web site. This approach does have some advantages, but due to the shortage of IPv4 addresses, it's usually used only as a last resort, such as when SSL (Secure Sockets Layer) encryption is required.

Name-based

    These virtual servers share a single IP address among multiple web sites, with the server using the Host: header from the HTTP request to determine which site the request is intended for. The usual way to achieve this is to create a configuration for each virtual server individually, specifying the name of the host and the directory to use as the "root" of the web site. However, that means you have to modify the Apache configuration and restart it every time you add a new virtual server.

Dynamic virtual hosting allows you to add new virtual hosts at any time without reconfiguring or restarting Apache by using a module called vhost_alias. Enable vhost_alias by creating a symlink in Apache2's mods-enabled directory:
[I]
$ sudo ln -s /etc/apache2/mods-available/vhost_alias.load \\
                 /etc/apache2/mods-enabled/vhost_alias.load[/I]
            


To allow the module to work, there are some changes that need to be made to /etc/apache2/apache2.conf to turn off canonical names, alter the logfile configuration, and specify where your virtual hosts will be located. Add or alter any existing settings to match the following:

[I]# get the server name from the Host: header
UseCanonicalName Off

# this log format can be split per virtual host based on the first field
LogFormat "%V %h %l %u %t "%r" %s %b" vcommon
CustomLog /var/log/apache2/access_log vcommon

# include the server name in the filenames used to satisfy requests
VirtualDocumentRoot /var/www/vhosts/%0/web
VirtualScriptAlias /var/www/vhosts/%0/cgi-bin
[/I]

Create the directory that will hold the virtual hosts:

**$ sudo mkdir /var/www/vhosts**
            


Create a skeleton virtual server:

**$ sudo mkdir -p /var/www/vhosts/skeleton/cgi-bin**
$ **sudo cp -a /var/www/apache2-default /var/www/vhosts/skeleton/web**
            


Restart apache2 so the configuration changes take effect:
[B]
$ sudo /etc/init.d/apache2 restart[/B]
            


[I]You are now ready to create name-based virtual hosts by copying the skeleton to the hostname you want it to respond to. For example, to create a new virtual server for [www.example.com](www.example.com), you would simply run:

$ sudo cp -a /var/www/vhosts/skeleton /var/www/vhosts/
               
                  [www.example.com](www.example.com)
               
            


Any HTTP connections made to your server with the Host: header set to [www.example.com](www.example.com) will now be answered out of that virtual server.

To make the virtual hosts accessible to other users, you will need to put appropriate entries in a publicly accessible DNS server and have the domains delegated to it, but for a quick local test you can edit your /etc/hosts file and add an entry similar to:

127.0.0.1 [www.example.com](www.example.com)[/I]

------------------------------------------------------------------------
i also have some errors:

when i type apache2 on my termanial i get:

kyle@kyle:~$ apache2
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
kyle@kyle:~$

---

### Post by proxima estacion on 2007-04-16
> **kylet450 said:**
> hi,

im kylet450 and i have had some trouble with apache2 in making a web server. i followed the book called 
i also have some errors:

when i type apache2 on my termanial i get:

kyle@kyle:~$ apache2
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
kyle@kyle:~$


If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then edit gksudo gedit /etc/apache2/apache2.conf and add 'ServerName localhost' at the end of the file.

that was a piece of advice from this excellant tutorial [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

good luck.

---

