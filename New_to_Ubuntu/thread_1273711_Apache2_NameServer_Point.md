---
title: "Apache2 NameServer Point"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Hovercat on 2009-09-23
I got apache2 set up for 173.2.183.98 and I have a DNS server set up on [www.editdns.net](www.editdns.net), but I have no clue how to point nameservers for Apache2. Please help. :)

---

### Post by lwvmobile on 2009-09-23
Not sure what you are asking, please clarify a bit.

Are you trying to point a registered domain name to your IP adress, have it hit your apache2 server, and using domain name info point it to the correct website on your server?

---

### Post by Hovercat on 2009-09-23
> **lwvmobile said:**
> Not sure what you are asking, please clarify a bit.

Are you trying to point a registered domain name to your IP adress, have it hit your apache2 server, and using domain name info point it to the correct website on your server?


I have Apache2 being my Web Server like the HFS program. I have editdns being my DNS server to change [http://173.2.183.98](http://173.2.183.98) into [www.asskickersunited.com](www.asskickersunited.com) (My Gaming Clan).

---

### Post by ken22 on 2009-09-23
So you're looking to have this domain resolve to a particular folder as a webroot?

Add something like this to your httpd.conf, then add your website's root dir will be /var/www/www.asskickersunited.com/

```

<VirtualHost *:80>
    ServerAdmin webmaster@asskickersunited.com/
    DocumentRoot /var/www/www.asskickersunited.com/
    ServerName asskickersunited.com
    ServerAlias www.asskickersunited.com
    ErrorLog logs/asskickersunited.com-error_log
    CustomLog logs/asskickersunited.com-access_log common

</VirtualHost>

```

For your dns, have an A record pointing at your IP and a CNAME for www pointed at @.

---

### Post by Hovercat on 2009-09-23
> **ken22 said:**
> So you're looking to have this domain resolve to a particular folder as a webroot?

Add something like this to your httpd.conf, then add your website's root dir will be /var/www/www.asskickersunited.com/

```

<VirtualHost *:80>
    ServerAdmin webmaster@asskickersunited.com/
    DocumentRoot /var/www/www.asskickersunited.com/
    ServerName asskickersunited.com
    ServerAlias www.asskickersunited.com
    ErrorLog logs/asskickersunited.com-error_log
    CustomLog logs/asskickersunited.com-access_log common

</VirtualHost>

```For your dns, have an A record pointing at your IP and a CNAME for www pointed at @.

Ok, I'll add that. One question, in var/www, I make a folder named "www.asskickersunited.com" and I move the index.html in that folder?

And for the DNS, I have an A record pointing at my IP for asskickersunited.com, and an A record for [www.asskickersunited.com](www.asskickersunited.com) also. Now, I need to point ns4.us.editdns.net, ns5.us.editdns.net, ns6.us.editdns.net, ns3.eu.editdns.net, ns4.eu.editdns.net. Atleast that is what [www.editdns.com](www.editdns.com) tells me. I have my Apache set up, except that code you typed above, I will take care of that in a moment. But I need my webserver (apache) to point to the Ns domains. By the way, I live in the US, so are the eu ns domains necessary?

---

### Post by ken22 on 2009-09-23
> **Hovercat said:**
> Ok, I'll add that. One question, in var/www, I make a folder named "www.asskickersunited.com" and I move the index.html in that folder?


Correct.

If a domain is pointed at this server and you've configured apache, you shouldn't need to do anything with NS's. 

DNS is made to be redundant. Use the eu ones too.

---

### Post by Hovercat on 2009-09-23
Ok... I'll test that out in a few minutes and I'll tell you my results with [www.asskickersunited.com](www.asskickersunited.com)

:)

---

### Post by ken22 on 2009-09-23
Cool. I'll point out that DNS updates can take many hours to propagate across the internet.

---

### Post by Hovercat on 2009-09-23
I'm sad. :(


root@asskickersunited:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [fail]
root@asskickersunited:~#

---

### Post by ken22 on 2009-09-23
post the output of ```
sudo tail /var/log/apache2/error.log
```

---

