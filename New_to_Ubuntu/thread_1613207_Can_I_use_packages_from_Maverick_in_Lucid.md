---
title: "Can I use packages from Maverick in Lucid?"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by loldrup on 2010-11-04
Hi

I have a Vaio X with Lucid, and no real hope for upgrading to 10.10 ([tried that]("http://ubuntuforums.org/showthread.php?t=1608589")).

I would like to get access to some of the packages from Maverick:
updated Ubuntu One client
updated Software Center
updated python (2.6.6)
netbeans

What would happen if I changed all occurrences of the word lucid to maverick in the /etc/apt/sources.list and then did

sudo apt-get install <package name>

for each package?


If that is not a clever strategy, what else could I try?


Oh, one more thing: is there a best practice for how to find out what package name a given application has?

---

### Post by Cheesehead on 2010-11-04
It's not a clever strategy. It has a significant risk of damaging your system.

Updated package foo may depend on updated packages foolib1, foolib2, foolib3, otherapp1, otherapp2, otherapp3...and before you know it you are trying to pull in whatever borked your upgrade, or youe have intordiced so many version-based incompatibilities that your system becomes unstable.

Under a Ubuntu system (meaning you're not willing to build from source and trace dependencies manually) , you have two realistic options:

1) Wait for the bugs that stymied your upgrade to be fixed.

2) Wait for updates to appear in 10.04.1 backports.

---

### Post by loldrup on 2010-11-04
> **Cheesehead said:**
> It's not a clever strategy. It has a significant risk of damaging your system.

Updated package foo may depend on updated packages foolib1, foolib2, foolib3, otherapp1, otherapp2, otherapp3...and before you know it you are trying to pull in whatever borked your upgrade, or youe have intordiced so many version-based incompatibilities that your system becomes unstable.

Under a Ubuntu system (meaning you're not willing to build from source and trace dependencies manually) , you have two realistic options:

1) Wait for the bugs that stymied your upgrade to be fixed.

2) Wait for updates to appear in 10.04.1 backports.

:(

hm

Is there a mailing list or other announcement system where I can follow what things appear in 10.04.1 as backports?

How do I know whether I have 10.04.1 or just 10.04 ?

---

### Post by howefield on 2010-11-04
> **loldrup said:**
> Is there a mailing list or other announcement system where I can follow what things appear in 10.04.1 as backports?

Read this, might give you a start.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)


> How do I know whether I have 10.04.1 or just 10.04 ?

Try

```
lsb_release -a
```

in a terminal.

---

### Post by X-Tarzan on 2010-11-04
i follow this instructions and 
[http://www.webupd8.org/2010/05/how-to-upgrade-to-ubuntu-1010-maverick.html](http://www.webupd8.org/2010/05/how-to-upgrade-to-ubuntu-1010-maverick.html)

and dang its maverick

---

### Post by kimberlite on 2010-11-04
You can install python 2.6 from the source. However you should take care to separate from your system wide python install. I am just learning python, but as far as I know, there are tools to achive this. Cf. virtualenv at [http://pypi.python.org/pypi/virtualenv](http://pypi.python.org/pypi/virtualenv) .

---

