---
title: "Mounting another file system via my router"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-07-19
Hi,  In addition to my Natty laptop, I have a standalone internet radio (Musicpal) connected to my router that has a linux file system that I'm trying to access via telnet.    The IP allocated to the radio is 192.168.1.3      I can log-in to the radio and control it from a browser simply by entering 192.168.1.3 followed by username and password,  but when I try to telnet from a root terminal,  I get: 

Unable to connect to remote host: Connection refused

I suspect I may need to mount the remote radio's filesystem in my Natty first.   How would I do that?

---

### Post by linuxman94 on 2011-07-19
Did you enable telnet via the hidden device page?

[http://192.168.1.3/admin/cgi-bin/debug](http://192.168.1.3/admin/cgi-bin/debug)

---

### Post by Sleepy-zz-John on 2011-07-19
No, I hadn't done that, but I have now, and it works a treat!    Thank you!

---

