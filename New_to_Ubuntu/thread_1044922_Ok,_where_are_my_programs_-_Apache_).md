---
title: "Ok, where are my programs - Apache :)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Alexander Barnes on 2009-01-19
Hi, I apologize for such a crazy question.

I'm starting a class and our prof is getting us working with Apache on *nix.  I used my Ubuntu synaptic manager to download Apache and it reported a successful installation...but how to find it?  I'm surprised I can't find many programs in the menus at the top (applications, places, system).  Maybe I don't understand Apache, but what should I be looking for?

Thanks in advance,
Alex

Ubuntu Hardy Heron 8.04 32-bit with Gnome desktop manager.

---

### Post by dnRoyston on 2009-01-19
Apache WWW files are stored at /var/www/

I believe Apache files are located at /etc/apache2/ , it's been a while since I've used it. Apache is a server, and a daemon, not an application.

---

### Post by mrbiggbrain on 2009-01-19
you likely will have to run apache from the shell... i would guess

---

### Post by iaculallad on 2009-01-19
> **mrbiggbrain said:**
> you likely will have to run apache from the shell... i would guess

And that would be:

To Start:

```
sudo /etc/init.d/apache2 start
```

To Stop:

```
sudo /etc/init.d/apache2 stop
```

To Restart:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by dnRoyston on 2009-01-19
oh, and apache should start up automatically. For example, if you go to firefox and enter "127.0.0.1" (no quotes), you should get a message saying "It works!". If it doesn't, go to terminal and type:

sudo /etc/init.d/apache2 start

EDIT: oop, iaculallad beat me to it

---

### Post by Alexander Barnes on 2009-01-19
Thanks everyone!  Awesome. I found the files and yes..."It works!" :-)

Great help.

---

