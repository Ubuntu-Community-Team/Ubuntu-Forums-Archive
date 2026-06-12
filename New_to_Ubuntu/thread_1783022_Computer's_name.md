---
title: "Computer's name"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-06-15
I've just upgraded from Karmic to Natty.   Looks very nice,   but it's going to take me a while to find where everything is!

During the upgrade installation I was asked what computer name I wanted to use,  and I chose one that I now realise,  having seen how it appears on a terminal home prompt,   is inconveniently long. I should have chosen a much shorter name. :redface:

I'm wondering if there's any way I can now edit this name without having to start the installation all over again from scratch.

---

### Post by hakermania on 2011-06-15
```
sudo gedit /etc/hostname
```
place your preferable name, save, restart terminal

---

### Post by Jacobonbuntu on 2011-06-15
....you can also edit the name (and a lot more) in Ubuntu Tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by kimda on 2011-06-15
Or use the following command: 

```
sudo hostname mynewhostname
```

---

### Post by Sleepy-zz-John on 2011-06-15
> **hakermania said:**
> ```
sudo gedit /etc/hostname
```
place your preferable name, save, restart terminal

Thanks!   That worked and was a lot easier than I'd imagined.   Needed a complete Natty restart though,  not just a terminal restart.

---

### Post by Sleepy-zz-John on 2011-06-16
Looks like I spoke too soon!!   

My new hostname shows up OK in my /etc/hostname file,  and when I log-in at startup it shows correctly in my log-in window there too,   but now when I use sudo,  I get this:

```
john@jaspir:~$ cat /etc/hostname
jaspir
john@jaspir:~$ sudo chmod 755 /usr/bin/skype
sudo: unable to resolve host jaspir
[sudo] password for john: 
john@jaspir:~$ 

```
 
Is this perhaps an indication that I should have set permissions on /etc/hostname ?

---

### Post by Sleepy-zz-John on 2011-06-16
Solved it!  I checked in /etc/hosts and found my old hostname was still showing there against 127.0.1.1.

Corrected that with gksudo gedit /etc/hosts,  changed the entry against 127.0.1.1 to my new hostname,  saved hosts,  and I'm now back in business again! :D

---

