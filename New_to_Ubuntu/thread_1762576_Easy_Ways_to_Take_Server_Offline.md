---
title: "Easy Ways to Take Server Offline?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Arwen17evenstar on 2011-05-19
I know the easiest way would be to simply unplug the ethernet cord. But sometimes I'm not physically near enough to do this. I want to be able to take my server offline for when I'm doing updates or general work on it. Some of the stuff I do would reveal critical information to the internet if it stays online.
Right now I'm always closing the port in apache2 and shorewall in order to cut it off from the internet. Is there a simpler way to make the server offline so I'm not always going into the config files? What are my options?

---

### Post by mcduck on 2011-05-19
```
sudo /etc/init.d/apache2 stop
```

..and to start it again:

```
sudo /etc/init.d/apache2 start
```

---

### Post by Arwen17evenstar on 2011-05-19
but see apache has to be running if I'm going to work on it. I'm just trying to cut off external access while I work on it.

---

### Post by compmodder26 on 2011-05-19
You can create a script that will reload shorewall with apache's port closed, and another script that will reload shorewall with apache's port open.  Then just run the close script when doing maintenance and run the open script when done.

---

### Post by HermanAB on 2011-05-19
sudo ifconfig eth0 down
sudo ifconfig eth0 up

---

### Post by compmodder26 on 2011-05-19
> **HermanAB said:**
> sudo ifconfig eth0 down
sudo ifconfig eth0 up

Not if the OP is doing this remotely.

> I know the easiest way would be to simply unplug the ethernet cord. But sometimes I'm not physically near enough to do this.

Eh, you may be right though.  Arwen17evenstar, please clarify if you are actually working on the server locally or doing it remotely through SSH, etc?

---

### Post by doas777 on 2011-05-19
> **compmodder26 said:**
> Not if the OP is doing this remotely.
from where, the next room? it doesn't add up that he can block http in, without impacting his administrative session, but that apache must be running for administration, unless the op is on the lan.

---

### Post by compmodder26 on 2011-05-19
> **doas777 said:**
> unless the op is on the lan.

Bingo.  Remotely doesn't have to mean from the internet.

Nevertheless, we need more info to get the OP's true intent.

---

### Post by crispy_420 on 2011-05-19
ssh in and disable the service (http, ftp, etc.)

do maintenance

ssh in a restart service disabled earlier

Everybody assuming web server, is that correct?

---

### Post by doas777 on 2011-05-19
> **crispy_420 said:**
> ssh in and disable the service (http, ftp, etc.)

do maintenance

ssh in a restart service disabled earlier

Everybody assuming web server, is that correct?
that would seem to be the belief, but the op has also implied that the apache service is required for his admin work (webmin perhaps?) so the apache must remain up, and only respond to queries from inside during the maintenance.

I can think of numerous ways to do it, but none are easier than altering the firewall rules as the op already suggests they do.

---

### Post by Arwen17evenstar on 2011-05-19
I'm inside the lan when I'm doing the work. It's look like altering the config files is the best way to do it. One of the posts above mentions writing a script that can do this automatically. How do I write this? A webpage I can read or something I can google would be a great start.

---

### Post by compmodder26 on 2011-05-19
I'm not familiar with using shorewall, so I don't know the exact steps you need to take.  But I imagine that it uses a file that specifies what ports to open, correct?  Well you could produce two separate files.  One that has the port open to the internet, and another that does not.  Then if you can restart/reload shorewall and specify which file it should read from, assuming it can do that.  Then you could use two commands (note these are just pseudo-commands, you'll need to work out the exact syntax you need yourself):

First command to open the port:
```
sudo shorewall --reload --file=/path/to/openport.conf
```

Second command to close the port:
```
sudo shorewall --reload --file=/path/to/closedport.conf
```

---

