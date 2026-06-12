---
title: "Java Runtime installing"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by alket on 2009-03-11
Im trying to install java in ubuntu but i cannt
i downloaded 2 files from java.com

```
Linux RPM (self-extracting file)
Linux (self-extracting file)  
```

but i cant install them.

How can I install them or is there any other way to install Java Runtime in my Ubuntu ?

---

### Post by taurus on 2009-03-11
Unless you have a reason why, install the one from the repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by alket on 2009-03-11
> **taurus said:**
> Unless you have reason why, install the one from the repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

I arleady tried that
```
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.

```

It says that i have java installed, but firefox doesnt recognise it and when i want to download something in sun.com it says that i dont have Java Runtime.

---

### Post by taurus on 2009-03-11
Can you post the output of this command from a terminal?

```
java -version
```
I assume you have restarted firefox.  Sometimes, rebooting your machine works wonder too.

---

### Post by alket on 2009-03-11
```
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)

```

---

### Post by alket on 2009-03-11
*nudge !!!*

---

### Post by binbash on 2009-03-11
sudo update-java-alternatives -s java-6-sun

---

### Post by jespdj on 2009-03-11
Just 7 minutes ago and you're already "nudging" your topic?! Be patient!

If you have the package **sun-java6-plugin** installed, then Java should work normally in Firefox. Maybe for some reason the package is not installed correctly. Try removing and re-installing it:
```
sudo apt-get purge sun-java6-plugin
sudo apt-get install sun-java6-plugin
```
Watch if this goes without errors.

How are you testing to see if Java is working or not, and how do you know it is not working?

---

### Post by alket on 2009-03-11
jespdj,
sorry about that, but i was very angry because im been trying to install Java Runtime for 2days

Your method works, thanks a lot.

---

