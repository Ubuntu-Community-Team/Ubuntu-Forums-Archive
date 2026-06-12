---
title: "I broke my apache somehow..."
date: 2010-05-30
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-30
I setup apache on a computer I have at home to host a little website.  I just checked on it and noticed that I couldn't access it anymore, not even from the server itself if I type "localhost:81" into the address bar in Firefox.

I did a little digging and decided to try invoking "/etc/init.d/apache2 start" in a terminal window.  This was the output I got:

```
/etc/init.d$ ./apache2 start
 * Starting web server apache2                                                  [Sun May 30 21:19:58 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```

Not sure what to do.  It's been so long since I set this up...

---

### Post by luisb on 2010-05-30
You get that "permisson denied" message because you're not running the command as root.

Try
```
sudo /etc/init.d/apache2 start
```

and then check [http://localhost/](http://localhost/) in your browser.

---

### Post by diablo75 on 2010-05-30
I did what you suggested.  Starting Apache with sudo outputs the following (similar to the output above, but a little shorter):

```
* Starting web server apache2                                                  [Sun May 30 21:41:26 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
httpd (pid 2538) already running
                                                                         [ OK ]

```

So it would appear it's running... but with the default settings, I guess.

My webpage is locally stored in /var/www and when I set it up originally I told it to use port 81 instead of 80 because my ISP blocks 80.  Worked just fine.

If I type "localhost:81" into firefox, I get:

> Unable to connect
Firefox can't establish a connection to the server at localhost:81.

And if I take the 81 off and just go with "localhost", I get a 404 error:

> Not Found

The requested URL / was not found on this server.
Apache/2.2.14 (Ubuntu) Server at localhost Port 80

So it would appear that I have to tell apache where my site is located locally, and that it needs to serve it out on port 81.  How do I do this?

Also... has anyone else had this kind of thing happen after a distro upgrade on Ubuntu?

---

