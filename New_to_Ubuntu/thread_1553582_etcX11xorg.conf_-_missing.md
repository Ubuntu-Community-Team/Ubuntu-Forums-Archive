---
title: "/etc/X11/xorg.conf - missing?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by landog on 2010-08-15
Day One with Ubuntu.  Installed 64-bit Server 10.04 LTS on a Thinkpad W510.  One thing that I'd like to accomplish is to gain control over the display brightness.  Some threads that I have seen reference a file /etc/X11/xorg.conf.

I don't seem to have such a file.  Am I supposed to create it?

Thanks,
-dog

---

### Post by mhgsys on 2010-08-15
yes; xorg.conf in 10.04 is no longer the standard... you can generate one.. it will use it when it's there.


 here's how to do that;


```
Switch to a tty ( press ctrl+alt+f1 (f2,f3 etc)
```
login with your username and password.

stop gdm with
```
sudo service gdm stop
```

then generate a xorg.conf with 
```
sudo Xorg -configure
```

this will create a xorg.conf.new in your home directory)
move the auto-generated xorg.conf.new to /etc/X11/xorg.conf


```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

Make changes you want to try 
```
sudo nano /etc/X11/xorg.conf
```
and start gdm again with

```
sudo service gdm start
```

---

### Post by landog on 2010-08-15
Wow.  Thanks!

---

### Post by mhgsys on 2010-08-15
Your welcome

---

### Post by overdrank on 2012-12-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

