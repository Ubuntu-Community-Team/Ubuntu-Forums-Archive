---
title: "apt-get install"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by ljw5491 on 2011-02-27
I am having no luck at all adding packages to my ubuntu server.  I can update, so there is definitely connectivity - but whenever I type in a command, for instance:

```
sudo apt-get install vsftpd
```I get back:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package vsftpd
```Is there anyone who can get me on the right track with this?  I've been running ubuntu server 10.10 for about a month now and know just enough to be dangerous -   Thanks -

---

### Post by snowpine on 2011-02-27
You need to refresh your list of available packages with:

```
sudo apt-get update
```

then you can:

```
sudo apt-get install vsftpd
```

---

### Post by ljw5491 on 2011-02-27
Yeah, I can get the update just fine - but when I enter the second  command I get the result shown above.  Not sure why I'm having so much  trouble.  

Here is the contents of /etc/apt/sources.list:


```
#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ $

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ $

deb http://security.ubuntu.com/ubuntu maverick-security main
deb-src http://security.ubuntu.com/ubuntu maverick-security main
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```


Are these the correct repositories??

---

### Post by snowpine on 2011-02-27
It looks like you have only the "security" repo enabled. I think that vsftpd is in "main". I would also recommend enabling "updates".

You may find this sources.list generator helpful: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Sef on 2011-02-27
> It looks like you have only the "security" repo enabled. 

If that is all that the OP has, then some repositories are missing.

---

### Post by ljw5491 on 2011-02-28
Worked like a charm - many thanks!

---

