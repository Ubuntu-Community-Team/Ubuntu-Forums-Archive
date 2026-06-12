---
title: "Help Identifying Problem"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by 10sJunkie on 2009-02-11
The symptom: my site files aren't visible. When you type [www.mydomain.com](www.mydomain.com) in a browser - what you get is the ISPConfig default welcome.html page for that domain. The index page I have uploaded is not shown.

The background is this:
I have just finished the (8.04) installation with ISPConfig installed and running fine. I can access ISPConfig, upload files via FTP etc. I have a static IP address with my domain registrar pointed to the IP...

The site shows in the DNS list in ISPConfig and the files I uploaded are going into the default location (/www).

Any idea why I can't see my sites?
TIA
Rebecca

---

### Post by Tony Flury on 2009-02-11
something that used to hit me - I would upload index.html - server would be look for index.htm as the default.

have you tried fetching the fils explicitly : [www.mydomain.com/index.html](www.mydomain.com/index.html)

---

### Post by 10sJunkie on 2009-02-11
Yeah... thanks for the idea but I tried fetching explicitly and got no new results.

---

### Post by halitech on 2009-02-11
I've never used ISPconfig but is there a setting in it to say where the files are to be served from? Maybe its pointing to another location instead of /var/www (or where ever you have apache pointed to)

also, have you tried by using [http://127.0.0.1](http://127.0.0.1) and seeing what loads?

---

### Post by 10sJunkie on 2009-02-12
The default directory is supposed to be /var/www but I can't find any place to check that other than the page where you set up a site. On that page the directory selection defaults to www - so I didn't mess with it.

---

