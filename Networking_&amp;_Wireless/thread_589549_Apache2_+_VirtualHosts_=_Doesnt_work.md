---
title: "Apache2 + VirtualHosts = Doesnt work?"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by Der_Idiot on 2007-10-24
Alright, I've spent the last 18 hours getting to know ubuntu, and I love it so far! I installed LAMP, and I'm well on my way to setting up a webserver, in fact I'm entirely complete. The only issue that remains, is virtual hosts.

I have setup my apache2.conf file as such:

```
NameVirtualHost *:80

<VirtualHost *:80>
        ServerName www.my-domain.com
        ServerAlias blog.my-domain.com
        DocumentRoot /var/www/wordpress
</VirtualHost>

<VirtualHost *:80>
        ServerName forum.my-domain.com
        DocumentRoot /var/www/phpBB2
</VirtualHost>
```

I also placed the servername into httpd.conf

```
ServerName mydomain.com
```

Should I be using [www.mydomain.com](www.mydomain.com) rather then just mydomain.com  ??

I have nothing in my /var/www directory except the phpBB and the wordpress/ directories. Both are on the same server, by the way.

Now, if I type any of the three virtualhost names (www. forum. or blog.) they all point to /var/www/wordpress. Wordpress itself is rather broken, as if the CSS table wasn't present. Not sure if that's an internal problem or not. As for phpBB, I can't even get to it. It's as if the server has reset it's home directory to /var/www/wordpress instead of /var/www

Any help? :confused::confused:

Edit: With the first block of code above left in and wordpress properly configured, that portion of the virtualhosts is working. However, I still cannot get phpBB2 to work. forum. still takes me to the blog rather then the forum.

---

### Post by conjur3r on 2007-10-24
Start by putting configuration information to the right file.  Take a look here: [http://ubuntuforums.org/showthread.php?t=584865](http://ubuntuforums.org/showthread.php?t=584865)

At the end of all of your changes, you should have three separate virtual host conf files.  These should be default (assuming you will use it for your [www.)](www.)), forum, and blog.

---

### Post by Der_Idiot on 2007-10-24
Alright, so I leave default alone, do I copy everything but the top line for the others, or do I make a new one without all that in it with just what I posted in my first code block on the top post? Also, if I empty out httpd.conf (Only has ServerName [www.mydomain.com](www.mydomain.com) specified), it gives me an error about not being able to determine FQDN, should I specify this in the default config since it will be pointing to www. ?

Strange that I didn't see anything about this in the docs.. But thanks for your help.

Edit: If I type Hostname and Hostname -f I get the name I gave the server, not my domain. Should I change this? Ah~ So frustrated and yet entertained. Also;

I went into /etc/apache2/sites-available and made a forum and blog files, which look like so:

```
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName forum.mydomain.com
        DocumentRoot /var/www/phpBB2
</VirtualHost>

```
```
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName blog.mydomain.com
        DocumentRoot /var/www/wordpress
</VirtualHost>

```

Here's the more entertaining part! In Firefox2 on my win2003 machine, blog, forum, and www, all point to the blog. _But_, in internet explorer it loads forum. without any hitches. www. and blog. both load a index.html file I put in /var/www meaning something is wrong with blog. correct?

So the issues now, are my firefox being strange (nonfactor), and blog. being redirected to www.

---

### Post by Der_Idiot on 2007-10-24
Resolved. blog. was redirecting visitors to www. due to an internal setting in wordpress which specified it's own domain. Very confusing up to when I corrected it.

More:

WordPress address (URL): 
Blog address (URL): 

Both were set to www. which caused to blog to redirect you upon opening blog.mydomain.com.

Thanks for your information, it was a big help. I can usually figure things out on my own, I just need a little 'push' in the right direction. :)

---

### Post by conjur3r on 2007-10-25
Excellent work!  It's rewarding solving problems with little help hey.

---

