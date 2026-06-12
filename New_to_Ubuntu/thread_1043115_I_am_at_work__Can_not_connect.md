---
title: "I am at work : Can not connect"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by piloti on 2009-01-18
When I am in the office I can not connect to the Ubuntu 'package update' service. I am on the web through the proxy [I am in the office now as I write this!] so I now that works.
I have updated / added the proxy to both Firefox and the Proxy manager in Ubuntu but it eventually just times out. The error messages are below.
#Thoughts ?#

P.
________________
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_GB.bz2)  Unable to connect to archive.canonical.com http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by albinootje on 2009-01-18
> **piloti said:**
>  I have updated / added the proxy to both Firefox and the Proxy manager in Ubuntu but it eventually just times out.

Where's the "Proxy manager" in Ubuntu ?

Can you try this instead :
[http://blogs.sun.com/venky/entry/using_apt_get_with_a](http://blogs.sun.com/venky/entry/using_apt_get_with_a)

---

### Post by Michael.Godawski on 2009-01-18
hi, 
not a proxy expert myself but perhaps have a look at :


[LIST]
[*][https://help.ubuntu.com/community/AptGet/Howto#Setting](https://help.ubuntu.com/community/AptGet/Howto#Setting) up apt-get to use a http-proxy
[/LIST]

---

