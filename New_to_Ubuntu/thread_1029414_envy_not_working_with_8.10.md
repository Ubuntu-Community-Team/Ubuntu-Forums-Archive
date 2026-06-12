---
title: "envy not working with 8.10"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nubix on 2009-01-03
hi ubuntu.org i was trying to install the driver for my 8600 with this guide

[http://ubuntuforums.org/archive/index.php/t-482096.html](http://ubuntuforums.org/archive/index.php/t-482096.html)

i finally get all the commands executed i go to install the driver and, envy apparently doesn't support my operating system. please help! thank you in advance.

---

### Post by Cl0ud9 on 2009-01-03
Could you be a little more descriptive. What commands did you execute and what error messages did you get? Perhaps you are using envy and not envyng. If this is the case remove envy and then install envyng.

```

sudo apt-get install envyng-core

```

---

### Post by nubix on 2009-01-03
sudo /etc/init.d/gdm stop
wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu3_all.deb)
sudo dpkg -i envy*.deb
sudo envy -t
those are the commands ive used

so i installed envyng, now what do i do?

---

### Post by nubix on 2009-01-03
nevermind i installed it and got the envyng program running using -t command, and i installed the latest one. its working now! anything else i should know? how to configure(tweak my settings?

---

### Post by Cl0ud9 on 2009-01-03
You should be good to go, although you can install a GUI for envyng.

For GNOME:
```

sudo apt-get install envyng-gtk

```

For KDE:
```

sudo apt-get install envyng-qt

```

---

### Post by nubix on 2009-01-03
to install new drivers when they become available, or is there more to it than that?

---

### Post by Cl0ud9 on 2009-01-03
After every kernel update you have to reinstall the driver. I have never paid any attention to installing new drivers as they were released, so I'm not sure about that.

---

### Post by nubix on 2009-01-03
well thank you!
just one more thing, how do i access the gui envy?

---

### Post by Cl0ud9 on 2009-01-03
```

envyng -g

```
or
```

envyng -k

```

You can also add to your applications menu by right clicking and selecting "Edit Menus".

---

### Post by nubix on 2009-01-03
it says: error make sure it is installed first

---

### Post by Cl0ud9 on 2009-01-03
> **nubix said:**
> it says: error make sure it is installed first

> **Cl0ud9 said:**
> You should be good to go, although you can install a GUI for envyng.

For GNOME:
```

sudo apt-get install envyng-gtk

```

For KDE:
```

sudo apt-get install envyng-qt

```

If you are using GNOME then
```

envyng -g

```

If you are using KDE then
```

envyng -k

```

---

### Post by nubix on 2009-01-03
ERROR: Make sure that envyng-qt is installed

i am using the gnome command, i am running gnome.

---

### Post by smooth3006 on 2009-01-03
i  installed envy and it won't show in my menu at all ? where is the gui interface ?

---

### Post by nubix on 2009-01-03
open it up in the command prompt ctrl alt f1

envyng -t

that runs it 

hope that helps

---

### Post by Cl0ud9 on 2009-01-03
> **nubix said:**
> ERROR: Make sure that envyng-qt is installed

i am using the gnome command, i am running gnome.

If you ran 
```

envyng -g

```
then I don't know what is going on here.

Check the man page, although it doesn't give much information.
```

man envyng

```

---

### Post by Cl0ud9 on 2009-01-03
> **smooth3006 said:**
> i  installed envy and it won't show in my menu at all ? where is the gui interface ?

First install the GUI, then use the appropiate commands to run the GUI.

> **Cl0ud9 said:**
> If you are using GNOME then
```

envyng -g

```

If you are using KDE then
```

envyng -k

```

You can add envyng to your application menu by right clicking on the applications menu and selecting "Edit Menus".

---

