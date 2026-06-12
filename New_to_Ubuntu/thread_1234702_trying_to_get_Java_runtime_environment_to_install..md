---
title: "trying to get Java runtime environment to install."
date: 2009-08-08
forum: New to Ubuntu
---

### Post by jonathanfrost on 2009-08-08
I need help trying to get it installed. Ive downloaded the installer but it wont activate. it has a .bin ending on it and archive manager wont recognize it. please help. message me on [email]gokou2231@hotmail.com[/email] or squall_leonhart_gunblade_use12

---

### Post by arochester on 2009-08-08
Just install ubuntu-restricted-extras. It will install several useful programs. JRE is one of them.

Connect to the Internet, open a terminal and issue the command: > sudo apt-get install ubuntu-restricted-extras

---

### Post by lykeion on 2009-08-08
ubuntu-restricted-extras do contain the package sun-java6-jre but if you don't need all the other packages in there, it's simpler just to:

1. Enable the multiverse repository in System > Administration > Software Sources

2. Install the package **sun-java6-jre** with System > Administration > Synaptic Packakage Manager

You might also be interested in the packages **sun-java6-plugin** and **sun-java6-fonts**

To check that installation went okay, launch a terminal (Applications > Accessories > Terminal) and enter "**java -version**" (without quotes). It should produce something like: java version "1.6.0_14"

Some help pages:
[LIST]
[*][Repositories in Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[*][Installing software]("https://help.ubuntu.com/community/InstallingSoftware")
[*][Using the terminal]("https://help.ubuntu.com/community/UsingTheTerminal")
[/LIST]

---

### Post by credobyte on 2009-08-08
In terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

