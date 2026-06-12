---
title: "Update manager,karmic 64 bit"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by vk7aaa on 2010-04-13
update manager starts with following message:


Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 49 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
Can anyone offer advice how to fix above problem?

---

### Post by philinux on 2010-04-13
> **vk7aaa said:**
> update manager starts with following message:


Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 49 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
Can anyone offer advice how to fix above problem?

Yes your sources list has an error in it. Open a terminal.

```
gksu [COLOR="Red"]gedit[/COLOR] /etc/apt/sources.list
```

Look at line 49 correct the error and save the file.

Then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by vk7aaa on 2010-04-13
can't open list
Display in terminal
andrew@andrew-desktop:~$ gksu /etc/apt/sources.list
andrew@andrew-desktop:~$

---

### Post by philinux on 2010-04-13
> **vk7aaa said:**
> can't open list
Display in terminal
andrew@andrew-desktop:~$ gksu /etc/apt/sources.list
andrew@andrew-desktop:~$

Finger trouble should be gksu gedit /etc/apt/sources.list

It helps if you turn on line numbering via gedit's preferences.

---

### Post by vk7aaa on 2010-04-13
Hi Phill
line 49 reads "deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) karmic-security universe"
Don't know how to fix it!
Regards Andrew

---

### Post by vk7aaa on 2010-04-13
sudo apt-get install bisigi-themes
 Could you show me the way please?
Andrew

---

### Post by philinux on 2010-04-13
Lets have a look at the whole thing.

```
cat /etc/apt/sources.list
```

Post back the result. Please wrap it with code tags.

---

### Post by vk7aaa on 2010-04-13
andrew@andrew-desktop:~$

---

### Post by philinux on 2010-04-13
You need to gedit this file and remove this.

sudo apt-get install bisigi-themes


```
gksu gedit /etc/apt/sources.list
```

---

### Post by vk7aaa on 2010-04-13
Thanks a lot for you help phil!
You have solved my problem
kind regards andrew

---

### Post by Arand on 2010-04-13
You also should replace the line:> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-freedeb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic maindeb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic mainWith```
deb http://packages.medibuntu.org/ karmic free non-free
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
```- Arand

---

