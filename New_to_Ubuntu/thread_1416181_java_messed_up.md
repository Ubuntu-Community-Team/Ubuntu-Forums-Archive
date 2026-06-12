---
title: "java messed up"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by patchido on 2010-02-25
while trying to install a thing called lejos i managed to do something im not sure what it is, i have java sun 1.6 installed but for some reason the one being used is gnu java 1.5, and i dont know why or how to revert it as it was before.

here is what i mean:

```
pato@pato-laptop:~$ mercury
Mercury does not run on GNU Java.
Please, make sure to have the Sun Java version 1.5 or later installed.

``````
pato@pato-laptop:~$ sudo apt-get install sun-java6-jdk
[sudo] password for pato: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  libusb-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

``````
pato@pato-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
pato@pato-laptop:~$ 

```

---

### Post by r-senior on 2010-02-25
You just need to set the Sun Java as the default. Check your default first with:

$ sudo update-java-alternatives -l

Then this should set Java 6 as the default.

$ sudo update-java-alternatives -s java-6-sun

---

### Post by patchido on 2010-02-25
thx! that was excatly what i needed :) how can i learn stuff like that?

---

### Post by r-senior on 2010-02-26
The easy answer would be that it's in the documentation:

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

But sometimes you need to know what you are looking for before you find it, which is where the forum helps. ;) Searching the web for "ubuntu java" would have taken you to the above page.

---

