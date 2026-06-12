---
title: "I still cannot mount my walkman mp3"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by smj0804 on 2008-12-28
ahhhhD:
why cant i mount my mp3 usb?
it's sony walkman mp3

how can i solve the problem..T^T
and can you explain it VERY CELARLY...? because..
im a beginner..and im new..to the things..D:

HELLPPP

---

### Post by Michael.Godawski on 2008-12-29
hey and morning,

download this application [JSymphonic_0.3.0alpha1.zip]("http://downloads.sourceforge.net/symphonic/JSymphonic_0.3.0alpha1.zip?modtime=1230196062&big_mirror=0") found here:

[http://sourceforge.net/project/showfiles.php?group_id=190494](http://sourceforge.net/project/showfiles.php?group_id=190494)

Extract it to your Desktop so you have this package on it:
JSymphonic_0.3.0a1.jar

Now open the terminal (plug in your walkman first) navigate to the Desktop and launch the app:

```
cd Desktop
java -jar JSymphonic_0.3.0a1.jar 
```

You will have to install Java for this app to run:
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

