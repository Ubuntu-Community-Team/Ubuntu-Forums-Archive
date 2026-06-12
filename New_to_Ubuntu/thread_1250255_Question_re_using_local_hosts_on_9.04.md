---
title: "Question re using local hosts on 9.04"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by New Boy on 2009-08-26
A couple of years ago I successfully installed 7.04 (including LAMP) on my laptop.  I do not use it a lot, except for maintaining two web sites, which I deal with on localhost and then upload to an external host.

I have decided to install 9.04 in my desktop PC using WIMP.  I have also installed LAMP.

There seems to be a difference as to how local hosts are dealt with and I cannot get it to work on 9.04.

On my 7.04 Laptop there is a folder (apache2-default) in var/www and link files there too (including links to my two folders for my web sites and one for phpmyadmin).

On my 9.04 PC there is nothing in the var/www folder although using the browser for localhost/phpmyadmin brings up the phpmyadmin page although there is a red box there which states 'Connection for controluser as defined in your configuration failed'

If I put a link file in var/www to my web page working directory (as I have in 7.04 above) I get a 404 not found page.

Can some-one point me in the right direction for me to sort this out please.

Many thanks,
David

---

### Post by cariboo on 2009-08-26
When you point your browser to [http://loclhost](http://loclhost) do you see the It Works! message. I would look at file ownership and privileges, every thing should be owned by root and have a permission of 755.

---

### Post by credobyte on 2009-08-26
> **cariboo907 said:**
> When you point your browser to [http://loclhost](http://loclhost) do you see the It Works! message. I would look at file ownership and privileges, every thing should be owned by root and have a permission of 755.

Actually, it can be owned not only by root ( I like to chown it :-$ ).

---

### Post by New Boy on 2009-08-26
> **cariboo907 said:**
> When you point your browser to [http://loclhost](http://loclhost) do you see the It Works! message. I would look at file ownership and privileges, every thing should be owned by root and have a permission of 755.

Yes, sorry, I should have said that it contains that index file.

What is meant by 'everything'?  Sorry, I need things spelled out at the moment until I get used to the jargon again.

David

---

### Post by nandemonai on 2009-08-26
These days phpmyadmin uses apache configuration files to redirect requests from say [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to where the phpmyadmin files are stored (/usr/lib/phpmyadmin from memory).

If you take a look at the files in /etc/apache2 you should from a virtual host setup somewhere for phpmyadmin.

I'm afraid I'm not at my ubuntu box at the moment so I can't confirm locations.

---

