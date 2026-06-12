---
title: "Cannot start eclipse"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-17
Hi,

     I cannot start the eclipse and I have attached the log when i try to run in thru terminal. I cannot find any log in the mentioned path of the eclipse after it ives the error. Pls help

home@home-desktop:~$ cd /usr/lib/eclipse
home@home-desktop:/usr/lib/eclipse$ ./eclipse -debug
Start VM: /usr/bin/java
-Xms40m
-Xmx256m
-jar /usr/lib/eclipse/./startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/./eclipse
-name Eclipse
-showsplash 600
-exitdata 66000c
-debug
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /usr/lib/eclipse/./startup.jar 
Install location:
    file:/usr/lib/eclipse/
Configuration file:
    file:/usr/lib/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/home/.eclipse/org.eclipse.platform_3.2.0/configuration/
Configuration file:
    file:/home/home/.eclipse/org.eclipse.platform_3.2.0/configuration/config.ini not found or not read
Shared configuration location:
    file:/usr/lib/eclipse/configuration/
Framework located:
    file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.2.2.R32x_v20070118.jar
Framework classpath:
    file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.2.2.R32x_v20070118.jar
Splash location:
    /usr/lib/eclipse/plugins/org.eclipse.platform_3.2.2.r322_v20070117b/splash.bmp
runCommand:
    </usr/lib/eclipse/./eclipse><-name><Eclipse><-showsplash><600></usr/lib/eclipse/plugins/org.eclipse.platform_3.2.2.r322_v20070117b/splash.bmp>
Debug options:
    file:/usr/lib/eclipse/.options not found
Time to load bundles: 9
Starting application: 1074
runCommand:
    </usr/lib/eclipse/./eclipse><-name><Eclipse><-exitdata><66000c><An error has occurred. See the log file
/media/Home/EclipseProject/.metadata/.log.>

---

### Post by logic++ on 2009-01-17
Did you install it from the repositories?

Try running the application while you are in you home directory:
```
your-username@machine-name:/usr/bin/eclipse
```

---

### Post by Jeyaganeshdj on 2009-01-17
yeah, i installed from the repositeries

---

