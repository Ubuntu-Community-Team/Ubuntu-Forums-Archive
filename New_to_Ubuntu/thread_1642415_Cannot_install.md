---
title: "Cannot install"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by kiniyaloca1 on 2010-12-10
I am not able to install via the Ubuntu Software Center on 10.10. It gives me the error message, "There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry."
I am running amd64 on a partitioned hardrive dual booting Ubuntu 10.10 and windows7. Also I am pretty new to linux, so very descriptive please :)

---

### Post by Perfect Storm on 2010-12-10
Close Softwarecenter. Open the terminal and type;
```
sudo apt-get update && sudo apt-get upgrade
```

See if it helps, if not please post the terminal output.

---

### Post by kiniyaloca1 on 2010-12-10
That worked out great. After I did what you said I had to do something called a partial install, and then it updated everything.
Thanks so much :)

---

### Post by amjjawad on 2010-12-10
> **kiniyaloca1 said:**
> That worked out great. After I did what you said I had to do something called a partial install, and then it updated everything.
Thanks so much :)

If you sorted it out and have no more questions, please mark this thread as SOLVED for future reference by others :)

And well done :)

---

