---
title: "Running Commands at Startup"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by nheather on 2009-03-26
I want to start some servers (Apache and mySQL) on login.

I can start them manually but have to do so using sudo.

Is there any way I can run this command automatically at login as if it is run as root without having to provide my password?

Cheers,

Nigel

---

### Post by sandyd on 2009-03-26
you can do
```

sudo visudo

```

then you can edit it to allow running sudo on programs without typing in a password



or add your commands to the /etc/rc.local file like this for example
```

bin/sh -c /path/to/app/

```

---

### Post by nheather on 2009-03-26
Excellent, they both worked.

Thanks very much,

Nigel

---

### Post by KIAaze on 2009-03-26
Why don't you simply start apache and mySQL like any other service/daemon?

It should be in administration->services or something like that.

Otherwise, you can use the /etc/init.d script system.
Here's some more info (too lazy to sort it all through for you now ^^):
[https://help.ubuntu.com/community/SysvconfigHowTo](https://help.ubuntu.com/community/SysvconfigHowTo)
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)
[http://luv.asn.au/overheads/linux-startup.html](http://luv.asn.au/overheads/linux-startup.html)

---

### Post by nheather on 2009-03-27
Apache and mySQL don't appear in my version Administration>Services

This is probably because I installed them together with PHP as a suite called xampp.

I have a single command ***/opt/lampp/lampp start*** which starts the lot.

I suspect it is starting them as applications rather than services.

Cheers,

Nigel

---

### Post by hyper_ch on 2009-03-27
daemons like apache and mysql will auto-start if installed through the repositories.

---

