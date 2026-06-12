---
title: "Python not working"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by RiverNet on 2010-01-24
Yes, sorry, another thread about this...

I installed the lamp package some time back as I want to host python based scripts.  The default install of apache worked pretty well.  The doc root was /var/www and the cgi-bin root was... something weird, I forget exactly what it was.  I was able to create python scripts and run them.  Proof of concept!

The wrinkles started when I tried to start using FileZilla to simplify uploads from my development machine.  FZ was able to transfer to the document root just fine, but for some reason refused to do anything with the default cgi-bin root.  I fussed with permissions and whatnot to no avail.  Since cgi-bin was in a weird place, I tried moving it to /var/www/cgi-bin, which made FZ happy, but has broken python.  (error log info below)

I have been scouring the forums and find lots of advice on setting up python, but after trying most of it, it's still broken and I'm afraid I've made an even bigger mess of my configs etc.  Even more disheartening is that many of the threads end with "Hey guys!  Thanks for all the help!  Nothing I tried seemed to help but then it just started working!  I have no idea what I did!"  NOT helpful :P

Based on various threads, I've tried updating packages, installing mods, fussing with file and directory permissions, changing apache configs, etc...  I have lost track of the exact sequence, so I'm hoping if I post up some of my info you'll notice the problem.

apache2.conf--no changes to default

httpd.conf--
```
<Location /server-info>
	SetHandler server-info
	Order deny,allow
	Deny from all
	Allow from 127.0.0.1
	Allow from 192.168.1
</Location>

```

sites-available/default-- this is where we put server specific stuff now, right?
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/content/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	<Directory /var/www/content/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/cgi-bin/
	<Directory "/var/www/cgi-bin/">
		AllowOverride None
		AddHandler cgi-script .pl .cgi
		AddHandler mod_python .py
		PythonHandler mod_python.publisher
		PythonDebug On
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel debug

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

Now, a recent development is confusing me even more.  Until recently, I had .py under the cgi-script handler.  I was getting this
```
[Sun Jan 24 10:12:27 2010] [error] [client 192.168.1.103] (2)No such file or directory: exec of '/var/www/cgi-bin/environment.py' failed, referer: http://192.168.1.115/
[Sun Jan 24 10:12:27 2010] [error] [client 192.168.1.103] Premature end of script headers: environment.py, referer: http://192.168.1.115/

```

which confused me, in that I thought the Premature end.. message meant the file was processed but gave invalid output.  Or is the error that apache can't find the file at all, therefore no headers?  Regardless, I can do this
```
mjj@UbuLAMPy:/var/www/cgi-bin$ python3.1 /var/www/cgi-bin/environment.py
Content-type: text/html
<pre>
<strong>Python 3.1.1+ (r311:74480, Nov  2 2009, 15:45:00) 
[GCC 4.4.1] </strong>
</pre>

```

But, see my most recent config above in /default.  I've installed the python mod into apache and moved the .py handling to mod-python.  Now when I attempt to browse to cgi-bin/environment.py all I get is a "404 file not found" error, and the following error.log trace:

```
mjj@UbuLAMPy:/var/log/apache2$ tail --lines=5 error.log
[Sun Jan 24 11:46:08 2010] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sun Jan 24 11:46:08 2010] [notice] mod_python: using mutex_directory /tmp 
[Sun Jan 24 11:46:08 2010] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_python/3.3.1 Python/2.6.4 configured -- resuming normal operations
[Sun Jan 24 11:46:21 2010] [notice] mod_python (pid=19193, interpreter='UbuLAMPy.localdomain'): Importing module '/var/www/cgi-bin/environment.py'
[Sun Jan 24 11:46:21 2010] [debug] mod_deflate.c(615): [client 192.168.1.103] Zlib: Compressed 299 to 231 : URL /cgi-bin/environment.py, referer: http://192.168.1.115/

```

