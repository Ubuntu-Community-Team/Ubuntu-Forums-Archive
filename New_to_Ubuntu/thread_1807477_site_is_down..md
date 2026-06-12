---
title: "site is down."
date: 2011-07-19
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-19
site is down.  I looked at apache log.  I restarted the apache. No luck.  This is what I get down below.  What is that mean?
> 
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Sun Jul 17 06:22:58 2011] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sun Jul 17 06:22:58 2011] [notice] mod_python: using mutex_directory /tmp 
[Sun Jul 17 06:22:58 2011] [notice] Apache/2.2.14 (Ubuntu) mod_python/3.3.1 Python/2.6.5 mod_ruby/1.2.6 Ruby/1.8.7(2010-01-10) mod_perl/2.0.4 Perl/v5.10.1 configured -- resuming normal operations
[Sun Jul 17 06:42:05 2011] [notice] Graceful restart requested, doing restart

---

### Post by jtarin on 2011-07-19
I'm assuming this line:
> PHP Deprecated: Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0

Deprecation is a status applied to software features to indicate that they should be avoided, typically because they have been superseded. Although deprecated features remain in the software, their use may raise warning messages recommending alternative practices, and deprecation may indicate that the feature will be removed in the future. Features are deprecated&#8212;rather than immediately removed&#8212;in order to provide backward compatibility, and give programmers who have used the feature time to bring their code into compliance with the new standard.
In your case the comment marked with "#" are no longer used. What problems are you having besides this message?

---

### Post by 007casper on 2011-07-20
Thank you so much for your help.

I got the site up now.

Somehow it served blank pages, and didnt give any errors besides what I posted.  It happened, after I installed a few things.

I installed nginx.  However, I have the site on apache.  I was planning to serve static content through nginx.

then, I did
apt-get php5-cli php5-cgi php5-dev php-apc

then installed webalizer, then the site was gone.

I decided to back track.  So, I removed webalizer, and php-apc, reboot the server.  Nginx served its default page on all the sites on the server.  I stopped nginx.  Then, the site came back up.

I am not really sure what caused the issue, because I dont see any errors.  I checked apache logs /var/log/apache2/error.log. Maybe I am not looking at the right places.

---

### Post by jtarin on 2011-07-20
Can you telnet to the IP address of your site on port 80?

---

### Post by 007casper on 2011-07-25
yeah, I can.  What I found that the database gets disconnected when disk IO rate goes up.  Maybe, it is just coincidence.

This happens especially when there is a burst of traffic.  

Disk IO rate makes the app give 500 error.  The screen goes white, and then sometimes the cache plugin just stops working, and then the application stop connecting to the database.

I have to figure out a way to solve this issue.

Is there a good source for high redundant setup etc somewhere?  Actually, I found many, but figured maybe the community can direct me to a site that I didnt come across.

---

### Post by jtarin on 2011-07-25
Maybe I'm missing something here......what DB are you using?

---

### Post by 007casper on 2011-07-25
mysql

apache, wordpress, w3tc cache plugin.

I found out that w3tc gives error due to php.  I should dig up the exact log, and will post it here.

I should also move the static files nginx, but I got a lot of stuff on htaccess.  CDN isnt an option right now.  Because, the traffic isnt high all the time.

Anyhow, I removed the cache completely, and reboot the server.  It works like a charm so far.  Actually, it is faster.  Disk IO rate goes up, but it doesnt choke.  The site just slows down a bit.  I was really surprised.  

I cant believe not using a cache is better than using a cache. I know it is going to bite me somehow for the fact that I am not using cache.  But on load I think cache plugin just eats dust due to disk IO rate, and php.

I am trying to figure out how to make the site static without a plugin maybe.  And would like to make the site highly redundant, so it doesnt get wiped out on surge of traffic.

---

