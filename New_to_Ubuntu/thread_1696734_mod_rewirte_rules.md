---
title: "mod_rewirte rules"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by duceduc on 2011-02-27
I am trying to rewrite some of my unfriendly URI but is not working for me. Mod_rewrite is enabled on my server.I have tested with a test page and it seems to be working; however, when I tried to rewrite this URI, it doesn't work.

[http://sub.domain.com/index.php?cmd=view](http://sub.domain.com/index.php?cmd=view)

My htaccess page.
> Options +FollowSymLinks
RewriteEngine on
RewriteRule ^/?(view|news).html$ index.php?cmd=$1 [L]
RewriteRule ^index.html$ index.php
RewriteRule ^/?test\.html$ test.php [L]

# URL rewrite rules
<IfModule mod_rewrite.c>
   RewriteEngine On
   RewriteCond %{REQUEST_FILENAME} !-f
   RewriteCond %{REQUEST_FILENAME} !-d
   RewriteCond %{REQUEST_FILENAME} !-l
   RewriteRule ^(.*)$ index.php [QSA,L]
</IfModule>


---

