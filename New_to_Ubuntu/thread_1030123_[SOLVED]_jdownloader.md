---
title: "[SOLVED] jdownloader"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by phanipalagummi on 2009-01-04
I downloded jdownloader_v0.3668.zip,then i extracted and foundjDownloader.jar which can be extracted but i run in java-6 run time 
which was said to do so in youtube.com nothing appears ,then i tried google
every thing was greek and latin to me,please help me in installing jdownloader:confused:

Please dont say to use firfox addons(down themall etc,.)

---

### Post by adobrakic on 2009-01-04
Install Java:

```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

Then go into the JDownloader folder, and go find the file that says JDownlaoder.jar (make sure not to mistake the Jdownloader.exe for this), right click that and go to Open With -> and open it with java

---

### Post by PeeZz on 2009-01-04
You don't have to extract the .jar. Try to right-click it and select "Open with Sun Java 6 Runtime" or something similar.

---

### Post by phanipalagummi on 2009-01-04
yes i got installing it by giving permission for executing it

```
sudo chmod +x JDownloader.jar
```

but tell me does i need  to run jdownloader.jar every time i need it.
sinse i cant see it in applications

---

### Post by PeeZz on 2009-01-04
> **phanipalagummi said:**
> yes i got installing it by giving permission for executing it

```
sudo chmod +x JDownloader.jar
```

but tell me does i need  to run jdownloader.jar every time i need it.
sinse i cant see it in applications

Actually you don't have to install anything.
jdownloader.jar _is_ the program. So when you select "Open with Java 6 runtime", the JRE (Java Runtime Environment) loads and runs the program.

So, yes, you have to open jdownloader.jar every time you want to use it.

I don't think you need to do chmod +x on the .jar (at least I don't ;) )

---

### Post by magnus0 on 2009-01-04
I think you can use:

```
java -jar JDownloader.jar
```

---

