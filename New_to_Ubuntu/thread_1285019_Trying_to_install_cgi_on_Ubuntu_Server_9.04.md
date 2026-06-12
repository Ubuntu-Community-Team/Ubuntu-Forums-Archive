---
title: "Trying to install cgi on Ubuntu Server 9.04"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by lcsfsr1 on 2009-10-07
Hello everyone,
I am using Ubuntu Server 9.04 command line version. I have Apache installed and it is working (I am getting the webpage with the words “It Works” on it). I also have PHP5 installed and it is also working (I am getting the webpage that gives all of the information about PHP).
 
[COLOR=red]**Now this is where the problem arise…**[/COLOR]CGI. I do not know how to get this CGI stuff installed.
 
Was CGI installed when PHP or Perl or Apache was installed**??**
Are these instructions correct**??**
What is the site configuration file**??**
What does it mean by <Virtual Host> tags**??**
I’ve seen some different things as far as the file permissions and making the file executable. 
Should I use chmod a+x or chmod 755 or chmod +x**??**
 
**These are the instructions that I am using. They are located on this website:**
[[COLOR=#000000]**http://www.ubuntugeek.com/how-to-ins...tu-server.html**[/COLOR]]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html")
 
Enable CGI and perl support for apache2 server
 
You need to install the following package
 
sudo aptitude install libapache2-mod-perl2
 
Configure a cgi-bin directory
 
You need to create a cgi-bin directory using the following command
 
sudo mkdir /home/www/cgi-bin
 
Configuring Apache to allow CGI program execution is pretty easy. Create a directory to be used for CGI programs and add the following to the site configuration file (again between the <VirtualHost> tags).
 
ScriptAlias /cgi-bin/ /home/www/cgi-bin/
 
<Directory /home/www/cgi-bin/>
Options ExecCGI
AddHandler cgi-script cgi pl
</Directory>
 
The first line creates an alias that points to the directory in which CGI scripts are stored. The final line tells Apache that only files that end with the *.cgi and *.pl extensions should be considered CGI programs and executed.
 
Test your Perl Program
cd /home/www/cgi-bin
 
sudo nano perltest.pl
 
Copy and paste the following section save and exit the file.
 
###Start###
#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing .<br />\n";
for ($i=0; $i<10; $i++)
{
praint $i."<br />";
}
###End###
make sure you change permissions on it
sudo chmod a+x perltest.pl
Now open your web browser open [[COLOR=#000000]http://yourserverip/cgi-bin/perltest.pl.It[/COLOR]]("http://yourserverip/cgi-bin/perltest.pl.It") should be working.
 
Thanks, Bobby Howerton

---

### Post by wojox on 2009-10-08
Okay so I take it you've got the 

```
sudo aptitude install libapache2-mod-perl2
```

Installed.

Now:

```
cd /etc/apache2/sites-available
```

Look for a default script called default. Then:

```
sudo nano default
```

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	[COLOR="Red"]ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
		[COLOR="Green"]AddHandler cgi-script cgi pl[/COLOR]
	</Directory>[/COLOR]

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

You will notice you already have a ScriptAlias for /cgi-bin/ pointing to /usr/lib/cgi-bin/. So all you have to do is add whats in green to the file. Then save the file Ctrl+x and exit nano

So now lets go to:

```
cd /usr/lib/cgi-bin/
```

Now open nano again:

```
sudo nano perltest.pl
```

And copy and paste the script in:

```
#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing .<br />\n";

for ($i=0; $i<10; $i++)
{
print $i."<br />";
}

###End###

```

Then save it and:

```
sudo chmod a+x perltest.pl
```

Now open your web browser open [http://yourserverip/cgi-bin/perltest.pl.It](http://yourserverip/cgi-bin/perltest.pl.It) should be working.

---

### Post by lcsfsr1 on 2009-10-22
Well i am sorry that i haven't gotten a reply back to you sooner, but
 
Wojox, your solution worked...and it worked perfectly!
 
Thank you!
 
Bobby Howerton

---

### Post by savyn on 2010-01-18
Hello Everyone,

Very new to Ubuntu (linux) in general and read various forum and threads to get .pl file to run on a new Ubuntu 9.10.  

My cgi-bin is in /var/www/site/cgi-bin.  The server will run 2 websites site1 and site 2.  Site2 is html only and site1 has some cgi and pl files.  Everytime i get to the cgi-bin/other_director the browser tries download the file or even if going directly to index.pl.  Please find attached my site-available for both default and site1 for your consideration.  
I also ran a2ensite site1 and a2ensite site2, the reloaded the apache2 server

Any help is very much appreciated.


many thanks
Savyn

---

### Post by zissshh on 2012-10-05
didnt work for me,,,404 error mini httpd error

---