### Post by Hovercat on 2009-09-23
root@asskickersunited:~# sudo tail /var/log/apache2/error.log
[Wed Sep 23 18:04:17 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Wed Sep 23 18:44:54 2009] [error] [client 173.2.183.98] File does not exist: /var/www/favicon.ico
[Wed Sep 23 18:44:57 2009] [error] [client 173.2.183.98] File does not exist: /var/www/favicon.ico
[Wed Sep 23 19:57:37 2009] [notice] caught SIGTERM, shutting down
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
root@asskickersunited:~#

---

### Post by ken22 on 2009-09-23
make sure that you've no instances of Apache running. 

look for them with ```
ps aux | grep http
```

kill them with ```
sudo kill *processid*
```

then try start apache again ```
sudo /etc/init.d/apache2 start
```

if it doesn't work...post the tail of that log file again.

---

### Post by Hovercat on 2009-09-23
root@asskickersunited:~# sudo tail /var/log/apache2/error.log
[Wed Sep 23 18:44:57 2009] [error] [client 173.2.183.98] File does not exist: /var/www/favicon.ico
[Wed Sep 23 19:57:37 2009] [notice] caught SIGTERM, shutting down
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/asskickersunited.com-error_log.
Unable to open logs
root@asskickersunited:~# 


Didn't do anything. Still Failed. It was working fine until I edited that httpd file.

---

### Post by ken22 on 2009-09-23
remove what i said to put in the apache config, get apache up again. 

you should be able to see apache's default "it works" page at [http://173.2.183.98/]("http://173.2.183.98/") if apache is ok.

---

### Post by Hovercat on 2009-09-23
Yes... I'm quite aware of


[SIZE=6]It works!

[SIZE=1]So... I'll remove the httpd, then what should I do? Also, If you need to, you can view the page at [http://173.2.183.98](http://173.2.183.98)[/SIZE]



[/SIZE]

---

### Post by ken22 on 2009-09-23
[http://173.2.183.98/](http://173.2.183.98/) doesn't show me a "It works". 

A firewall problem? Do you have port 80 open on your server?

---

### Post by Hovercat on 2009-09-23
That's because I still have that [www.asskickersunited.com](www.asskickersunited.com) folder in my var/www, but, click that link and it should come up. But still... I need to focus on getting the domain. Any other suggestions before I just give up?

---

### Post by ken22 on 2009-09-23
[http://173.2.183.98/](http://173.2.183.98/) should show me a "It works" regardless.

Domain-wise. If you've acquired the domain and set A records, you just have to wait for it to propagate, but this won't be any use to you until you fix apache.

---

### Post by Hovercat on 2009-09-23
Well... what do I need to do to Apache that will work?

---

### Post by ken22 on 2009-09-23
By default, starting apache without altering the configuration should display "It works!" from the default webroot.

We should be able to see that at [http://173.2.183.98/](http://173.2.183.98/) but it does not seem that apache is running. Remember to restart/reload apache after you change configuration files.

I got to sleep now but I've bookmarked this thread. I'll be back tomorrow.

---

### Post by Hovercat on 2009-09-23
I did. Every computer in my house says when I connect to [http://173.2.183.98](http://173.2.183.98) It says "It Works"

But... Unfortunately, I asked one of my friends to do and it didn't work. But I don't understand... I have ports forwarded to port 80, and that address is my External address. :(


Is there a way I can add an exception in the firewall for Ubuntu?

---

### Post by Hovercat on 2009-09-23
Ah. I figured it out. I believe Optimum blocks port 80. What can I do? I checked it on [www.canyouseeme.org](www.canyouseeme.org) and it replied: [COLOR=red]Error:[/COLOR] I could **not** see your service on **173.2.183.98** on port (**80**)
Reason: Connection timed out

---

### Post by Hovercat on 2009-09-24
Grrr... I used port 55902 (Don't ask why), but as with every other port, I have to add :55902 to the end of every link. I just know this will be a problem when I have a domain up and running. So, can I please have help on getting 173.2.183.98:8025 (What I'm changing the port to) into [www.asskickersunited.com](www.asskickersunited.com)

---

### Post by ken22 on 2009-09-25
current status?

---

### Post by Hovercat on 2009-09-25
What do you mean? I have the server off for now because I'm moving it into another room so I can sleep without having to listen to it all night long... but it'll be back up within two days... but since my damn ISP blocks port 80, I had to use port 8025... It's $10/month extra for my ISP to unblock 80.... So I think I'm going to have to give up on the domain.

---

