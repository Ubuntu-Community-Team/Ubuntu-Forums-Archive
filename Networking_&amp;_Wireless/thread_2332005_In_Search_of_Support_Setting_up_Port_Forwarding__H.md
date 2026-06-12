---
title: "In Search of Support Setting up Port Forwarding / HTTPS"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by extrobe on 2016-07-27
Hello, I'm a relative newbie, setting up a nas system

I'm using Ubuntu Server 16.x, running Owncloud 9.x and Ajenti web management interface

I've got everything working nicely - OC & Samba can see my other system devices, I can access OC internally on http and Ajenti on https - and even setup my first cron jobs and groups :)

However, I'm trying to setup access to OC externally, over https

*(At this time, I have no intention to access ajenti externally, which runs on port 8000)*

Because I also run another device using the standard http & https ports, I need to use different ports. I've gone with 89 for http, and 489 for https (*no real reason behind those, may well change them*)

Using port 89 for http, I've managed to setup external access to OC. However, my efforts to setup https (be it internally or externally) are proving a little futile - and I lose access to both OC and in some cases Ajenti - and have conceded I'm swimming just a little out of my depth now!

In my /etc/apache2/ports.conf file, I've updated to


```
Listen 80
Listen 89


<IfModule ssl_module>
#       Listen 443
Listen 489
</IfModule>


<IfModule mod_gnutls.c>
#       Listen 443
Listen 489
</IfModule>

```
And, in my  /etc/apache2/sites-enabled/000-default.conf file
```

<VirtualHost *:89>
         ServerName sub.domain.com


        # Redirect permanent / https://sub.domain.com:489/


          ServerAdmin webmaster@localhost
          DocumentRoot /var/www/owncloud


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

*(At one point, I have *:89 separate to *:80 - but it didn't seem to like me having both in that file, so just updated 80 to 89)*

When I un-comment the redirect, I do get 'redirected' to port 489, but get a page can't be loaded

I tried adding this to the same file...

```
<VirtualHost *:489>
        DocumentRoot /var/www/owncloud
        ServerName sub.domain.com
</VirtualHost>

