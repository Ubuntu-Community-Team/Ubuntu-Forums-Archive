---
title: "Internet speed test"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Unborn on 2009-07-04
I need a little help, i have ssh acces to a server and i want to determine it's upload transfer rate. I am not sure whats the os redhat or centos :D - i'm newb to linux.

```
cat /proc/version
Linux version 2.6.18-92.el5 (mockbuild@builder10.centos.org) (gcc version 4.1.2 20071124 (Red Hat 4.1.2-42)) #1 SMP Tue Jun 10 18:51:06 EDT 2008

```I tried some test but i didnt find a website for upload to run it in terminal
ex: links [www.speedtest.net]("http://www.speedtest.net")

so is there another way to determine the upload transfer rate?
for download i tested with wget [http://www.site.com/file.exe](http://www.site.com/file.exe)

Please help :lolflag:

---

### Post by jenkinbr on 2009-07-04
Well I can tell you that your remote server is CentOS (which is a derivitive of Red Hat, and uses the Red Hat repositories.  As far as speed goes, I'm not sure...

---

### Post by SlugSlug on 2009-09-10
> **Unborn said:**
> I need a little help, i have ssh acces to a server and i want to determine it's upload transfer rate. I am not sure whats the os redhat or centos :D - i'm newb to linux.

```
cat /proc/version
Linux version 2.6.18-92.el5 (mockbuild@builder10.centos.org) (gcc version 4.1.2 20071124 (Red Hat 4.1.2-42)) #1 SMP Tue Jun 10 18:51:06 EDT 2008

```I tried some test but i didnt find a website for upload to run it in terminal
ex: links [www.speedtest.net]("http://www.speedtest.net")

so is there another way to determine the upload transfer rate?
for download i tested with wget [http://www.site.com/file.exe](http://www.site.com/file.exe)

Please help :lolflag:


are you accessing server via ssh oer the internet? if so the use scp and send a file from server to you eg

scp /home/user/test-file user@homeserver:/home/user/

---

