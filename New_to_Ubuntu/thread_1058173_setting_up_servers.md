---
title: "setting up servers"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by windows hater on 2009-02-02
hello im looking into setting up a dhcp and later a web sever i been looking around and i have been using ubuntu for awhile now and does ubuntu have tools to make it happen or do i have to sadly pick a different distro 

thanks

---

### Post by theozzlives on 2009-02-02
You can use your router as a DHCP server, but you can also use Ubuntu if you want. Apache comes in the repos for your web server.

---

### Post by RuleMaker on 2009-02-02
It's not depending on distro...

Just run these lines in terminal one-by-one:
```
sudo apt-get update
```
```
sudo apt-get install tasksel
```
```
sudo tasksel
```

---

### Post by windows hater on 2009-02-02
well i know i can set my router to dhcp but i want to just run a strict dhcp and maybe a webserver but my question is there a distro that is made strict for this or does it really matter or is there one easier to learn then the other i been looking at open suse and redhat  

sorry if i worded my question wrong

---

### Post by perlluver on 2009-02-02
> **windows hater said:**
> well i know i can set my router to dhcp but i want to just run a strict dhcp and maybe a webserver but my question is there a distro that is made strict for this or does it really matter or is there one easier to learn then the other i been looking at open suse and redhat  

sorry if i worded my question wrong

If you already know a little about Ubuntu, it will work well as a Web Server, and DHCP server.  I am currently using it for a file/web/squid proxy cache server.  No problems with it, and it is headless, so I ssh into it.

---

### Post by windows hater on 2009-02-02
ok thank you  because i was hearing some distros where better then others coming from the server side so i was just wondering how good it is

---

### Post by HermanAB on 2009-02-02
The Ubuntu Server Version has a wizard for Apache.

If however, you want wizards for everything and the kitchen sink and want to forego the command line completely, then you need to use Suse or Mandriva.

Cheers,

Herman

---