```
But that made no difference either

I've seen references to editing virtual hosts within httpd files - but couldn't track these down and wondered if they were the same thing as the default.conf file I'm editing.

Happy to do reading, and have no problem doing trial & error - but now worried I'm going to screw something up properly, so would welcome any pointers on where I'm going way off piste.

Thank you!

---

### Post by TheFu on 2016-07-27
I've always used a reverse proxy to handle HTTPS stuff, though I don;t believe it is secure enough to be trusted for internal file access. For that, use either sftp or a full VPN like openvpn.  I realize that I disagree with lots and lots of others on this.  Plus, I don't consider anything using a userid/password to be secure. Key-based authentication is so, so, so, so much better than passwords.

Just one of the possible issues with HTTPS: [http://arstechnica.com/security/2016/07/new-attack-that-cripples-https-crypto-works-on-macs-windows-and-linux/](http://arstechnica.com/security/2016/07/new-attack-that-cripples-https-crypto-works-on-macs-windows-and-linux/) , but there are many, many, issues.

Purely personal preference, but I've seen HTTP on 80, 8080, 8000, 9000, and 82, but never 89. Some outbound firewalls and proxies might block any unpopular ports,  I've seen it at many small to mid-sized companies where their firewall wasn't smart about protocols and just worked at the port level.  I've seen hotels block odd ports too.  For HTTPS, 443, 8443 are common. 489 seems like an already used port, don't know why ... my mistake. it is 4899 that is the RA-admin port.

Thought if you used gnuTLS that name-based SSL connections could work with many clients.  Never tried it myself, always just use a different port (like you are doing) for each SSL site. 

Just throwing this out ... have you considered using openvpn for all connectivity back home? It would be more secure and remove the need for https.  There are great, free, F/LOSS clients for every OS I've used. Management tools should never be available directly over the internet. NEVER.  If desktop OSes are the only consideration, then ssh tunnels would be easier to setup while still being MORE secure than HTTPS.

IMHO.

Sorry I don't have any specific help.  We stopped using apache years ago here.

BTW, welcome to the forums.

---

### Post by extrobe on 2016-07-28
Thanks for taking the time to reply TheFu
Yes, my port selection was pretty arbitrary and do plan to figure out a better selection!
I did have a go with openvpn before (against my other NAS), but pretty sure our organisation is blocking the vpn protocols. (They 'allow' (well, don't block) most cloud storage providers, but do block most others ports/protocols - RDP, Plex etc)

---

### Post by TheFu on 2016-07-28
> **extrobe said:**
> Thanks for taking the time to reply TheFu
Yes, my port selection was pretty arbitrary and do plan to figure out a better selection!
I did have a go with openvpn before (against my other NAS), but pretty sure our organisation is blocking the vpn protocols. (They 'allow' (well, don't block) most cloud storage providers, but do block most others ports/protocols - RDP, Plex etc)

Work networking - their network, their rules.  At that location, just use the data plan on your phone.

A possible way around the filters is to use ssh or openvpn on port 443/tcp and tunnel through that. 
[http://www.howtogeek.com/121698/how-to-route-all-your-android-traffic-through-a-secure-tunnel/](http://www.howtogeek.com/121698/how-to-route-all-your-android-traffic-through-a-secure-tunnel/) has a guide.

But we are away from your question - getting https working on apache.
[https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)  in their example, there is a certificate section for each virtual host. Your post doesn't show those lines.

---

### Post by extrobe on 2016-07-28
> **TheFu said:**
> Work networking - their network, their rules.  At that location, just use the data plan on your phone.

Oh, I agree - in fact, they offer a wireless network for just those purposes, and being on a laptop, I can quickly switch between them :)

> **TheFu said:**
> 
But we are away from your question - getting https working on apache.
[https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)  in their example, there is a certificate section for each virtual host. Your post doesn't show those lines.

Yep, I was missing a couple of things - links to certificates.
But more importantly - after many hours of searching, testing, searching again - I found the key thing I was missing - I hadn't actually enabled ssl

```
sudo a2enmod ssl
```

and suddenly everything sprang to life! Probably so obvious to many of you :)

Didn't help that my ISP and/or Router block port 443 either, which just made it harder to figure out what the heck was going on, but apart from some tidying up of the virtual hosts file, things are looking much better now!

---

### Post by TheFu on 2016-07-28
I find it best to stay with the examples FROM THE SOURCE (apache.org). Be careful googling for answers, since people have been blogging with varying levels of understanding.  When I was new to Unix/Linux, it was hard to know when someone knows a tiny bit or is a true expert.  Experts usually know 50 different issues and have to figure out which of those are happening.  Noobs will claim "THIS" is the problem, because it was there issue (or they believe it was their issue).  I've seen lots of so-called _fixes_ posted everywhere that don't make any sense.

Plus with every LTS release, we've had a new line of apache to deal with.  The 2.2 --> 2.4 change caused lots of issues for many people. They changed the Allow/Deny techniques. They also made config files have to end in .conf ... which was a new mandate.  I remember these because I was burned by them on apache servers that hadn't needed to be touched in 10+ yrs through multiple upgrades.

Anyway, pretty much you had to figure the ssl part out, though I should have told you to look at the apache log files to see what was failing.  Also, there is a config tester that is part of the apache package ... don't remember the name.  Or I could be confusing this with another daemon. Hard to say.

Always check the log files. Always.

---

### Post by extrobe on 2016-07-28
Actually, the one bit I am still trying to figure out - because I'm using a custom port for https, I want to redirect any http traffic on that port to https

I thought I could do something like this...

```

    RewriteEngine On 
    RewriteCond %{HTTPS} off 
    RewriteRule ^(.*)$ https://my.domain.com:1234 [R,L]

```

but this gives a BAD REQUEST error. Not end of the world, but will be a nice loose end to tie up!

---

