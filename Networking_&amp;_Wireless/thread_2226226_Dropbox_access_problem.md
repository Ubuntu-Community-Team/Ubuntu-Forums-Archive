---
title: "Dropbox access problem"
date: 2014-05-26
forum: Networking &amp; Wireless
---

### Post by grappler on 2014-05-26
I have two laptops, both running ubuntu 14.04 with gnome. Until a couple of weeks ago I was using dropbox on both. Now neither is able
to connect to the dropbox website - with either google-chrome or firefox. For a while I was able to continue to  update my dropbox but this has now 
ceased - perhaps because of my attempts to reinstall dropbox.  When I reinstall nautilus-dropbox it fails to download the dropbox software 
from the website. Restarting dropbox with dropbox start -i fails too:

>  
Error: Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable.


URL that failed to download: [https://www.dropbox.com/download?plat=lnx.x86_64](https://www.dropbox.com/download?plat=lnx.x86_64)
Error: None


This has happened at several different locations - accessing the internet through various servers. At my current location 
I have never had problems with dropbox before and I control the router settings - they are unchanged. 

I have no problem accessing other websites using https. 

Any ideas? Thanks!

---

### Post by grappler on 2014-05-26
OK - I've solved it. Embarrassing! I had been in China and, while there, put a couple of IP addresses of dropbox servers that worked there in my /etc/hosts file. Obviously they don't work outside China! 

Removal of the IP addresses from the hosts file fixed it!

Thanks and apologies for wasting time.

---

