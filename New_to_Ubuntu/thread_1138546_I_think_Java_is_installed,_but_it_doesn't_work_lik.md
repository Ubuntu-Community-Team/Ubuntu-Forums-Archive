---
title: "I think Java is installed, but it doesn't work like it used to"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by diablo75 on 2009-04-26
I have the sun-java6-jre (version 6-13-1) installed in synaptic, but when I visit a website like this:

[http://radar.weather.gov/radar.php?rid=TWX&product=NCR&overlay=11101111&loop=yes](http://radar.weather.gov/radar.php?rid=TWX&product=NCR&overlay=11101111&loop=yes)

It says:  Java is necessary for radar looping and is best optimized using Java version 1.4.2 or higher.
Go to [www.java.com/en](www.java.com/en) for more information regarding Java.

Any ideas?

---

### Post by gandaran on 2009-04-26
> **diablo75 said:**
> I have the sun-java6-jre (version 6-13-1) installed in synaptic, but when I visit a website like this:

[http://radar.weather.gov/radar.php?rid=TWX&product=NCR&overlay=11101111&loop=yes](http://radar.weather.gov/radar.php?rid=TWX&product=NCR&overlay=11101111&loop=yes)

It says:  Java is necessary for radar looping and is best optimized using Java version 1.4.2 or higher.
Go to [www.java.com/en](www.java.com/en) for more information regarding Java.

Any ideas?
did you install the sun-java6-plugin for firefox?

---

### Post by Michael.Godawski on 2009-04-26
Basically you need to install these three packages to use Java applets on the Internet:
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by diablo75 on 2009-04-26
> **gandaran said:**
> did you install the sun-java6-plugin for firefox?

This did the trick.  Thanks!

---

