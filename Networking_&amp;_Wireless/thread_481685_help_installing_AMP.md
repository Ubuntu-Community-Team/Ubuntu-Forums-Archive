---
title: "help installing AMP"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by mkramer on 2007-06-22
I am trying to install just a very basic, local testing server.  I don't care about security, as this server is behind a firewall only connected to trusted computers.    I want it to work with no hassles, no permissions issues.  I am trying to follow this guide:

[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

Things went wrong pretty quickly.  I get an error message from apt-get:

```
sudo apt-get install apache2 php5 libapache2-mod-php5
```
```
... 
* Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

mysql-server doesn't install.  Meanwhile when I follow his testing suggestion to see if php is installed, it fails.  Unfortunately there is no suggestion about how to troubleshoot a failure.  If I insert a text file called test.php into /var/www and then navigate to [http://localhost/test.php](http://localhost/test.php), it tries to download the script instead of execute it.  This looks like php is not running.  

I've tried XAMPP, and neither php nor mysql worked (apache did work).  I uninstalled XAMPP and tried it piecemeal with this guide, and it's the same thing.  I'm now coming here for assistance.  I'll check back frequently to answer questions and give more information.  I am a complete and total linux newbie, I've been using linux for less than a month and am very disoriented here, so if you have a suggestion, please spell it out for me.  Even a little discursive explanation about what you're having me do to troubleshoot things would be very helpful.  Thanks for your time.

PS
Apache seems to be working just fine, if I navigate to [http://serverhostname/](http://serverhostname/) on any machine, I get an index of /var/www

PS how can I check to see what services are running and how do I cause programs to run on startup?

Edit: By the way, the error code I reported above is a message I got from running apt-get install a second time.  I got an error the first time but it may have been a different error.  I don't know how to uninstall the stuff to try it clean again...

---

### Post by scrupul0us on 2007-06-22
well if ur looking for a quick and dirty setup of ubuntu 7.04 follow this:

[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

skip over stuff that doesnt interest you (dns, webalizer, ispconfig, email, etc...) but the web stuff is spot on

---

### Post by mkramer on 2007-06-23
Thanks for your interest!  I just ifollowed that guide, and I have no idea what I did, but it still doesn't work.  I've done everything except install ispconfig because I  can't figure out how to do it from the d ininstallation guide on the ispconfig.org site.

---

### Post by az on 2007-06-23
> **mkramer said:**
> 
Edit: By the way, the error code I reported above is a message I got from running apt-get install a second time.  I got an error the first time but it may have been a different error.  I don't know how to uninstall the stuff to try it clean again...

That's the problem.

run

sudo apt-get -f install 

and post the output.

As well, do you have mixed repos?  You should only have one release of Ubuntu in your sources.list.  Nothing else.  No foreign repos.

---

