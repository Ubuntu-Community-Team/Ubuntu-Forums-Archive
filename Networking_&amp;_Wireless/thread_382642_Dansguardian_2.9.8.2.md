---
title: "Dansguardian 2.9.8.2"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by _Tilt_ on 2007-03-12
Hope this post is in the right place.  Iver setup an ubuntu server and have it setup as a web cache at the mo.  I want to get dansguardian on so i can use it as a web filter, Ive downloaded the latest beta of dansguardian (because i need it to log usernames) and have compiled it and installed.  The problem im encoutering is when i do the ./configure it is not configuring startup scripts ie those that go in init.d.  Ive checked in Makefile and true enough its missing a setting that configures init.d, in previous releases (from what i can tell fromt he internet) there is a variable called SYSVLOCATION in Makefile and the switch sysvdir for ./configure but these are missing.  Can someone tell me how i install the dansguardian service?

---

### Post by darrenm on 2007-03-12
why not just ```
sudo apt-get install dansguardian
``` ?

---

### Post by _Tilt_ on 2007-03-14
Because i wanted to log the user details (ie which user went to what site) using ntlm and i dont think thats supported in 2.8.  Well i fugured out how to setup the service but now dansguardian isnt logging the user details as its supposed to nor is it blocking sites. It is however logging the banned urls ie in the access log it does show the site banned but you can still view the site.  I have checked the reportinglevel and it is set at 3.  Any ideas?

---

