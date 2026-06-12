---
title: "Sudo apt-get remove... Oooppsss"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by iamjfarrell on 2009-09-27
I did sudo apt-get remove and I did a bunch of compiz related items but for some reason it went overboard and removed much more than just compiz. It basically removed just about everything. Now when I go to ubuntu it is on the basic black screen and that is how I log in. Even if I do it in safe mode. What are my options? Am I screwed?

---

### Post by aysiu on 2009-09-27
Just type in ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
``` and you should be good.

More details here:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by iamjfarrell on 2009-09-28
> **aysiu said:**
> Just type in ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
``` and you should be good.

More details here:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

I did the apt-get update and nothing happened. It ran into some error. Do I need to be physically connected to the internet or is wireless ok? I will do all the above code though and see what happens.

---

### Post by kevdog on 2009-09-28
you need a working internet connection.

---

### Post by Amstell on 2009-09-28
>  It ran into some error

What was the error?  

You do need a working internet connect but as long as its wireless you should be fine.

---

### Post by marshmallow1304 on 2009-09-28
If there's no window manager running, wireless won't connect automatically AFAIK.  If possible, use a wired connection.

---

### Post by prshah on 2009-09-28
> **iamjfarrell said:**
> Do I need to be physically connected to the internet or is wireless ok?

Physical connection is better in this case if it is convenient.

Otherwise, post back the type of security you are using (None, WEP, WPA) for a commandline guide to connect.

---

### Post by iamjfarrell on 2009-09-28
I got a physical connection and I am all good now. back to normal. I don't know what I did. Thanks to everyone!

---

### Post by MAFoElffen on 2013-02-23
Bigger ooppss. Old thread and it will not let me delete my on post (this one) on it.

---

### Post by Sef on 2013-02-24
Locked to prevent someone else from posting even by accident.

---