So, when I have .py under cgi-script handling, I get a 500 error with Bad headers (or was it no headers), and when I have .py under mod-python, I get a 404 file not found error but the error log seems to indicate it has loaded the file.  Ugh!  (Presumably it's desirable to have mod-python handle my scripts and I should try to get this configuration to work?)

I do want to use python 3, I don't care about backward compatibility.

What else might be of use?

```
mjj@UbuLAMPy:/var/www/cgi-bin$ uname -a
Linux UbuLAMPy 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64 GNU/Linux
mjj@UbuLAMPy:/var/www/cgi-bin$ cat /etc/issue
Ubuntu 9.10 \n \l

mjj@UbuLAMPy:/var/www/cgi-bin$ aptitude show libapache2-mod-python
Package: libapache2-mod-python
State: installed

mjj@UbuLAMPy:/var/www/cgi-bin$ ls -l environment.py
-rwxr-xr-x 1 www-data mjj 321 2010-01-23 17:23 environment.py


```

Looking over this all, I am wondering if I have an additional issue here... is the mod-python I'm running restricted to python < 2.7?  If so how do I install the python 3+ mod?  I'm having trouble sorting out the various issues, I sure hope you have some ideas!

tia,

Mark

---

### Post by cariboo on 2010-01-25
have you set the new location of the cgi-bin directory in /etc/apache2sites-available? The cgi-bin directory in in /usr/lib/ on purpose, to make it harder for crackers to access it.

---

### Post by RiverNet on 2010-01-25
> **cariboo907 said:**
> have you set the new location of the cgi-bin directory in /etc/apache2sites-available? The cgi-bin directory in in /usr/lib/ on purpose, to make it harder for crackers to access it.

Thanks for the reply.

I thought I had!  Take a look above, I've posted the contents of my sites-available/default file.  Anything look amiss there?

---

### Post by RiverNet on 2010-01-31
I am back in business and wanted to make brief note of what I ended up doing.  I had so many mistakes piled up on that first install it's a wonder anything worked.  A few problems arose from the LAMP package itself so I built a bare server and installed what I needed as I went.

Just in case anyone is as clueless as I am, here's what I did (abbreviated, post up if you need elaboration).  Note I did not try to make this a tutorial; not all steps are noted (restarting servers after config, etc..) so be alert to "filling in between the lines":

My manual LAMP setup:

Server
-Bare server setup from ubuntu-9.10-server-amd64.iso
-selected Expert Mode at install screen (only deviations from defaults noted)
-declined pcmcia card support
-setup network with fixed address
-selected targeted initrd
-selected no additional packages
-skipped grub step, installed lilo on "mbr"
-ran aptitude, loaded package list, updated security patches and 'upgradable patches'

gcc
-update lib6/g++/gcc per [this]("http://evalinux.wordpress.com/2008/12/04/installing-python-30-on-ubuntu-810-intrepid-ibex/")

Python 3.1
-sudo apt-get install python3.0
-sudo apt-get install python3-minimal 

SSH 
-sudo apt-get install ssh-server
-sudo ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub
-additional step as I had accessed the same IP address previously from my client, and it was unhappy that the server was 'different'
--deleted /users/[mylogin]/.ssh/known_users (host RSA key had changed)

Setup time daemon
-install openntpd
-sudo apt-get install openntpd

Sqlite3 (Okay so my LAMP substitutes sqllite for MySQL, it's good for what I need)
-apt-get install sqlite3
-apt-get install libsqlite3-dev (needed to compile sqllite support into apache2)

Apache ([primary reference]("http://httpd.apache.org/docs/2.0/install.html"))
-wget [http://apache.multihomed.net/httpd/httpd-2.2.14.tar.gz](http://apache.multihomed.net/httpd/httpd-2.2.14.tar.gz)
-apt-get install zlib1g-dev ([reference]("http://davidwinter.me.uk/articles/2006/10/17/building-apache-22-from-source-for-ubuntu-dapper/"))
-verify build-essential and linux-headers-2.6.31-17-server are current ([reference]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Installing_a_package_from_source")) 
-unpack apache sources into a work directory
-./configure, use --enable-layout=Apache   (default, but just to be sure; see config.layout for other options)
-make (takes forever)
-sudo make install (also lengthy)
-edit httpd.conf
--set User apache
--set Group nogroup
--set LogLevel info
-sudo useradd apache -c "Apache2.2" -d /dev/null -g nogroup -s /usr/sbin/nologin -M (apache runs as 'apache', group 'nogroup')
---It Works!

Getting file permissions right in order to a) serve up pages and b) ftp in took some trial and error.  Mostly error.  

It took me a couple of minutes to realize my ftp was failing because... I hadn't installed an ftp server.
-sudo apt-get install vsftpd (could also use others, see [this review]("http://linuxreviews.org/software/ftp-servers/"))
-I configured my ftp server to run under a nopriv user (hey, didn't we make one up there... apache!)
-allow Local User Login in /etc/vsftpd.conf (otherwise only allows anonymous)
-created a new user 'www' and changed ownership of apache2/htdocs and apache2/cgi-conf to that user ([reference]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server#Where_To_Put_Your_Web_Pages"))
-I'm running FileZilla as a client ftp GUI which seems adequate but not outstanding.

It may be ugly but it worked.

---

