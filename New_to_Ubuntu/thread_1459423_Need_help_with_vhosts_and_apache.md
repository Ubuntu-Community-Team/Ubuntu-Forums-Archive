---
title: "Need help with vhosts and apache"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by dandenton on 2010-04-21
I really need some kind-hearted soul to help me out. I am running Ubuntu 9.10 Desktop and have installed the LAMP package using tasksel and choosing LAMP. It works. Then I tried adding 3 vhosts following several different "simple" tutorials. None of them worked for me so I decided to try Webmin and that has also failed to give me the results I wanted. After enabling (a2ensite) my three sites, they all seem to point to the same folder, the standard "It Works!" page. After using a2dissite default, I was able to get to the first of my vhosts but then the other two vhosts ended up pointing to the first vhost. I have added and removed so many things in the hosts file and the httpd.conf file that now I don't know how to proceed. If you think you can help me or at least give me a link to a tutorial that really does have ALL the steps, I would really be grateful. Thanks, Dan

---

### Post by gmargo on 2010-04-21
I just ran through this tutorial, which creates three hosts www.example.{com,net,org}.

"Hosting multiple websites with Apache2"
[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

The article uses /home/www/ as the base; I changed all instances to /var/www/.

I edited /etc/hosts so that the www.example.{com,net,org} domains point to localhost (or whatever machine you're running it on).  And it works for me - going to [http://www.example.com/](http://www.example.com/) (for example) gives me an empty directory listing with a page footer saying [www.example.com]("http://www.example.com").  Similar for .net and .org.  Tested on 9.10 Karmic.

---

