---
title: "help with tftp"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by henryjm206 on 2008-10-19
hi,

I followed this guide

([http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)) 

and it does this 
```
 * Starting internet superserver xinetd                                  [fail] 

```
when I run this command,
```
sudo /etc/init.d/xinetd start

```
 any ideas on why it won't work?

Thanks

henry

---

### Post by henryjm206 on 2008-10-26
bump

---

### Post by Xama on 2008-12-04
BUMP!

How do you get tftp working in Ubuntu ... please someone answer this ... with working non-complicated straightforward directions ... the old link posted above now seems to not work (it once worked on the older Ubuntus).

---

### Post by superprash2003 on 2008-12-04
ensure that you have followed step 2 and step 3 of that guide properly.. it could be that

---

### Post by Xama on 2008-12-04
My tftp requests (get and put) were very slow. 

I know it is tied to my /etc/host.conf and /etc/hosts file configuration. For one I added the client machines to the hosts file and this sped things up ... everything seems fine. 

I assume that reverse-dns is the culprit and the fact that 127.0.1.1 points to my machine name ... (which I never liked and off topically I think is a weirdness). 

I want tftp to work right without me hacking the /etc/hosts file

Helpful things
* I found that I needed to tabify the xinetd.d/tftp file properly and remove the server args on tftp

* Doing a tail -f /var/log/syslog while doing the tftp requests allowed me to log what was going on ...

---

### Post by virgoptrex on 2009-09-03
> **henryjm206 said:**
> hi,

I followed this guide

([http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)) 

and it does this 
```
 * Starting internet superserver xinetd                                  [fail] 

```
when I run this command,
```
sudo /etc/init.d/xinetd start

```
 any ideas on why it won't work?

Thanks

henry

Use

```
sudo /etc/init.d/xinetd restart

```

and it should work. It has to recognize the configuration.hope it helps!

---

