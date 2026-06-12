---
title: "ISA Proxy will Ubuntu"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by soan on 2008-10-31
Hi 

I was having some trouble getting apt to work with the ISA proxy here at work. After some looking around I found CNTLM. It allows you to use an ISA proxy and get passed all the problems of having special characters in your password.

[http://cntlm.wiki.sourceforge.net/](http://cntlm.wiki.sourceforge.net/)

After download and installing the .deb all you need to do is edit the /etc/cntlm.conf file and then start cntlm with the command:

sudo /etc/init.d/cntlm start

Now I config my proxy to localhost:3128 and happy days :) apt works like a charm through the ISA proxy.

---

### Post by mjh007 on 2008-11-26
Hi All

I am using cntlm as a way of dealing with an ISA proxy at university. Unfortunately I can't seem to get it to start automatically when I start ubuntu. I have to manually type in sudo /etc/init.d/cntlm restart in the terminal every time.

I think it has something to do with permissions. Any ideas?

Thanks in advance

---

### Post by parktownprawn on 2009-01-14
what is the output of the following

```
grep cntlm /var/log/syslog
```

before you type

```
sudo /etc/init.d/cntlm restart
```

I had the same problem until I entered the IP address of the proxy rather than just its name in the file /etc/cntlm.conf

---

### Post by timur_ba on 2011-05-06
The same problem is also here: 
[http://ubuntuforums.org/showthread.php?t=1020784](http://ubuntuforums.org/showthread.php?t=1020784)
[http://ubuntuforums.org/showthread.php?t=964746](http://ubuntuforums.org/showthread.php?t=964746)
[http://ubuntuforums.org/showthread.php?t=1285745](http://ubuntuforums.org/showthread.php?t=1285745)
[http://ubuntuforums.org/showthread.php?t=1396749](http://ubuntuforums.org/showthread.php?t=1396749)
[http://ubuntuforums.org/showthread.php?p=10777002](http://ubuntuforums.org/showthread.php?p=10777002)

I opened a bug for this:
[https://bugs.launchpad.net/ubuntu/+bug/724849](https://bugs.launchpad.net/ubuntu/+bug/724849)

---

