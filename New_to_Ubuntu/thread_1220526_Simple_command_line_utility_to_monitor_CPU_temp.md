---
title: "Simple command line utility to monitor CPU temp"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-07-22
Hi!

I have been looking around for a command line utility that will monitor my CPU temp.  I have read some man pages and websites, but I can't seem to find anything.  Has anyone ever seen anything like this?

Thanks in advance!

---

### Post by Durden on 2009-07-22
[http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/](http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/)

Give that a shot

---

### Post by ecmatter on 2009-07-22
```

sudo apt-get sensors-applet
sudo apt-get lm-sensors

```

and then at the command line run:

```

sensors-detect

```

---

### Post by MontelEdwards on 2009-07-22
On my EEE,
all that sensors stuff dont work.

I just ACPI

just apt-get install acpi
then acpi -t

---

### Post by pi.boy.travis on 2009-07-23
> **Durden said:**
> [http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/](http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/)

Give that a shot


Awesome!  Thanks!

---

