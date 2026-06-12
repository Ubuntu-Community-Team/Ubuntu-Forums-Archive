---
title: "Log of installed updates"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by vaughany on 2009-07-24
Hi all. Short version:

Is there a way of finding out what updates have been installed to my computer and on what dates?

Long version: 

Thursday last week my Ubuntu Jaunty laptop did an update. I don't know what was updated, only that it updated.

Friday morning, when I start up the laptop for the day, I cannot connect to the internet. Firefox/Opera won't connect, Pidgin is dead in the water, twetdeck utterly blank and so on.

I have always had a direct connection to the Internet, no proxy settings required, but now I find I have had to add in proxy settings to connect Firefox et al to the internet. I am reasonably certain that whatever updated the previous day caused this issue.

A little background: most staff where I work have to use the proxy server to get external access, however due to my elevated status I have been assured that I have a hole in the firewall and that I definitely have complete access through it... (It's the only thing I can't check myself so I have to believe them.)

Any and all halp always appreciated. :)

---

### Post by neu2buntu on 2009-07-24
yes.. goto > system > administration > synaptic package manager > file > history > then your date

---

### Post by Greenwidth on 2009-07-24
In Synaptic:
File > History

---

### Post by vaughany on 2009-07-24
I'm actually quite embarrassed I didn't spot that myself! Thanks both of you. :)

---

### Post by PGScooter on 2009-07-24
how can one do this from the commandline?

---

### Post by philinux on 2009-07-24
> **PGScooter said:**
> how can one do this from the commandline?

```
cat /var/log/dpkg.log
```

---

### Post by PGScooter on 2009-07-24
> **philinux said:**
> ```
cat /var/log/dpkg.log
```

great, thanks!

For archive purposes, please note that dpkg.log only contains the info from the last month or so. To get all months, you must also search in the other files in that folder with title such as dpkg.log.3.tar.gz

---

