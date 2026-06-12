---
title: "Webalizer help"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by rbwh_wiki on 2009-01-05
Hi all,

I'm new to ubuntu

I have installed ubuntu server with DekiWiki installed - working great.

Now I'm trying to install Webalizer and when I execute 

$webalizer (as root), it came back with 

```
Webalizer V2.01-10 (Linux 2.6.27-7-server) locale: en_AU.UTF-8
Using logfile /var/log/apache2/access.log (clf)
Using default GeoIP database
Creating output in /var/www/webalizer
Hostname for reports is 'WIKISERVER'
History file not found...
No valid records found!

```

What did I miss?

any help is greatly appreciated

Thanks

---

### Post by Crafty Kisses on 2009-01-05
You might want to check the permissions and ownership on the log directory and the log files.

---

### Post by rbwh_wiki on 2009-01-05
thanks for the reply.

I have Chmod 777 to the var/www/webalizer and I still get the same message (I'm login as root) :confused:

Thanks

---

### Post by rbwh_wiki on 2009-01-05
I might have to just use other stat application. this is just driving me nuts :confused::confused:

---

### Post by rbwh_wiki on 2009-01-05
Finally i got it working. 

I put the original log file name into log.1 and it works. 

Now, My next question is :

How do I access the webalizer stat?

I tried with:

[http://mywebsite/webalizer](http://mywebsite/webalizer)

but it keeps trying to oepn up my existing website pages (not the webalizer stat)

Any suggestion is much appreciated

Thanks

---

