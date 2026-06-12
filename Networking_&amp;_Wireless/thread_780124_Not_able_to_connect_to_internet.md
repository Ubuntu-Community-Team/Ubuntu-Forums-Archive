---
title: "Not able to connect to internet"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by lucky.developer on 2008-05-03
Hey, i found a big problem in Ubuntu.

I am not able to connect to the internet now in ubuntu...whereas in windows i can. i am having a dsl broadband connection. i was using internet till yesterday in ubuntu.. but today i am not able to do that.

i even tried reconfiguring my ubuntu pppoe connection by typing

sudo pppoeconf


then i typed

plog

to test the connection. it also responded well.

but when i opened firefox and typed google.com... no progress

what may be the problem?

---

### Post by lucky.developer on 2008-05-03
please help

---

### Post by toallpointswest on 2008-05-03
Have you looked into your /etc/resolv.conf after connecting, it sounds like you're missing your dns server entries.

---

