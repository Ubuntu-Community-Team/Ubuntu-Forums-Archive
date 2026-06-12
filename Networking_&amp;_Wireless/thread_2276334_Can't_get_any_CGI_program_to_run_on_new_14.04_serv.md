---
title: "Can't get any CGI program to run on new 14.04 server installation"
date: 2015-05-01
forum: Networking &amp; Wireless
---

### Post by henrylaw on 2015-05-01
Ubuntu 14.04.2 server.  Default Apache install with no virtual hosts or alternate ports.  The default "It Works" page comes up but I can't get any CGI program (or even a text file in the cgi-bin library) to come up: I just get 404 errors.

/usr/lib/cgi-bin is the correct library:
[FONT=courier new]wizard@sirius:/etc/apache2$ grep -R ScriptAlias
conf-available/serve-cgi-bin.conf:        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
conf-enabled/serve-cgi-bin.conf:        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/[/FONT]

It's enabled for CGI execution:
[FONT=courier new]wizard@sirius:/etc/apache2$ grep -R ExecCGI
conf-available/serve-cgi-bin.conf:            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
conf-enabled/serve-cgi-bin.conf:            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch[/FONT]

The known-good CGI program (written in Perl, it lists the environment) has a .cgi extension, which is enabled:
[FONT=courier new]wizard@sirius:/etc/apache2$ grep -R AddHandler *
mods-available/mime.conf:    AddHandler cgi-script .cgi
mods-available/mime.conf:    AddHandler type-map var
mods-enabled/mime.conf:    AddHandler cgi-script .cgi
mods-enabled/mime.conf:    AddHandler type-map var[/FONT]

The known-good program is executable:
[FONT=courier new]wizard@sirius:/etc/apache2$ ls -l /usr/lib/cgi-bin/printenv.cgi
-rwxr-xr-x 1 root root 262 May  1 19:21 /usr/lib/cgi-bin/printenv.cgi[/FONT]

The /usr/lib/cgi-bin directory is owned by root and is 755:
[FONT=courier new]wizard@sirius:/etc/apache2$ ls -ld /usr/lib/cgi-bin
drwxr-xr-x 2 root root 4096 May  1 22:25 /usr/lib/cgi-bin[/FONT]

... and still I get "The requested URL /cgi-bin/printenv.cgi was not found on this server", with this in the access log:
[FONT=courier new]$ tail -1 /var/log/apache2/access.log
172.24.0.204 - - [01/May/2015:22:49:46 +0100] "GET /cgi-bin/printenv.cgi HTTP/1.1" 404 505 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:36.0) Gecko/20100101 Firefox/36.0" [/FONT]

What on earth am I doing wrong?  It's something simple, I'm sure, but I've tried everything I know.

---

### Post by TheFu on 2015-05-01
Please post the actual config file that is in sites-enabled/.
As you know, the location of directives inside the file matters.  On my box, it is named "000-default.conf"

BTW - I'd never seen **grep -R** before - THANKS!
Ah ... it isn't working on my AIX, HP-UX, Irix, or Solaris machines. :(

---

### Post by henrylaw on 2015-05-02
Here is the relevant .conf file, called conf-available/serve-cgi-bin.conf
```
wizard@sirius:/etc/apache2$ egrep -v "^#" conf-available/serve-cgi-bin.conf
<IfModule mod_alias.c>
    <IfModule mod_cgi.c>
        Define ENABLE_USR_LIB_CGI_BIN
    </IfModule>

    <IfModule mod_cgid.c>
        Define ENABLE_USR_LIB_CGI_BIN
    </IfModule>

    <IfDefine ENABLE_USR_LIB_CGI_BIN>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Require all granted
        </Directory>
    </IfDefine>
</IfModule>
```

(About grep -R .. why would they not do that?)

---

### Post by henrylaw on 2015-05-02
Just noticed those IfDefine things, which I've never looked at.  I'll check that out later; gotta run.

---

### Post by TheFu on 2015-05-02
Where's the DocumentRoot set? I'd guess that is the issue.
Also - something needs to have a host setup - methinks.
```
<VirtualHost *:80>
  DocumentRoot /var/www/html/www.example.com
.....
.....   put all your settings here ... 
.....
</VirtualHost>

```
Just a guess - I've never seen a website without those minimal settings. OTOH, we don't use apache much anymore.

As to the grep option - the -R is new.  Swapping in a new option might break things for scripts which have been working for 20-30 yrs and that is bad.  I have some scripts from the early 1990s that have been running daily all that time. I'd be pissed if a vendor changed something and broke them.

---

### Post by henrylaw on 2015-05-02
Been chasing down this IfModule stuff.  It needs mod_cgi.c loaded, so I looked for LoadModule statements for that:
[FONT=courier new]/etc/apache2$ grep -R LoadModule * | grep mod_cgi
mods-available/cgid.load:LoadModule cgid_module /usr/lib/apache2/modules/mod_cgid.so
mods-available/cgi.load:LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so[/FONT]

So that looks OK on the face of it.  But I then found a way to list the modules loaded, thus:
[FONT=courier new]wizard@sirius:/etc/apache2$ apache2ctl -M
Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)[/FONT]
 ... and lots more, but not including anything with cgi in the name.

Whereas on a system on which CGI does work (Jupiter, running Ubuntu server 12.04) it does seem to be loaded:
[FONT=courier new] henry@jupiter:/etc/apache2$ apache2ctl -M | grep cgi
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
Syntax OK
 cgi_module (shared)[/FONT]

Am I onto something here?  It looks as if the cgi module isn't being loaded on Sirius, whereas it is on Jupiter; but the LoadModule statements are the same on both servers, viz this:
[FONT=courier new]wizard@sirius:/etc/apache2$ grep -R LoadModule * | grep cgi
mods-available/cgid.load:LoadModule cgid_module /usr/lib/apache2/modules/mod_cgid.so
mods-available/proxy_scgi.load:LoadModule proxy_scgi_module /usr/lib/apache2/modules/mod_proxy_scgi.so
mods-available/proxy_fcgi.load:LoadModule proxy_fcgi_module /usr/lib/apache2/modules/mod_proxy_fcgi.so
mods-available/cgi.load:LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so[/FONT]

Still needing help here, folks; even if it's just to say that I'm barking up the wrong tree.

---

### Post by henrylaw on 2015-05-02
OK, well I'm sorry you guys have been watching me debug this, and thanks to TheFu for getting up early to help (Metro-ATL presumably means Atlanta GA?), but I've found the answer. Even though it looked as if those LoadModule statements were loading the CGI module they were only pretending.  I issued 
```
sudo a2enmod cgi
sudo service apache2 restart
```
... and everything burst into life. I know what I've done but I don't know why I had to do it, given what I found.  But there we are.

---

### Post by TheFu on 2015-05-02
Apache is very mature, so they've thought of reasons to be able to enable/disable sites and modules across a server. Really all that command does is create a symlink to the mod-enabled/ directory.  Also, you can "reload" apache - no need to interrupt currently running connections with a restart.

Yep - Atlanta area currently.  I'm a morning person - no alarm clock needed. Up doing server maintenance. Been up about an hour already. ;) Just waiting for some diving (FINA/NVC Diving World Series 2015 - London) to start later today. Hopefully the crowd won't scream when the divers are airborne like they did yesterday. Someone could die.

For the the **egrep -R** stuff made this completely worthwhile!

FYI - you've posted in the networking/wireless forum - perhaps posting in the "server" forum where lots of apache admins hang out would have worked faster?

---

