---
title: "How to install im sensors"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by QazLeo on 2010-02-14
i dont understand their installation instruction.
i extracted the .tar.bz2 file.but wat to do next?

---

### Post by SuperSonic4 on 2010-02-14
*im sensors* or *lm sensors*? A google search for the former yields the latter.

lm_sensors is in the repositories so you can use synaptic to find it



To answer the question I suspect you'd do ```
cd lm_sensors-3.1.2
make all
sudo make install
```

this is explained in the INSTALL file in the folder you extracted

---

### Post by QazLeo on 2010-02-14
I typed wrongly.lm sensors.But show me step by step how to install?

---

### Post by QazLeo on 2010-02-14
It says

Makefile:175: lib/data.ld: No such file or directory
Makefile:175: lib/general.ld: No such file or directory
Makefile:175: lib/error.ld: No such file or directory
Makefile:175: lib/access.ld: No such file or directory
Makefile:175: lib/init.ld: No such file or directory
Makefile:175: lib/sysfs.ld: No such file or directory
Makefile:175: lib/conf-parse.ld: No such file or directory
Makefile:175: lib/conf-lex.ld: No such file or directory
Makefile:175: lib/data.ad: No such file or directory
Makefile:175: lib/general.ad: No such file or directory
Makefile:175: lib/error.ad: No such file or directory
Makefile:175: lib/access.ad: No such file or directory
Makefile:175: lib/init.ad: No such file or directory
Makefile:175: lib/sysfs.ad: No such file or directory
Makefile:175: lib/conf-parse.ad: No such file or directory
Makefile:175: lib/conf-lex.ad: No such file or directory
bison -p sensors_yy -d lib/conf-parse.y -o lib/conf-parse.c
make: bison: Command not found
make: *** [lib/conf-parse.c] Error 127

when i enter sudo make install

---

### Post by SuperSonic4 on 2010-02-14
Do you have build-essential installed? As the name suggests it's essential for compiling

```
sudo apt-get install build-essential
```

The instructions in my previous post work for me.

Just out of interest what is the output of ```
echo $PATH
```

---

### Post by wojox on 2010-02-14
You could also just download it from the repo's:

```
sudo apt-get install lm-sensors sensors-applet
```

```
sudo sensors-detect
```

---

### Post by nick_goodfate on 2010-02-14
step 1 : System->Administration->Synaptic package manager
stem 2 : in the search field type lm sensors
step 3 : click the box next to lm-sensors, in the list of results, and mark for      installation. a new window will pop up that tells you you need some extra packages .  click on "mark" button.
step 4 : click "apply" button . you re done .

---

### Post by QazLeo on 2010-02-14
Ok ,i used nick_goodfate's method.the package manager says its installed, but where can i find it?

---

### Post by nick_goodfate on 2010-02-14
i installed it too and i cant find it ether ... help !:P

---

### Post by lovinglinux on 2010-02-14
> **QazLeo said:**
> Ok ,i used nick_goodfate's method.the package manager says its installed, but where can i find it?

It's a command-line application. Open a terminal and type *sensors*. It will display the results. You can also add a panel item that will use sensors to display the information graphically. I don't remember it's name, because I'm using KDE. Anyway, several applications use sensors as backend. For example the screenlets monitors.

---

### Post by SuperSonic4 on 2010-02-14
> **lovinglinux said:**
> It's a command-line application. Open a terminal and type *sensors*. It will display the results. You can also add a panel item that will use sensors to display the information graphically. I don't remember it's name, because I'm using KDE. Anyway, several applications use sensors as backend. For example the screenlets monitors.

First you will have to run ```
sudo sensors-detect
``` and setup the config file via the on-screen prompts.

After that running *sensors* works.


If you're [OP] interested in the temperature of your hard drive(s) then you can also grab hddtemp from Synaptic or by pasting ```
sudo apt-get install hddtemp
``` into a terminal. You can then run it with ```
sudo hddtemp /dev/sda /dev/sdb
``` etc

---

