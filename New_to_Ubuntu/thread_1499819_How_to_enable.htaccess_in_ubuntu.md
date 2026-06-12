---
title: "How to enable.htaccess in ubuntu"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by dilantha on 2010-06-02
Hi,
 I want to enable .htaccess in apache and im really sorry for posting this as a new thread because i already saw this was discussed in a previous thread :(. But that solution did not worked for me. So that's why i thought of posting this in a new thread. I went to */etc/apache2/sites-available* and edited *default* file as below
```
DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        **AllowOverride ALL**
        Order allow,deny
        allow from all
    </Directory>
```and then restart the apache web server.but still the .htaccess is not working :(. Also i have enabled apache user directories. so im accessing my local host in
```
 http://localhost/~dilantha/  
```May be there is a different way to enable .htaccess in user directories .](*,) Please help..:(

---

### Post by lukeiamyourfather on 2010-06-02
There's a sites-enabled and a sites-available directory. Only the files in the sites-enabled directory are used. Cheers!

---

### Post by dilantha on 2010-06-02
> **lukeiamyourfather said:**
> There's a sites-enabled and a sites-available directory. Only the files in the sites-enabled directory are used. Cheers!

Hi,
 Thanks a lot for your effort but its not working yet.Here is the 000-default file inside sites-enabled folder
```
<Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        **AllowOverride All**
        Order allow,deny
        allow from all
    </Directory>

```

It already has  **AllowOverride All **in it. but still no luck :confused:. any idea?

---

### Post by lukeiamyourfather on 2010-06-02
> **dilantha said:**
> Hi,
 Thanks a lot for your effort but its not working yet.Here is the 000-default file inside sites-enabled folder
```
<Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        **AllowOverride All**
        Order allow,deny
        allow from all
    </Directory>

```

It already has  **AllowOverride All **in it. but still no luck :confused:. any idea?

What do you mean by no luck? Are you not getting the default HTML page when you browse to localhost? Or is a PHP site you have not working right?

---

### Post by dilantha on 2010-06-02
> **lukeiamyourfather said:**
> What do you mean by no luck? Are you not getting the default HTML page when you browse to localhost? Or is a PHP site you have not working right?

Hi,
 Yes..Its a PHP site. The folder which contains the .htaccess file in not visible in the localhost and when i tried to access that folder through the URL it gives me an Internal server error.

In the apache error logs it says 
```
.htaccess: Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
```So i enabled mod re-write by typing below command and restart the apache server.

```
sudo a2enmod rewrite
```Now the folder which contains the .htaccess file is visible in localhost. But when i click on that folder it asks to download a file called *McTTInre.phtml.part*. I don't know from where this file came from. Now in my apache error logs it says 

```
[Thu Jun 03 08:21:45 2010] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Jun 03 08:21:46 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 03 08:21:56 2010] [warn] RewriteCond: NoCase option for non-regex pattern '-d' is not supported and will be ignored.
[Thu Jun 03 08:21:56 2010] [warn] RewriteCond: NoCase option for non-regex pattern '-f' is not supported and will be ignored.
[Thu Jun 03 08:21:56 2010] [warn] RewriteCond: NoCase option for non-regex pattern '-d' is not supported and will be ignored.
[Thu Jun 03 08:21:56 2010] [warn] RewriteCond: NoCase option for non-regex pattern '-f' is not supported and will be ignored.
[Thu Jun 03 08:22:10 2010] [warn] RewriteCond: NoCase option for non-regex pattern '-d' is not supported and will be ignored.

[Thu Jun 03 08:22:10 2010] [warn] RewriteCond: NoCase option for  non-regex pattern '-f' is not supported and will be ignored.

```

](*,)..any idea?

---

### Post by lukeiamyourfather on 2010-06-03
Do you mind if I ask what application/site you're trying to host? The default htaccess file will work for most sites. Also check with the documentation if its a application like Wordpress, Drupal, etc. They will usually cover common problems specific to that project. Cheers!

---

### Post by deepakost on 2012-06-18
Go to Joomla Admin Panel and ->  Global Configuration  -> SEO Settings -> URL Rewriting -> Set Yes

  Now Go to Ubuntu Terminal write :-

cd /etc/apache2/sites-available$ vi default press Enter key

and after that space key it will show you different Modes on virtual terminal Select E for Edit mode 

  and Set All in first three <directory> AllowOverride All</directory> and stay Set none to last one directory and now save it as a new setting 

and then press Q for quit and exit to come out from virtual mode..

Thanx
God Bless You

---

