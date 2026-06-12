---
title: "Java in ubuntu"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by cookie101 on 2009-02-24
hi all, Im a newbie to linux and trying to get a java program working in ubuntu. The commands I used in windows are:

set path= <... SET THE PATH TO THE BIN OF YOUR JDK ...>

set classpath=./classes/;./lib/jdom.jar;%classpath%

java aminePlatform/guis/aminePlatformGUI/AminePlatformGUI

So in ubuntu I tried:

set path= /usr/lib/jvm/java-6-openjdk/bin
set classpath=./classes/;./lib/jdom.jar;%classpath%
java aminePlatform/guis/aminePlatformGUI/AminePlatformGUI

And it doesnt work, does anyone have any ideas?

---

### Post by konqueror7 on 2009-02-24
```
sudo gedit /etc/bash.bashrc
```
then add the following lines,
```
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.10/"
```
then,
```
export PATH="$PATH:$JAVA_HOME/bin/"
```
save it, and restart your pc/laptop... (just change **java-6-sun-1.6.0.10** with your version)

this is assuming you already installed java...

[here's]("https://help.ubuntu.com/community/Java") a guide regarding java in ubuntu...

---

### Post by tarps87 on 2009-02-24
You shouldn't need to set the path to Java unless you want to set a different version

To find out the version you are running
```
java -version
```

To find out where the java version is stored
```
which java
```

To run the program
```
java -cp ./classes/;./lib/jdom.jar aminePlatform/guis/aminePlatformGUI/AminePlatformGUI
```
or as konqueror7 suggested
```
export PATH="$PATH:$JAVA_HOME/bin/"
java aminePlatform/guis/aminePlatformGUI/AminePlatformGUI
```

---

