---
title: "standard LAMP help for opening php cge scripts"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by ClarkePeters on 2006-10-24
I have a basic LAMP server I use only for development (no domain) with Apache2.2 and PhP5.1.2. I know its set up right because I installed Moodle (education content manager) and it works ok. And I did a localhost/test.php (php info page) and it works fine. 

The problem is me. I'm just learning how to do php and cgi/pl scripts (practicing with basic Hello World in a php and pl script) but can't open anything in firefox. I did finally find my /usr/lib/cgi-bin so I think all my cgi/pl scripts will be fine if I park them there. But anything with php just gives me constant pop-ups from firefox asking me to open or download (save to). Hitting cancel gives me a blank page. Also, sometimes I think my html page is not in the right place or something--- locations, permissions? I don't know what's up. I'm not really sure when and how to use "localhost" in my web addresses for testing, or should I just use file:// to refer to my html and scripts?

I tried some Apache searches but really can't figure out what's goin on as the httpd.conf file seems to be deprecated with Apache2.2. I know this is an awful question with probably not enough info, but could someone help me get started? I have all this free power (thanks Ubuntu!, Apache, PhP, and Perl :) ) but I can't us it :( 

(tutorials are great, how to write script, but I haven't found one yet that addresses this basic issue for me--how to get my scripts to run)](*,)

---

### Post by funkyade on 2006-10-24
I use an ubuntu server on my home net for testing purposes (I'm a web developer).

The Ubuntu packages are great, but, for ease of setup I cannot recommend XAMPP highly enough. ([http://xampp.org/](http://xampp.org/))

Uninstall your existing Apache/PHP/MySQL etc... and use XAMPP as it works out of the box without you having to go through hoops first! You can then play with the config later if you so wish, safe in the knowledge that it was working and correctly setup in the first place...!

A more direct answer to your question would be that you have not set up your Apache filter to serve PHP pages correctly, that is why firefox is trying to download them - it doesn't understand the file extension...

You need to look in the includes for the runtime modules apache is loading and make sure apache is actually loading php. You can do it from a shell but I forget the exact command. try -

```
#> /etc/init.d/httpd --help
```
or
```
~> /etc/init.d/apache2 --help
```

for a list of options, then choose the appropriate one. You are looking to see what modules are loaded at runtime and what is compiled in.

hth

+ DO NOT use file://path/to/myscript.php to run your scripts/pages as this will either show the sourcecode or trigger firefox to download - it will show HTML files however - which can lead to confusion! Use either [http://localhost/myscript.php](http://localhost/myscript.php) or [http://192.168.0.1/myscript.php](http://192.168.0.1/myscript.php) (replace 192.168.0.1 with your IP address).

---

### Post by ClarkePeters on 2006-10-24
Ok, Xampp looks like a great idea, but for now I'll skip it. Seems it's still new (no documentation) and according to the FAQ and Forum people still can run into problems, I don't want to jump out of the frying pan into the fire. (although I think if I were starting from the beginning this would be a good idea.) Also, after I finally get things going, I'll need to setup our own server for the schools distance ed programs. I programmed a long time ago, so I'm not totally lost, but I've never tried to integrate my progs to the web. So I have much to learn in this respect.

So when I make an html file that uses php or cgi, I need to reference it via [http://localhost/file.html](http://localhost/file.html) right?  But where do I put the file.html --in the /var/www directory? Does that mean all my html files should go in /var/www ? I mean, once my project gets big, how can I manage a large number of documents all in a single folder?

---

### Post by ClarkePeters on 2006-10-24
This is what my httpd.conf file says(apache2.2)

> # This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

---

### Post by funkyade on 2006-10-24
In your httpd.conf or other included .conf you need to look for a line that says

```
DocumentRoot /var/html/www
```

or similar. That's where your html/php etc goes.

To manage lots and lots of documents, html files, scripts, etc... you can just create extra folders in DocumentRoot and reference them from the URL like so -

[http://localhost/folder-full-of-pdfs/mypdfdoc.pdf](http://localhost/folder-full-of-pdfs/mypdfdoc.pdf) is /var/html/www/folder-full-of-pdfs/mypdfdoc.pdf

[http://localhost/myblog/blogpages/home.html](http://localhost/myblog/blogpages/home.html) is /var/html/www/myblog/blogpages/home.html 

and so on...

When you are accessing this remotely you will need a fully-qualified doamin name, for example, [http://www.mywebsite.new/myblog/blogpages/home.html](http://www.mywebsite.new/myblog/blogpages/home.html) this will then point to your server's ip address using DNS records.

I would suggest investing in a couple of decent Apache books, and something about PHP if you are serious as this is a VAST topic!

hth

---

### Post by ClarkePeters on 2006-10-24
My php info() screen says I'm using Apache 2.O.55, and apache2 -v command also says Apache 2.0.55. Can't figure how I came up with 2.2 -- old age, stress? :)

but I still think I can't use the httpd.conf file, otherwise, why is it empty except for the backwards compatability notes?

---

### Post by ClarkePeters on 2006-10-24
Ok, quite by accident i found that typing [http://localhost/](http://localhost/) into the browser will give me an EXtremely familiar sight--  

```
Index of /

Name                    Last modified      Size  Description[DIR] apache2-default/        27-Jul-2006 01:50    -   
[TXT] hello.htm               23-Oct-2006 15:02   78   
[   ] hello.php               22-Oct-2006 16:04   63   
[DIR] php/                    24-Oct-2006 20:37    -   
[   ] test.php                06-Oct-2006 10:00   14   
[TXT] xubuntu-programs-lis..> 
```

Now THAT looks familiar, 8) 
however, why in the world would is my workable cgi-bin found in /usr/shar/lib/cgi-bin and not in my /var/www path? :-? 

and what is this :-k 
```
/usr/share/apache2/default-site/cgi-bin
```
and why can't I use this (my cgi pl scripts will not run from here)

I know someone holds the key for me out there.  ;)

---

### Post by ClarkePeters on 2006-10-24
Thanks Funkyade. That's a great starting point for me, and makes me more comfortable working inside my /var/www folder--was worried if I added folders I'd screw things up or something.

I was so wrapped up in my problem that I missed your post.. 
the simple things always stump us when we'ere starting out, I will certainly get more serious and get some books (I'm in Taiwan, english books are hard to come by, so ebooks, although a bit outdated, is all I have) But for now, I just need to test the software itself, which is a testmaker/CMS program. So I just need my php, pl, cgi, mysql etc all talking to each other.

any clue, though, why my workable cgi-bin is in /usr/lib/cgi-bin? will that be a problem later on?

---

### Post by ClarkePeters on 2006-10-24
correction to earlier post
the workable cgi-bin is not:
usr/shar/lib/cgi-bin  
it should be just: usr/lib/cgi-bin

---

### Post by funkyade on 2006-10-24
> **ClarkePeters said:**
> correction to earlier post
the workable cgi-bin is not:
usr/shar/lib/cgi-bin  
it should be just: usr/lib/cgi-bin

cgi-bin is usually NOT in your DocumentRoot for security reasons. It is usually somewhere like /var/www/cgi-bin with your DocRoot being var/www/html (mistyped this earlier) and Apache creates an alias to it so that cgi-bin requests are run from there.

Note that cgi-bin usually contains perl programs not php, so don't go putting your php scripts in there!

---

### Post by ClarkePeters on 2006-10-25
Thanks again funkyade. You have me goin' in the right direction. 

FYI anyone following this thread.  Here's the results; what I learned.

Ubuntu Dapper 6.06; Appache2.055

1. /usr/lib/cgi-bin -- the install automatically set my cgi-bin file in the directory location: 
```
usr/lib/cgi-bin
``` --so any .cgi .pl (perl) scripts should work from there.

This was set by ScriptAlias in my default file in directory  

```
/usr/share/apache2/config/
#filename is default (no filename extention)

##inside the file default is this line
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/::VHOSTNAME::-::PORT::

```
However, I still don't understand why my httpd.conf file is empty except for the backwards compatability note. When I search on the web about this issue, almost everything says to go in and change your SriptAlias and such in the httpd file. Maybe its because I'm using my LAMP for development only and when I go live (create a domain DNS) my httpd becomes active? well,not important right now.

2. DocumentRoot was set-up automatically as /var/www. 
(so if you put [http://localhost/](http://localhost/) in your browser you will get an index for all files and folders in the directory location /var/www).

it looks like this in the same default file:

```
DocumentRoot /var/www/::VHOSTNAME::/htdocs-::PORT::
```

(not sure about htdocs part. my Moodle (education CMS) is the only directory that has a htdocs file, so I'll need to investigate when and how to use the htdocs).

3. You can add/arrange subfolders under var/www to help you organize your files and this is what shows from the [http://localhost/](http://localhost/) address in the browser. 
So to work with your files, put them in:
```
var/www/file.name or var/www/folder/file.name 
``` 
but to access it with your browser reference:
```
http://localhost/file.name or http://localhost/folder/file.name
```

Thanks again to funkyade for explaining these basics and getting me looking in the right places.

---

### Post by az on 2006-10-25
> **ClarkePeters said:**
> But anything with php just gives me constant pop-ups from firefox asking me to open or download (save to). Hitting cancel gives me a blank page. 

Do you have libapache2-mod-php5 installed?


As for cgi, do you have php5-cgi or libapache2-mod-fastggi packages?

---

### Post by ClarkePeters on 2006-10-25
using locate, I found these files, so I think I have the libapache2-mod-php5
```

/var/cache/apt/archives/libapache2-mod-php5_5.1.2-1ubuntu3.3_i386.deb
/var/cache/apt/archives/libapache2-mod-php5_5.1.2-1ubuntu3.2_i386.deb
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.list
```

> do you have php5-cgi or libapache2-mod-fastggi packages
This I don't know, did a locate, no files or directories by those names, how can I be sure?

---

### Post by ClarkePeters on 2006-10-25
using locate, I found these files, so I think I have the libapache2-mod-php5
```

/var/cache/apt/archives/libapache2-mod-php5_5.1.2-1ubuntu3.3_i386.deb
/var/cache/apt/archives/libapache2-mod-php5_5.1.2-1ubuntu3.2_i386.deb
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.list
```

> do you have php5-cgi or libapache2-mod-fastggi packages
This I don't know, did a locate, no files or directories by those names, how can I be sure?

---

