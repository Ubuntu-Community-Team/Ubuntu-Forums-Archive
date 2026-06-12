---
title: "Is there a problem with proxy?"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by gpap1266 on 2007-08-02
My computer is behind proxy in a corporate network.
Comparing with my home computer i see that some applications don't work propertly...
Lets say gmail-notfier cannot connect. (for gmail notifier i read that there is a broblem with proxy[ https://bugs.launchpad.net/debian/+source/gmail-notify/+bug/66276]("https://bugs.launchpad.net/debian/+source/gmail-notify/+bug/66276") )
All the weather desklets don't connect...
Everything else it's ok, let's say i get updates, browsing it's ok e.t.c

it's important to see that problems because some of us we try to "put" ubuntu in our "working life" and you can imagine the fighting form the windows "side" ;-)

Enyone with ideas :(

---

### Post by dougfractal on 2007-08-02
Have you 
```
gnome-network-preferences
```,  also found in preferences,  set the proxy settings? 

you may also have to set environmental variable if you use terminal.

export http_proxy='proxy.domain: port'

---

### Post by gpap1266 on 2007-08-03
i done everything and still nothing....:confused:

---

### Post by dougfractal on 2007-08-07
[http://gmail-notify.sourceforge.net/faq.php](http://gmail-notify.sourceforge.net/faq.php)
> Q: Whenever I start Gmail notifier, it pops up and says the connection to Gmail failed, I'm connected to the net, and I can login to my Gmail account normally, so why?
Are you using a proxy? The Notifier does not have proxy support.

---

### Post by gpap1266 on 2007-08-09
Thank's for the help..;-)
a i see i have to wait for the new version of gmail... (for proxy support) :(

---

### Post by dougfractal on 2007-08-09
iGoogle personalized google home page may provide all that you want.

[www.google.com/ig](www.google.com/ig)
[http://www.google.co.uk/ig/directory?root=%2Fig&dpos=top&num=24&url=http://www.google.com/ig/modules/builtin_gmail.xml](http://www.google.co.uk/ig/directory?root=%2Fig&dpos=top&num=24&url=http://www.google.com/ig/modules/builtin_gmail.xml)

---

